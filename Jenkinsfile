@Library('Shared')_
pipeline{
    agent any
    
    stages{
        stage("Hello"){
            steps{
                script{
                    Hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                clone("https://github.com/LohadeDarshan/django-notes-app.git","main")    
                }
            }
        }
        stage("Build"){
            steps{
                script{
                dockerbuild("notes-app","latest", "myserverd")    
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                dockerpush("dockerHubCreds","notes-app","latest")    
                }
            }
        }
        stage("Deploy"){
            steps{
                script{
                echo "This is deploying the code"
                sh "docker-compose down && docker-compose up -d"
                }
            }
        }        
    }
}
