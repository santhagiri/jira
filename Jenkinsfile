pipeline {
  agent any
  stages {
    stage('DEPLOY DEV') {
      steps {
        echo 'deploy'
      }
    }
  }
  environment {
    PROJECT = 'cx'
    APPLICATION = 'ess'
    SERVICE_TYPE = 'nodejs'
    PATH = '/sbin:/usr/sbin:/bin:/usr/bin:/opt/jenkins_home/tools/hudson.plugins.sonar.SonarRunnerInstallation/SonarQube_Scanner/bin'
    SERVICE = 'dd-cx-enrollee-portal'
    EXECUTION = 'jenkins'
    APP_ENDPOINT = 'enrollee-services'
  }
}