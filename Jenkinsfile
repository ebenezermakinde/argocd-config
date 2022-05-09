node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh "git config user.email ebenezermakinde@gmail.com"
                        sh "git config user.name ebenezermakinde"
                        sh "cat ./dev/nodeapp/nodeapp-deployment.yaml"
                        sh "sed -i 's+ebenezermakinde/node-express-app.*+ebenezermakinde/node-express-app:${DOCKERTAG}+g' ./dev/nodeapp/nodeapp-deployment.yaml"
                        sh "cat ./dev/nodeapp/nodeapp-deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/argocd-config.git HEAD:main"
      }
    }
  }
}
}