node {
  checkout scm
  env.PATH = "${tool 'Maven3'}/bin:${env.PATH}"
  stage('Compile') {
    dir('webapp') {
      sh 'mvn clean package'
      junit '**/target/surefire-reports/*.xml'
    }
  }

  stage('Create Docker Image') {
    dir('webapp') {
        //docker.withRegistry("https://arun-gupta-docker-docker_jenkins_pipeline.bintray.io", "bintray") {
          //def app = docker.build("arun-gupta-docker-docker_jenkins_pipeline.bintray.io/workshop/docker_jenkins_pipeline:${env.BUILD_NUMBER}")
          //def app = docker.build("docker_jenkins_pipeline:${env.BUILD_NUMBER}")
        //}
      docker.build("arungupta/docker-jenkins-pipeline:${env.BUILD_NUMBER}").push()
    }
  }
}
