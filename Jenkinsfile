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
            }
        }

        stage('Test') {
            steps {
                // Стъпка за тестове
                sh 'echo "Running tests..."'
            }
        }
    }
}
