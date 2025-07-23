pipeline{
    agent any
       environment{
        VERSION = "${env.BUILD_ID}"
       }
    stages{
        stage("docker build and push"){
            steps{
                script{
                    withCredentials([string(credentialsId: 'docker-h', variable: 'doc-pass')]) {
                        sh '''
                         docker build -t khaira23/testapp:${VERSION} .
                         echo $doc-pass | docker login -u khaira23 --password-stdin  
                         docker push khaira23/testapp:${VERSION} 
                         docker rmi khaira23/testapp:${VERSION}            
                        '''
                    }
                 }
              } 
           }
        }  
    } 
