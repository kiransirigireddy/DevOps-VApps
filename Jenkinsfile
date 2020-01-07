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
        stage('Configure-IQuote-Eflow-Server') {
          steps {
            build(job: 'Configure-IQuote-Eflow-Server', quietPeriod: 1)
          }
        }

        stage('RDP AC4D Server') {
          steps {
            build(job: 'RDP-AC4DServer', quietPeriod: 3)
          }
        }

      }
    }

    stage('Integration 2') {
      parallel {
        stage('Configure-PrintFlowServer') {
          steps {
            build(job: 'Configure-PrintFlowServer', quietPeriod: 3)
          }
        }

        stage('RDP IQuote Server') {
          steps {
            build(job: 'RDP-IQuoteServer', quietPeriod: 3)
          }
        }

      }
    }

    stage('Integration 3') {
      parallel {
        stage('Configure_AC4D_Server') {
          steps {
            build(job: 'Configure_AC4D_Server', quietPeriod: 3)
          }
        }

        stage('RDP Printflow Server') {
          steps {
            build(job: 'RDP-PFServer', quietPeriod: 3)
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

  }
}