pipeline {
        agent any
 
        tools {
        maven 'Local_Maven'
        }
    stages {
        stage ('Build Servlet Project') {
            steps {
                /*For windows machine */
               //bat  'mvn clean package'

                /*For Mac & Linux machine */
                sh  'mvn clean package'
            }

            post{
                success{
                    echo 'Now Archiving ....'

                    archiveArtifacts artifacts : '**/*.war'
                }
            }
        }
        stage ('Deploy Build in Staging Area'){
            steps{

                build job : 'Deploy_stagging_pipeline'

            }
        }       
    }
}
