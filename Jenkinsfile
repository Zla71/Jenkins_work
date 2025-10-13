def getNextDayOfWeek(String day) {
    def today = new Date()
    def dayOfWeek = ['sunday': Calendar.SUNDAY, 'monday': Calendar.MONDAY, 'tuesday': Calendar.TUESDAY, 'wednesday': Calendar.WEDNESDAY, 'thursday': Calendar.THURSDAY,
    'friday':Calendar.FRIDAY, 'saturday':Calendar.SATURDAY][day. toLowerCase()]

    def cal = Calendar.getInstance()
    cal.setTime(today)
    def daysToAdd = (dayOfWeek - cal.get(Calendar.DAY_OF_WEEK) + 7 ) % 7
    daysToAdd = daysToAdd == 0 ? 7 : daysToAdd
    cal.add(Calendar.DATE, daysToAdd)
    return cal.getTime().format('yyyy-MM-dd')
}

properties([
    parameters([
        booleanParam(name: 'CHECK_DATE_OF_NEXT_SATURDAY', defaultValue: true, description: "Check the box if you want to see the date of next Saturday.")
    ])
])


pipeline {
    agent any

    
    stages {
        if (params.CHECK_DATE_OF_NEXT_SATURDAY) {
            stage('Get date of next Saturday') {
                steps {
                    script {               
                        def today = java.time.LocalDate.now()
                        def nextSaturday = getNextDayOfWeek('saturday')
                        echo "Next Saturday's date is: ${nextSaturday}"
                    }
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
