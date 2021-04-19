pipeline {
   agent any

   stages {
      stage('Verify Branch') {
         steps {
            echo "$GIT_BRANCH"
         }
      }
      stage('Start test app') {
         steps {
            sh '''docker run --name so1 --hostname so1 -p 8000:8000 \\
              -e "SPLUNK_PASSWORD=admin123" \\
              -e "SPLUNK_START_ARGS=--accept-license" \\
              splunk/splunk:latest'''
         }
         post {
            success {
               echo "App started successfully :)"
            }
            failure {
               echo "App failed to start :("
            }
         }
      }
   }
}
