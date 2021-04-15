// path of the template to use
def templatePath = 'nodejs-mongodb-example'
// name of the template that will be created
def templateName = 'nodejs-mongodb-example'
// NOTE, the "pipeline" directive/closure from the declarative pipeline syntax needs to include, or be nested outside,
// and "openshift" directive/closure from the OpenShift Client Plugin for Jenkins.  Otherwise, the declarative pipeline engine
// will not be fully engaged.
pipeline {
    agent {
      node {
        // spin up a node.js slave pod to run this build on
        label 'nodejs'
      }
    }
    options {
        // set a timeout of 20 minutes for this pipeline
        timeout(time: 20, unit: 'MINUTES')
    }

    stages {
        stage('preamble') {
            steps {
                script {
                    openshift.withCluster() {
                        openshift.withProject() {
                            echo "Using project: ${openshift.project()}"
                        }
                    }
                }
            }
        }
        stage('create') {
            steps {
                script {
                    openshift.withCluster() {
                        openshift.withProject() {
                            // create a new application from the templatePath
                            openshift.newApp( 'https://github.com/Dienstfreude/DO280-apps', '--as-deployment-config', '--context-dir hello-world-nginx')
                        }
                    }
                } // script
            } // steps
        } // stage
    } // stages
} // pipeline
