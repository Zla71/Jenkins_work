def getNextDayOfWeek(String day) {
    def today = new Date()
    def dayOfWeek = ['sunday': Calendar.SUNDAY, 'monday': Calendar.MONDAY, 'tuesday': Calendar.TUESDAY, 'wednesday': Calendar.WEDNESDAY, 'thursday': Calendar.thursday
    'friday':Calendar.FRIDAY, 'saturday':Calendar.SATURDAY][day. toLowerCase()]

    def cal = Calendar.getInstance()
    cal.setTime(today)
    def daysToAdd = (dayOfWeek - cal.get(Calendar.DAY_OF_WEEK) + 7 ) % 7
    daysToAdd = daysToAdd == 0 ? 7 : daysToAdd
    cal.add(Calendar.DATE, daysToAdd)
    return cal.getTime().format('yyyy-MM-dd')
}


pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    
                    def today = java.time.LocalDate.now()
                    // def nextSaturday = today.with(java.time.temporal.TemporalAdjusters.next(java.time.DayOfWeek.SATURDAY))
                    def nextSaturday = getNextDayOfWeek('saturday')
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
