node {
  def myGradleContainer = docker.image('gradle:4.2.1-jdk8-alpine')
  myGradleContainer.pull()
  stage('prep') {
    checkout scm
  }
  stage('test') {
     myGradleContainer.inside("-v ${env.HOME}/.gradle:/home/gradle/.gradle") {
      sudo sh 'cd complete && ./gradlew test'
     }
  }
  stage('run') {
     myGradleContainer.inside("-v ${env.HOME}/.gradle:/home/gradle/.gradle") {
      sudo sh 'cd complete && ./gradlew run'
     }
  }
}
