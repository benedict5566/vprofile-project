pipeline{
    agent any
    tools {
        jdk 'JDK'
        maven 'Maven'
    }
    stages {
        stage ('FETCH THE CODE FROM GITHUB') {
            steps{
                git branch: 'main', credentialsId: 'key-logs', url: 'https://github.com/benedict5566/vprofile-project.git'
            }
        }
        stage ('BUILD THE CODE') {
            steps{
                sh 'mvn clean install -DskipTest'
            }
            post {
                success {
                    echo 'Archiving artifacts now.'
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage ('UNIT TEST') {
            steps{
                sh 'mvn test'
            }
        }
    }
}