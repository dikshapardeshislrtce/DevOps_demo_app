pipeline{
    agent any

    stages{
        stage {'Build'}{
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archinveArtifacts artifacts: '**/target/*.warf '
                }
            }
        }
        stage {'Deploy to tomcat server'} {
            steps{
                deploy adapters: [tomcat7(credentialsId: '00222d77-77f9-4c15-b6eb-7c4ff6b85f53', path: '', url: 'http://localhost:8085/')], contextPath: null, war: '**/*.war'
            }
        }

    }
}