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
        
        stage('Deploy'){
            steps{
                sh """ sudo cp /var/lib/jenkins/workspace/Ak-deploy/target/java-tomcat-maven-example.war /opt/tomcat/webapps
                sudo yum update
                """
            }
        }
    }
}
