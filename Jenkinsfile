@Library('Shared')_
pipeline{
    agent any
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
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
                docker_build("notes-app", "latest", "myserverd")  
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                docker_push("notes-app","latest", "myserverd")    
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker-compose down && docker-compose up -d"
            }
        }        
    }
}
