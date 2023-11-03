pipeline {
    agent {
        label 'testnode2'
    }
    environment {
        SNYK_TOKEN = credentials('asubedisnyktoken') 
        

    stages {
        stage('checkout') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Research-Associate-Internship/asubeditest2_.git']])
            }
        }
        stage('build') {
            steps {
                sh 'npm install'
            }
        }
        stage('sast-testing') {
            steps {
                sh """
                #set +x
                snyk auth ${env.SNYK_TOKEN}
                #snyk test --json | snyk-to-html > /home/ubuntu/Snyk_Report_${BUILD_ID}.html
                """
                }
            }
        }
        } 
        
        /*stage('run-application') {
            steps {
                sh 'docker run -d -p 80:3000 --name owasp bkimminich/juice-shop'
            }
        }
        stage('dast-testing') {
            steps {
                sh 'cd /usr/share/owasp-zap; ./zap.sh -cmd -quickurl http://34.200.236.39:80 -quickout /home/ubuntu/zap_reports/JENKINS_ZAP_VULNERABILITY_REPORT_${BUILD_ID}.html -quickprogress'
                
            }
        }
        stage('stop-application') {
            steps {
                sh 'docker stop $(docker ps -q)'
                sh 'docker rm $(docker ps -a -q)'
            }
        }*/
    /*}*/
    /*post {
        always {
            publishHTML(target: [
                allowMissing:false,
                alwaysLinkToLastBuild:true,
                keepAll:true,
                reportDir:'/home/ubuntu/zap_reports',
                reportFiles: 'JENKINS_ZAP_VULNERABILITY_REPORT_${BUILD_ID}.html',
                reportName: 'OWASP_ZAP_Scan_Report'
                ])
        }
    }
}*/
