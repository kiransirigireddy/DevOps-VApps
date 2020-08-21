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
            build(job: 'Build Server2', quietPeriod: 3)
          }
        }

      }
    }

    stage('Build') {
      parallel {
        stage('RestartIQuoteServer') {
          steps {
            sleep 60
            build(job: 'RestartServer1', quietPeriod: 1)
          }
        }

        stage('Restart AC4D Server') {
          steps {
            sleep 120
            build(job: 'RestartServer2', quietPeriod: 3)
          }
        }

        stage('Restart PF Server') {
          steps {
            sleep 220
            build(job: 'RestartServer3', quietPeriod: 3)
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('RDP AC4D Server') {
          steps {
            sleep 220
            build(job: 'RDPServer', quietPeriod: 3)
          }
        }

        stage('RDP -IQuote Server') {
          steps {
            sleep 400
            build(job: 'RDPServer2', quietPeriod: 3)
          }
        }

        stage('RDP- PF Server') {
          steps {
            sleep 540
            build(job: 'RDP-Server4', quietPeriod: 3)
          }
        }

      }
    }

    stage('Product Integration') {
      parallel {
        stage('Configure_ AC4D_Server') {
          steps {
            sleep 220
            build(job: 'Configure_Server', quietPeriod: 3)
          }
        }

        stage('Configure-Print Flow Server') {
          steps {
            sleep 350
            build(job: 'Configure-Server2', quietPeriod: 3)
          }
        }

        stage('Configure IQuote Eflow Server') {
          steps {
            sleep 120
            build(job: 'Configure-Eflow-Server', quietPeriod: 3)
          }
        }

      }
    }

    stage('Functional Test') {
      parallel {
        stage('Restart IQuote Server') {
          steps {
            sleep 60
            build(job: 'RestartServer', quietPeriod: 3)
          }
        }

        stage('Restart AC4D Server') {
          steps {
            sleep 80
            build(job: 'RestartServer', quietPeriod: 3)
          }
        }

        stage('Restart PF Server') {
          steps {
            sleep 40
            build(job: 'RestartServer', quietPeriod: 3)
          }
        }

      }
    }

    stage('Non Functional Test') {
      parallel {
        stage('RDP AC4D Server') {
          steps {
            sleep 120
            build(job: 'RDP-Server', quietPeriod: 3)
          }
        }

        stage('RDP -IQuote Server') {
          steps {
            sleep 400
            build(job: 'RDPServer2', quietPeriod: 3)
          }
        }

        stage('RDP- PF Server') {
          steps {
            sleep 540
            build(job: 'RDP-Server3', quietPeriod: 4)
          }
        }

      }
    }

    stage('Publish Product') {
      parallel {
        stage('Upgrade AC4D') {
          steps {
            sleep 500
            build(job: 'Upgrade-4D', quietPeriod: 3)
          }
        }

        stage('Upgrade-IQuote') {
          steps {
            sleep 500
            build(job: 'UpgradeServer', quietPeriod: 3)
          }
        }

        stage('Upgrade Print Flow') {
          steps {
            sleep 540
            build(job: 'Upgrade-Server3', quietPeriod: 3)
          }
        }

      }
    }

  }
}