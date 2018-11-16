pipeline {
  agent any
  stages {
    stage('Code Compile') {
      steps {
        timestamps() {
          sh 'env | sort'
        }

      }
    }
    stage('CODE QUALITY') {
      parallel {
        stage('Code Coverage') {
          steps {
            timestamps() {
              sh '''
			  '''
            }

          }
        }
        stage('Code Security') {
          steps {
            timestamps() {
              sh '''
			  '''
            }

          }
        }
      }
    }
    stage('Archive Artifacts') {
      steps {
        timestamps() {
          sh '''
		  '''
          archiveArtifacts(artifacts: '*.zip', allowEmptyArchive: true)
        }

      }
    }
    stage('Docker Build') {
      steps {
        timestamps() {
          sh '''
		  '''
        }

      }
    }
    stage('JUnit Report') {
      steps {
        timestamps() {
          junit(testResults: '**/test-results/*.xml', allowEmptyResults: true, healthScaleFactor: 1)
        }

      }
    }
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