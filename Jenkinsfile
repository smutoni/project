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
          def customImage = docker.build("smutoni2/devops-pipeline2:${env.BUILD_ID}")
           def customImage = docker.build("smutoni2/devops-pipeline1")
          customImage2.push()
           customImage1.push()
          }
    }
        
    }
}
    }
}

