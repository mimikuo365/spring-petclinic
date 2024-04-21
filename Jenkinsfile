pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    stages {
        stage ('Check setup') {
            steps {
                echo 'Checking setup...'
                sh 'which ansible'
                sh 'ansible --version'
                sh 'java -version'
                sh 'mvn -version'
            }
        }

        stage('Static Analysis') {
            steps {
                withSonarQubeEnv(installationName: 'sonarqube-server', credentialsId: 'sonarqube-token') {
                    echo 'Static analysis..'
                    sh './mvnw clean verify sonar:sonar'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    ansiblePlaybook(credentialsId: 'ansible-ssh-1', disableHostKeyChecking: true, installation: 'ansible', inventory: 'ansible/hosts.ini', playbook: 'ansible/petclinic.yml')
                }
            }
        }
    }
}
