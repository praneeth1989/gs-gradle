node {
  def myGradleContainer = docker.image('gradle:jdk8')
  myGradleContainer.pull()
  stage('prep') {
    checkout scm
  }
  stage('test') {
     myGradleContainer.inside('-u root')("-v ${env.HOME}/.gradle:/home/gradle/.gradle") {
      sudo sh 'cd complete && ./gradlew test'
     }
  }
  stage('run') {
     myGradleContainer.inside('-u root')("-v ${env.HOME}/.gradle:/home/gradle/.gradle") {
      sudo sh 'cd complete && ./gradlew run'
     }
  }
}
