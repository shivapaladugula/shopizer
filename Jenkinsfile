pipeline {
        agent {
             label 'Node1'
        }
          parameters {
              choice(name: 'CHOICE', choices: [SPRINT_1_REL], description: 'CHOICE')
          }
    
    stages {
        stage('Git') {
            steps {
                git url: 'https://github.com/shivapaladugula/shopizer.git',
                branch: "${params.CHOICE}"
            }
        }
        stage('Build') {
            steps {
                sh 'mvn package'
            }
        }
        stage('archive') {
            steps {
                archiveArtifacts artifacts: 'sm-core/target/*.jar', followSymlinks: false
            }
        }
         stage('reports') {
            steps {
                junit 'sm-shop/target/surefire-reports/*.xml'
            }
        }
    }
}
