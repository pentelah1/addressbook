pipeline {
    agent any
    tools{
        jdk 'myjava'
        maven 'Mymaven'
       
    }
   

    stages {
        stage('COMPILE') {
            steps {
                script{
                    echo "COMPILING THE CODE"
                    git 'https://github.com/pentelah1/addressbook.git'
                    sh 'mvn compile'
                   
                }
            }

            
        }
        stage('UNITTEST') {
           
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
            
             steps{
               script{
                echo "PACKAGING THE CODE"
                sh 'mvn package'
              
               }
             }
        }  
        
        
    }
}
