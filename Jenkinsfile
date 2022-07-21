pipeline { 
  agent any
  tools{
	nodejs 'Nodejs-18'
  }
  
  stages { 
    stage('clone repository') {
      steps { 
        git 'https://github.com/kkangwe/gallery.git'
      }
    }
     stage('Build the project') {
      steps { 
        sh 'echo "here we will Build"'
      }
    }
    stage('Install Dependencies') {
      steps { 
        sh 'npm install'
      }
    }
    stage('Tests') {
      steps { 
        sh 'echo "test"'
      }
    }
	stage('Deploy Application') {
      steps {
             withCredentials([usernameColonPassword(credentialsId: 'Saline', variable: 'HEROKU_CREDENTIALS' )]){
                    sh 'git push https://${HEROKU_CREDENTIALS}@git.heroku.com/saline-app.git master'
                    }
              }
    }
  }
}