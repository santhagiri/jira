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
    stage('PUBLISH REPORTS') {
      parallel {
        stage('Checkstyle Report') {
          steps {
            timestamps() {
              checkstyle(pattern: '**/test-results/jshint-checkstyle.xml')
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
      }
    }
    stage('Deploy - DEV') {
      environment {
        DEPLOYMENT_ENVIRONMENT = 'dev'
        DOCKER_PORT = '3003'
        DOCKER_SERVER_1 = 'aw-lx0076'
        DOCKER_SERVER_2 = 'aw-lx0336'
      }
      steps {
        timestamps() {
          deleteDir()
          git(url: '${DOCKER_VARIABLES_DEV}', credentialsId: 'ca88899d-be3e-45db-a2a0-6fa79f678a56')
          sh '''
		'''
          deleteDir()
        }

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
