pipeline{
  agent any
  stages{
    stage('Create PagerDuty Maintenance Window'){
      environment{
        PAGERDUTY_API_KEY = credentials("PAGERDUTY_API_KEY")
      }

      steps{
        script{
            svn.getAnsible()
            ok = createPagerDutyMaintenanceWindow(
                token: '$PAGERDUTY_API_KEY',
                env: 'dev',
                desc: "Test Description right here"
          )
          if(!ok){
            error("Failed to create PagerDuty maintenance window")
          }
        }
      }
    }
  }
}
