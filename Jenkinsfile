pipeline {
    agent any

environment{
 PATH="${PATH}:/opt/maven/bin"
}
    stages {
        stage('CLONE') {
            steps {
                git branch: 'main', credentialsId: 'Github-Login', url: 'https://github.com/kk1567811/vansro22.git'

            }
        }
     stage('BUILD') {
            steps {
                sh "mvn clean package"
            }
        }

stage('DEPLOY') {
            steps {
                sshagent(['tomcat-Login']) {

sh "scp -o StrictHostKeyChecking=no target/vansro-1.0-SNAPSHOT.jar  ec2-user@13.127.239.171:/opt/apache-tomcat-9.0.95/webapps"

                    

     }
   }
 }


        
     }
}

