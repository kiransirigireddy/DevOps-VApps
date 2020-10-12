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
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

          }
        }

        stage('Code Coverage') {
          steps {
            sleep 3
            catchError(buildResult: 'SUCCESS', stageResult: 'UNSTABLE') {
              sh 'exit 1'
            }

          }
        }

        stage('Sonar Qube Analysis') {
          steps {
            sleep 2
            catchError(buildResult: 'SUCCESS', stageResult: 'UNSTABLE') {
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

    stage('Product Configuration') {
      parallel {
        stage('Update the Configurations') {
          steps {
            sleep 3
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

          }
        }

        stage('Sanity Test') {
          steps {
            sleep 3
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

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

        stage('Workflow Test/Point2Point') {
          steps {
            sleep 2
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

          }
        }

        stage('Installation Testing') {
          steps {
            sleep 3
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

          }
        }

      }
    }

    stage('Non Functional Test') {
      parallel {
        stage('Base Line Performance Test') {
          steps {
            sleep 3
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

          }
        }

        stage('Stress Test') {
          steps {
            sleep 3
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

          }
        }

        stage('Stability Test') {
          steps {
            sleep 3
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

          }
        }

        stage('Security Test') {
          steps {
            sleep 2
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('Publish Product') {
          steps {
            sleep 3
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

          }
        }

        stage('Deploy to Hosting') {
          steps {
            sleep 2
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

          }
        }

        stage('Upload To SharePoint') {
          steps {
            sleep 2
            catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
              sh 'exit 1'
            }

          }
        }

      }
    }

  }
}
