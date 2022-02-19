pipeline{
    agent any
    stages{
        stage  ('SCM for Java Code'){
            steps{
                git changelog: false,url:  'https://github.com/pavansw/simpleMavenJunit.git'
               echo 'polling to developers SCM'

            }   
        }    // end of SCM stage 

        stage  ('Maven Compile'){
            steps{
                sh '''mvn clean 
                    mvn compile'''
            }
            
        }    // end of Maven stage

        stage  ('Testing code'){
            steps{
                sh '''mvn test'''
               echo 'Testing complete with Junit on maven'
            }
        }    // end of Testing code

        stage  ('Package')  {
            
            steps {
                sh 'mvn package'
            }
            
        }   // end of package

        stage  ('Publish Test result'){
            steps{
                junit 'target/surefire-reports/*.xml'
            }
        }   // end of publish

        stage  ('Execute Jar'){
            steps{
             sh 'java -jar target/*.jar'
            }
            
        } //end of execute
        
    }   // First stage

} // End of pipeline
