pipeline {
    agent any
    tools{
        tool name: 'myjava', type: 'jdk'
        tool name: 'Mymaven', type: 'maven'
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
