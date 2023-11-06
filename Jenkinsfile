node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email arshadkpathan1@gmail.com"
                        sh "git config user.name arshad"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+569823541824.dkr.ecr.ap-south-1.amazonaws.com/arshad786.*+569823541824.dkr.ecr.ap-south-1.amazonaws.com/project2:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}: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@github.com/${GIT_USERNAME}/kubernetesmanifest-1.git HEAD:main"
      }
    }
  }
}
}
