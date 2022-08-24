pipeline {
    agent any
    parameters{
        string(name:'ENV',defaultvalue:'Test',description:'version to deploy')
        booleanParam(name:'ExecuteTests',defaultvalue:true,description:'decide to run tc')
        choice(name:'APPVERSION',choices:['1.1','1.2','1.3'])
    }

   

    stages {
        stage('Build') {
            steps {
                script{
                    echo "Building the code"
                }
            }

            
        }
         stage('Test') {
            when{
                expression{
                    params.ExecuteTests==true
                }
            }
            steps {
                script{
                    echo "compiling the code"
                }
            }

            
        }
         stage('Deploy') {
            steps {
                script{
                    echo "deploying the app "
                    echo "deploying to env: ${params.ENV}"
                    
                }
            }

            
        }
    }
}
