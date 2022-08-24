pipeline {
    agent none
    tools{
        jdk 'myjava'
        maven 'Mymaven'
       
    }
   

    stages {
        stage('COMPILE') {
            agent any
            steps {
                script{
                    echo "COMPILING THE CODE"
                    git 'https://github.com/pentelah1/addressbook.git'
                    sh 'mvn compile'
                   
                }
            }

            
        }
        stage('UNITTEST') {
            agent {label 'linux_slave1'}
           
            steps {
                script{
                    echo "RUNNING THE UNIT TEST CASES"
                    sh 'mvn test'
                }


            }
            post{
                always{
                    junit 'target/surefire-reports/*.xml'
                }
            }
         }
        stage('package'){
            agent any
            
             steps{
               script{
                sshagent(['Test-server-key']) {
                  echo "PACKAGING THE CODE"
                  sh "scp -o strictHostKeyChecking=no server-script.sh ec2-user@172.31.29.27:/home/ec2-user"
                  sh "ssh -o strictHostKeyChecking=no ec2-user@172.31.29.27 'bash ~/server-script.sh'"
                  
    
                }
               
              
               }
             }
        }  
        
        
    }
}
