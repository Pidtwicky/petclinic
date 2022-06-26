pipeline {
    agent any

    stages {
        /*
        stage('Test Sonar') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "/opt/sonar-scanner/bin/sonar-scanner"
                }
            }
        }
        */ 
        /**/
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/Pidtwicky/petclinic.git'

                // Run Maven on a Unix agent.
                sh "mvn package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
            post {
            // If Maven was able to run the tests, even if some of the test
            // failed, record the test results and archive the jar file.
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.war'
                }
            }
        }
        /*
        stage('Code Quality'){
            
            steps{
            	withSonarQubeEnv('sq-server1'){
            		sh 'mvn sonar:sonar'	
            	}	
            }
        }
        */
        
        
       
    }
}