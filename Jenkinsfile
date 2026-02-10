@Library("Shared") _
pipeline{
    agent {label "safi"}
    stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code"){
            steps{
            script{
             clone("https://github.com/SAFI-ULLAHSAFEER/django-notes-app.git","main")
            }
        }
        }
        stage("build"){
        steps{
            script{
                docker_build("notes-app","latest","safi221")
            }
        }
    }
    stage("Push To DockerHub"){
            steps{
               script{
                   docker_push("notes-app","latest","safi221")
                }
            }
        }
    stage("Deploy"){
    steps{
          sh 'docker compose down && docker compose up -d'
          echo "Application deployed successfully"
       }
}
}
}
