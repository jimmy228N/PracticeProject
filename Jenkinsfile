pipeline{
  agent any
  parameters {
        booleanParam(name: 'refresh', defaultValue: false, description: 'Refresh pipeline stages')
  }
stages {
  stage('Refresh pipeline') {
    script{
      if (params.refresh) {
          currentBuild.result = 'ABORTED'
          error('Stopping early…')
      }
    }
  }
  stage('Cloning our Git') {
    steps {
      git branch: 'main', url: 'https://github.com/jimmy228N/PracticeProject.git'
    }
  }
  stage('User Validation'){
    steps{
      script{
        timeout(time: 1, unit:'HOURS')
        input message: 'Do you want to proceed?', ok: 'Continue'
      }
    }
  }
  stage('Building our image') {
    steps{
      sh 'docker build -t practice-app:$BUILD_NUMBER .'
      sh 'echo "DONE BUILDING DOCKER IMAGE"'
    }
  }
  stage('Running our image') {
    steps{
      sh 'docker run --name practice1 -p 3000:3000 -d practice-app:$BUILD_NUMBER'
      echo 'DOCKER CONTAINER RUNNING...'
    }
  }
}
}
