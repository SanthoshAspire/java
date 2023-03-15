pipeline {
    agent any
     tools {
    maven 'Maven'
  }
      environment {
        SNAP_REPO = 'demo-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'admin'
        RELEASE_REPO = 'demo-release'
        CENTRAL_REPO = 'demo-maven-central'
        NEXUSIP = '3.7.66.246'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'demo-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
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
	//	    post {
        //        success {
        //            echo "Now Archiving."
        //            archiveArtifacts artifacts: '**/*.war'
        //        }
        //    }
	    }
	 }
	//	stage('Checkstyle Analysis'){
        //    steps {
        //        sh 'mvn -s settings.xml checkstyle:checkstyle'
        //    }
       // }
       // #stage('Deliver') {
       // #    steps {
       // #        sh './jenkins/scripts/deliver.sh'
       // #    }
       // #}
    }
}
