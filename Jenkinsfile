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
                sh """ sudo cp -r /var/lib/jenkins/workspace/build/target/java-tomcat-maven-example.war /opt/tomcat/webapps
                 sudo /opt/tomcat/bin/startup.sh
                """
            }
        }
    }
}
