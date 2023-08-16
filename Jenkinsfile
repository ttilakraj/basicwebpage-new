pipeline {
    agent any

    environment {
        TOMCAT_WEBAPPS = '/var/lib/tomcat9/webapps' // Set this to the actual path of the Tomcat webapps directory
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the Git repository
                checkout scm
            }
        }
        stage('Copy HTML to Tomcat') {
            steps {
                script {
                    def tomcatWebappsDir = "/var/lib/tomcat9/webapps/ROOT/"

                    if (env.BRANCH_NAME == 'main') {
                        sh "sudo cp index.html ${tomcatWebappsDir}"
                    } else if (env.BRANCH_NAME == 'master') {
                        sh "sudo cp index1.html ${tomcatWebappsDir}"
                    } else {
                        echo "Unsupported branch"
                    }
                }
            }
        }
    }
}
