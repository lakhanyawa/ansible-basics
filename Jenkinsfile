pipeline {
    agent any
    stages {
         stage('Run SSH command') {
             steps {
                 script {
                     sshagent(credentials : ['root']) {
                        sh "echo pwd"
                        sh 'ssh -t -t root@192.168.77.137 -o StrictHostKeyChecking=no'
                        sh "echo pwd"
                        sh 'sudo -i -u root'
                        sh 'systemctl restart docker'
                        sh 'echo pwd'
                        sh (script:'''git diff-tree --no-commit-id --name-only -r '$COMMIT_ID' |awk -F\'/\' \'{print $1}\' ''',returnStdout: true).trim();
                    }
                 }
             }
         }
     }
}
