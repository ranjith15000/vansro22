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

     }
}

