pipeline {
agent any
stages {
stage('Cloning our Git') {
steps {
git 'https://github.com/jimmy228N/PracticeApp.git'
}
}
stage('Building our image') {
steps{
  sh 'docker build -t practice-app:$BUILD_NUMBER .'
  echo 'DONE BUILDING DOCKER IMAGE'
}
}

stage('Running our image') {
steps{
  sh 'docker run --name practice1 -p 3000:3000 -d practice-app'
  echo 'DOCKER CONTAINER RUNNING...'
}
}

}
}