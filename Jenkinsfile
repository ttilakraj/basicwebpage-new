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
                    def targetTomcatServer
                    
                    if (env.BRANCH_NAME == 'main') {
                        sh "cp index.html ${tomcatWebappsDir}"
                        targetTomcatServer = "http://3.234.86.185:8090/"
                    } else if (env.BRANCH_NAME == 'master') {
                        sh "cp index.html ${tomcatWebappsDir}"
                        targetTomcatServer = "http://54.80.115.152:8091/"
                    } else {
                        echo "Unsupported branch"
                        return
                    }
                    
                    deployToTomcat(targetTomcatServer)
                }
            }
        }
    }
}

def deployToTomcat(serverUrl) {
    sh "curl -T ${TOMCAT_WEBAPPS}/index.html ${serverUrl}"
}
