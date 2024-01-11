// pipeline {
//     agent any
//     stages {
//         stage('Build') {
//             steps {
//                 echo 'Running build automation'
//                 sh './gradlew build --no-daemon'
//                 archiveArtifacts artifacts: 'dist/trainSchedule.zip'
//             }
//         }
//     }
// }


pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Clean and build using Gradle
                    sh './gradlew clean build'
                }
            }
        }

        stage('Archive Artifact') {
            steps {
                script {
                    // Archive the dist/trainSchedule.zip artifact
                    archiveArtifacts artifacts: 'build/distributions/trainSchedule.zip', allowEmptyArchive: true
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! Do further deployment or notification here.'
        }
    }
}
