pipeline {
  agent any
  stages {
    stage('Environment') {
      parallel {
        stage('Build AC4D Server') {
          steps {
            build(job: 'VApps-AC4D', quietPeriod: 2, wait: true)
          }
        }

        stage('Build IQuote Server') {
          steps {
            build(job: 'VApps-IQuote', quietPeriod: 3)
          }
        }

        stage('Build Print Flow Server') {
          steps {
            build(job: 'VApps-PrintFlow', quietPeriod: 3)
          }
        }

      }
    }

    stage('Integration 1') {
      parallel {
        stage('RestartIQuoteServer') {
          steps {
            sleep 60
            build(job: 'RestartIQuoteServer', quietPeriod: 1)
          }
        }

        stage('Restart AC4D Server') {
          steps {
            sleep 120
            build(job: 'RestartAC4DServer', quietPeriod: 3)
          }
        }

        stage('Restart PF Server') {
          steps {
            sleep 220
            build(job: 'RestartPFServer', quietPeriod: 3)
          }
        }

      }
    }

    stage('Integration 2') {
      parallel {
        stage('RDP AC4D Server') {
          steps {
            sleep 220
            build(job: 'RDP-AC4DServer', quietPeriod: 3)
          }
        }

        stage('RDP -IQuote Server') {
          steps {
            sleep 400
            build(job: 'RDP-IQuoteServer', quietPeriod: 3)
          }
        }

        stage('RDP- PF Server') {
          steps {
            sleep 540
            build(job: 'RDP-PFServer', quietPeriod: 3)
          }
        }

      }
    }

    stage('Integration 3') {
      parallel {
        stage('Configure_ AC4D_Server') {
          steps {
            sleep 220
            build(job: 'Configure_AC4D_Server', quietPeriod: 3)
          }
        }

        stage('Configure-Print Flow Server') {
          steps {
            sleep 350
            build(job: 'Configure-PrintFlowServer', quietPeriod: 3)
          }
        }

        stage('Configure IQuote Eflow Server') {
          steps {
            sleep 120
            build(job: 'Configure-IQuote-Eflow-Server', quietPeriod: 3)
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        stage('Upgrade-AC4D') {
          steps {
            build(job: 'Upgrade-AC4D', quietPeriod: 3)
          }
        }

        stage('Upgrade-IQuote') {
          steps {
            build(job: 'Upgrade-IQuote', quietPeriod: 3)
          }
        }

        stage('Upgrade-PrintFlow') {
          steps {
            build(job: 'Upgrade-PrintFlow', quietPeriod: 3)
          }
        }

      }
    }

    stage('Test') {
      parallel {
        stage('Workflow Automation Test Execution') {
          steps {
            build(job: 'VApps_TestAutomation', quietPeriod: 2)
          }
        }

        stage('Performance test - Workflows') {
          steps {
            build(job: 'VApps_PerformanceTest', quietPeriod: 3)
          }
        }

      }
    }

  }
}