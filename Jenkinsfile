pipeline {

  environment {
  agent any
    //adding a comment for the commit test
    DEPLOY_CREDS = credentials('deploy-anypoint-frussog')
    MULE_VERSION = '4.3.0'
    BG = "Test"
    WORKER = "Micro"
  }
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }



     stage('Deploy Development') {
      environment {
        ENVIRONMENT = 'Sandbox'
        APP_NAME = 'inventory-service-api'
      }
      steps {
      
			bat 'mvn -U -V -e -B -DskipTests deploy -DmuleDeploy --Dapp.runtime=4.3 -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dtarget=retail-revamp-server -Dtarget.type=server  -Denvironment=Sandbox'            
      }
    }
  }

  tools {
    maven 'M3'
  }
}