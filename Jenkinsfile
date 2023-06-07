pipeline {
    agent {
        node {
            label 'nodejs'
        }
		}
    parameters {
        booleanParam(name: "RUN_INTEGRATION_TESTS", defaultValue: true)
    }
    stages {
        stage('Test') {
            steps {
                stage('Unit tests') {
                    steps {
                        sh './mvnw test -D testGroups=unit'
                    }
                }
                stage('Integration tests') {
					when { expression { params.RUN_INTEGRATION_TESTS } }
                    steps {
                        sh './mvnw test -D testGroups=integration'
                    }
                }		
            }
        }
    }
}