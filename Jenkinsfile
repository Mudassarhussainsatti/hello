pipeline {
            agent any

            stages {
                stage('Build Docker Image') {
                    steps {
                        sh "docker build . -t mudassarhussain/k8test:v1"
                    }
                }
                stage('Docker Hub Push') {
                    steps {
                        withCredentials([usernamePassword(credentialsId: 'hub', passwordVariable: 'mudassarpass', usernameVariable: 'mudassarid')]) {
                         sh "docker login -u mudassarhussain -p ${mudassarpass}"
                         sh "docker push mudassarhussain/k8test:v1"

                        }
                    }
                }
                        
              stage ('ssh agent')  {  
                          
                          steps {
                          sshagent(['server3']) {
                            echo "Hello_world"
                          }
                          
              }
                          

         }
    }
}
