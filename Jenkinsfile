pipeline {
  agent any
  stages {
    stage('Environment') {
      parallel {
        stage('Build Server1') {
          steps {
            build(job: 'Download_VM_Template', quietPeriod: 2, wait: true)
          }
        }

        stage('Build IQuote Server') {
          steps {
            build(job: 'Download_VM_Template', quietPeriod: 3)
          }
        }

      }
    }

    stage('Build') {
      parallel {
        stage('RestartIQuoteServer') {
          steps {
            sleep 3
          }
        }

        stage('Restart AC4D Server') {
          steps {
            sleep 3
          }
        }

        stage('Restart PF Server') {
          steps {
            sleep 3
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('RDP AC4D Server') {
          steps {
            sleep 3
          }
        }

        stage('RDP -IQuote Server') {
          steps {
            sleep 3
          }
        }

        stage('RDP- PF Server') {
          steps {
            sleep 3
          }
        }

      }
    }

    stage('Product Integration') {
      parallel {
        stage('Configure_ AC4D_Server') {
          steps {
            sleep 3
          }
        }

        stage('Configure-Print Flow Server') {
          steps {
            sleep 3
          }
        }

        stage('Configure IQuote Eflow Server') {
          steps {
            sleep 3
          }
        }

      }
    }

    stage('Functional Test') {
      parallel {
        stage('Restart IQuote Server') {
          steps {
            sleep 3
          }
        }

        stage('Restart AC4D Server') {
          steps {
            sleep 3
          }
        }

        stage('Restart PF Server') {
          steps {
            sleep 3
          }
        }

      }
    }

    stage('Non Functional Test') {
      parallel {
        stage('RDP AC4D Server') {
          steps {
            sleep 3
          }
        }

        stage('RDP -IQuote Server') {
          steps {
            sleep 3
          }
        }

        stage('RDP- PF Server') {
          steps {
            sleep 3
          }
        }

      }
    }

    stage('Publish Product') {
      parallel {
        stage('Upgrade AC4D') {
          steps {
            sleep 3
          }
        }

        stage('Upgrade-IQuote') {
          steps {
            sleep 3
          }
        }

        stage('Upgrade Print Flow') {
          steps {
            sleep 3
          }
        }

      }
    }

  }
}