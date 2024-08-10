pipeline {
    agent any

environment{
PATH="${PATH}:/opt/maven/bin"
}

    stages {
        stage('CLONE') {
            steps {
                git branch: 'main', credentialsId: 'Github_Logins', url: 'https://github.com/kk1567811/vansro22.git'
            }
        }

stage('BUILD') {
            steps {
               sh "mvn clean package"
            }
        }
stage('UPLOADNEXSUS') {
            steps {
               nexusArtifactUploader artifacts: [[artifactId: 'vansro', classifier: '', file: 'target/vansro-1.0-SNAPSHOT.jar', type: 'jar']], credentialsId: 'Nexus-Logins2', groupId: 'com.vansro.payments', nexusUrl: '13.232.156.39:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'kkprojects', version: '1.0-SNAPSHOT'

            }
        }
    
stage('DEPLOY') {
            steps {
               sshagent(['Tomcat_Logins']) {
  sh "scp -o StrictHostKeyChecking=no target/vansro-1.0-SNAPSHOT.jar  ec2-user@13.232.222.147:/opt/tomcat9/webapps"

    }
  }
}



        
    }
}





