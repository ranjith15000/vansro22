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
                sshagent(['Tomcat-Login']) {
sh "scp -o StrictHostCheckingKey=no
target/vansro-1.0-SNAPSHOT.jar ec2-user@15.206.72.185:/opt/tomcat9/webapps"

     }
   }
 }


        
     }
}

