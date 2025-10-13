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
        booleanParam(name: 'CHECK_DATE_OF_NEXT_SATURDAY', defaultValue: true, description: "Check the box if you want to see the date of next Saturday."),
        booleanParam(name: 'TESTING', defaultValue: true, description: "Check the box if you want to start Testing stage"),
        booleanParam(name: 'DEPLOY', defaultValue: true, description: "Check the box if you want to start deploying stage.")
    ])
])


pipeline {
    agent any

    
    stages {
        stage('Get date of next Saturday') {
            steps {
                script {
                    if (params.CHECK_DATE_OF_NEXT_SATURDAY) {
                        def today = java.time.LocalDate.now()
                        def nextSaturday = getNextDayOfWeek('saturday')
                        echo "Next Saturday's date is: ${nextSaturday}"
                    } else {
                        echo 'Skipping build as not selected'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    if (params.CHECK_DATE_OF_NEXT_SATURDAY) {
                        echo 'Testing..'
                    } else {
                        echo 'Skipping build as not selected'
                    }
                    
                }
                
            }
        }
        stage('Deploy') {
            steps {
                script {
                    if (params.CHECK_DATE_OF_NEXT_SATURDAY) {
                        echo 'Deploying..'
                    } else {
                        echo 'Skipping build as not selected'
                    }
                }
            }
        }
    }
}
