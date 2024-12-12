github -- your repo -- Jenkinsfile -- edit

pipeline {
    agent {
        label 'linux'
    }
    
    tools {
        maven "MVN3"
    }
    
    stages {
        stage ('pull scm') {
            steps {
                git credentialsId: 'github', url: 'https://github.com/Niranjanharitwal/jenkins_test.git'
            }
        }
        
        stage('build') {
            steps {
                sh "mvn -f api-gateway/ clean package"
            }
        }
        
        stage('publish') {
            steps {
                archiveArtifacts artifacts: 'api-gateway/target/*.jar', followSymlinks: false
                junit stdioRetention: '', testResults: 'api-gateway/target/surefire-reports/*.xml'
            }
        }

        stage('print') {
            steps {
                sh "echo testing"
            }
        }
    }
}
