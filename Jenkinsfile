pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }

    environment {
        PATH = "/usr/bin/ansible-playbook:${env.PATH}" // Adjust the path according to where Ansible is installed
    }

    stages {
        // stage('Fetch') {
        //     steps {
        //         // Get some code from a GitHub repository
        //         git url: 'https://github.com/mimikuo365/spring-petclinic.git', branch: 'main'
        //     }
        // }
        stage ('Check setup') {
            steps {
                echo 'Checking setup...'
                sh 'java -version'
                sh 'mvn -version'
                sh 'which ansible'
                sh 'ansible --version'
            }
        }
        // stage('Build') {
        //     steps {
        //         // Run Maven on a Unix agent.
        //         sh "./mvnw package"
        //     }

        // }

        // stage('Static Analysis') {
        //     steps {
        //         withSonarQubeEnv(installationName: 'sonar-server', credentialsId: 'sonarqube-token') {
        //             echo 'Static analysis..'
        //             sh './mvnw clean verify sonar:sonar'
        //         }
        //     }
        // }

        // stage('Deploy to Production') {
        //     steps {
        //         script {
        //             ansiblePlaybook(credentialsId: 'ansible-ssh')
        //             // , inventory: 'ansible/hosts.ini', playbook: 'ansible/petclinic.yml')
        //         }
        //     }
        // }

        // stage('Deploy') {
        //     steps {
        //         echo 'Deploying....'
        //         sh 'java -Dserver.port=8000 -jar target/*.jar &'
        //     }
        // }
    }
}
