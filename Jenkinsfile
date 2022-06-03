pipeline{
    agent any
    stages{
        stage('SCM checkout'){
            steps{
                git 'https://github.com/Akshay369vm/java-tomcat-maven-example.git'
            }
        }
        
        stage('Build'){
            steps{
                sh'mvn package'
            }
        }
        
        stage('sonarQ analysis'){
            environment{
            SCANNER_HOME = tool 'SonarQube' 
            PROJECT_NAME = "java-maven"
            }
            steps {
                script {
                    withSonarQubeEnv('SonarQube') {
                        sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=$PROJECT_NAME \
                        -Dsonar.java.binaries=\"target/classes/\"'''
                    }
                }
                }
            }
            
        stage('Deploy'){
            steps{
                sh """ sudo cp -r /var/lib/jenkins/workspace/build/target/java-tomcat-maven-example.war /opt/tomcat/webapps
                 sudo /opt/tomcat/bin/startup.sh
                """
            }
        }
    }
}
