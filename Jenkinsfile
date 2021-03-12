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
                            sh 'echo "Hello_world" > /var/log/hello.txt'
                          }
                          
              }
                          

         }
		 
		 
		 stage ('ssh agent2')  {  
                          
                          steps {
                          sshagent(['server4']) {
                          sh 'echo "Hello_world" > /var/log/hello2.txt'
                          }
                          
              }
                          

         }
		 
		 
    }
}
