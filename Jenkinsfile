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
                        sh "cp index.html ${tomcatWebappsDir}"
                    } else if (env.BRANCH_NAME == 'master') {
                        sh "cp index.html ${tomcatWebappsDir}"
                    } else {
                        echo "Unsupported branch"
                    }
                }
            }
        }
    }
}
