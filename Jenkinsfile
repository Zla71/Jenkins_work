pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    
                    def today = java.time.LocalDate.now()
                    // def nextSaturday = today.with(java.time.temporal.TemporalAdjusters.next(java.time.DayOfWeek.SATURDAY))
                    echo "Next Saturday's date is: ${today}"
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
