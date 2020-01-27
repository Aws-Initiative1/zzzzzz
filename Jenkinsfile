node {
    try {

    
            stage('Build and Quality Analysis'){
                    
                            stage('Build'){
                                echo 'Build'
                                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '345c79bc-9def-4981-94b5-d8190fdd2304', url: 'https://wwwin-github.cisco.com/Aws-Initiative1/zzzzzz.git']]])
                            }
                                       
            }

            
            stage('Publish'){
                def server = Artifactory.newServer url: 'https://artifactory.cdaf-cloud.com/artifactory', username:'as-deployer',password:'AKCp5e3yVDAi1k6xTqNzjHkbnuqHAhcVBTrqoVqk2NKjxKbxvb6Cv8ByQRsb8Sa5dEVtz7HgJ'
                
                    def uploadSpec = """{
        								"files": [
                									{
                    									"pattern": "*.tar",
                    									"target": "Mobility-Rakuten-Solution-group/Mobility-Rakuten-Solutions/Vendors/Cisco-group/CPNR/Early_Releases/1.0",
                    									"props": "p1=v1;p2=v2"
                									}
            									]
        			}"""
        			
        			def buildInfo1 = server.upload spec: uploadSpec
        			server.publishBuildInfo buildInfo1
            }
            
            

            
    } catch (err) {
        echo "${err}"
        println err
            
    }finally{
    }
}
