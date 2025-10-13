def returnGivenDayDate(String day) {
    if (day.contains("[")) {
        day = replace("[", "").replace("]", "").replace("\"", "") 
    }
    def day = java.time.LocalDate.now()
    def dayOfWeek = java.time.DayOfWeek.valueOf(day.toUpperCase())
    return today.with(java.time.temporal.TemporalAdjusters.next(dayOfWeek))
}


pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    
                    def today = java.time.LocalDate.now()
                    def nextSaturday = today.with(java.time.temporal.TemporalAdjusters.next(java.time.DayOfWeek.SATURDAY))
                    echo "Next Saturday's date is: ${nextSaturday}"
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
