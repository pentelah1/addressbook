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
                echo "PACKAGING THE CODE"
                sh 'mvn package'
              
               }
             }
        }  
        
        
    }
}
