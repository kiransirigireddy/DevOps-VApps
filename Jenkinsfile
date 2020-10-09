pipeline {
  agent any
  stages {
    stage('Test Bed') {
      parallel {
        stage('Download VM Template') {
          steps {
            build(job: 'Download_VM_Template', quietPeriod: 2, wait: true)
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

          }
        }

        stage('Spin a VM from Template') {
          steps {
            build(job: 'Download_VM_Template', quietPeriod: 3)
            catchError(buildResult: 'SUCCESS', stageResult: 'UNSTABLE') {
              sh 'exit 1'
            }

          }
        }

      }
    }

    stage('Trigger Build') {
      parallel {
        stage('Unit Test') {
          steps {
            sleep 3
            catchError(buildResult: 'SUCCESS', stageResult: 'UNSTABLE') {
              sh 'exit 1'
            }

          }
        }

        stage('Code Coverage') {
          steps {
            sleep 3
            catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
              sh 'exit 1'
            }

          }
        }

        stage('Sonar Cube Analysis') {
          steps {
            sleep 2
            catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
              sh 'exit 1'
            }

          }
        }

      }
    }

    stage('Upgrade Test Bed') {
      parallel {
        stage('Prepare for Installation') {
          steps {
            sleep 3
          }
        }

        stage('Upgrade Server') {
          steps {
            sleep 3
          }
        }

      }
    }

    stage('Product Integration') {
      parallel {
        stage('Update the Configurations') {
          steps {
            sleep 3
          }
        }

        stage('Smoke Test') {
          steps {
            sleep 3
          }
        }

      }
    }

    stage('Functional Test') {
      parallel {
        stage('Smoke Test') {
          steps {
            sleep 3
          }
        }

        stage('Regression Test') {
          steps {
            sleep 3
          }
        }

        stage('Workflow Test') {
          steps {
            sleep 2
          }
        }

      }
    }

    stage('Non Functional Test') {
      parallel {
        stage('Base Line Performance Test') {
          steps {
            sleep 3
          }
        }

        stage('Stress Test') {
          steps {
            sleep 3
          }
        }

        stage('Stability Test') {
          steps {
            sleep 3
          }
        }

        stage('Security Test') {
          steps {
            sleep 2
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('Publish Product') {
          steps {
            sleep 3
          }
        }

        stage('Deploy to Hosting') {
          steps {
            sleep 2
          }
        }

        stage('Upload To FTP') {
          steps {
            sleep 2
          }
        }

      }
    }

  }
}