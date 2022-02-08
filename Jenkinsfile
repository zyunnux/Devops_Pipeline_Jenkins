pipeline {
    agent any
    stages {
	
	stage('Git-Checkout') {
	    steps {
                echo "Checking out from Git Repo";
                git 'https://github.com/zyunnux/Devops_Pipeline_Jenkins.git'
            }
        }
        
    stage('Build') {
        steps {
            echo "Building the checkout project!";
            sh 'Build.bat'
        }
    }

    stage('Unit-Test') {
        steps {
            echo "Running JUnit Tests";
            sh 'Unit.bat'
        }
    }

    stage('Quality-Gate') {
        steps {
            echo "Verifying Quality Gates";
            sh 'Quality.bat'
        }
    }

    stage('Deploy') {
        steps {
            echo "Deploying to Stage Environment for more tests!";
            bat 'Build.bat'
        }
    }
    }

    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }

    }
}
       