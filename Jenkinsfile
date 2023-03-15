pipeline {
    agent any
     tools {
    maven 'MAVEN_JENKINS'
  }
    stages {
        stage('Build') {
            steps {
		sh 'mvn compile'    
                sh 'mvn -B -DskipTests clean package'
		echo 'converted the code from human readable to machine readable '
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
	 stage("convert the code to package"){
            steps{
                sh "mvn clean package"
                echo 'convert the files to war file'
	    }
	 }
		stage('Checkstyle Analysis'){
            steps {
                sh 'mvn -s settings.xml checkstyle:checkstyle'
            }
        }
       // #stage('Deliver') {
       // #    steps {
       // #        sh './jenkins/scripts/deliver.sh'
       // #    }
       // #}
    }
}
