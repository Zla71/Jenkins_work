pipeline {
    agent any  // Изпълнява на всеки наличен агент

    stages {
        stage('Checkout') {
            steps {
                // Изтегляне на кода от Git репозитория
                git 'https://github.com/Zla71/Jenkins_work.git'
            }
        }

        stage('Build') {
            steps {
                // Стъпка за билдване на проекта
                sh 'echo "Building project..."'
                sh './build.sh'  // ако имате скрипт за билд
            }
        }

        stage('Test') {
            steps {
                // Стъпка за тестове
                sh 'echo "Running tests..."'
                sh './test.sh'   // ако имате тестов скрипт
            }
        }
    }

    post {
        success {
            echo 'Build and tests succeeded!'
        }
        failure {
            echo 'Something went wrong.'
        }
    }
}
