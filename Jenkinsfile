node {
  def myGradleContainer = docker.image('gradle:jdk8')
  myGradleContainer.pull()
  stage('prep') {
    checkout scm
  }
  stage('test') {
     myGradleContainer.inside("-v /var/jenkins_home/.gradle:/home/gradle/.gradle") {
       sudo sh 'cd /var/jenkins_home/workspace/GITHUB_REPO_gs-gradle_master'
      sudo sh 'cd complete && ./gradlew test'
     }
  }
  stage('run') {
     myGradleContainer.inside("-v ${env.HOME}/.gradle:/home/gradle/.gradle") {
      sudo sh 'cd complete && ./gradlew run'
     }
  }
}
