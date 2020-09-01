pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    triggers {
  pollSCM '* * * * *'
}

    stages {
        
       stage('build') {
            steps {
                echo 'Hello build'
                sh 'mvn clean'
                sh  'mvn install'
                sh 'mvn package'
            }
        }
        stage('test') {
            steps {
                sh 'mvn test'
                
            }
        }
        stage ('build and publish image') {
      steps {
        script {
          checkout scm
          docker.withRegistry('', 'docker-registryID') {
          def customImage1 = docker.build("smutoni2/devops-pipe1:${env.BUILD_ID}")
           def customImage2 = docker.build("smutoni2/devops-pipe")
          customImage1.push()
           customImage2.push()
          }
    }
        
    }
}
    }
}

