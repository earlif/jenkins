pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                echo "build stage"
                sh 'mvn --version'
            }
        }
    }
    stages {
        agent { label "jdk11"}
        stage('test') {
            steps {
                echo "test stage"
                sh 'java --version'
            }
        }
    }
    stages {
        agent { label "jdk8"}
        stage('deploy') {
            steps {
                echo "deploy stage"
                sh 'java --version'
            }
        }
    }
    post {
        always {
            mail to: 'peng_zhou@epam.com',
                 subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Something is wrong with ${env.BUILD_URL}"
        }
    }
}
