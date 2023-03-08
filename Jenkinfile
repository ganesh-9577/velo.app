pipeline {
    agent {
        label {
            label "built-in"
            customWorkspace "/mnt/project"
        }
    }
    stages {
        stage ("clone") {
            steps {
                sh "ansible devlinux[0] -b -m yum -a "pkg=httpd state=present"  "
            }
        }
        stage ("deploy") {
            steps {
                sh "ansible devlinux[0] -b -m service -a "name=httpd state=started"  "  
                sh "ansible devlinux[0] -b -m copy -a "src=/mnt/project/velo.app/index.html dest=/var/www/html" "
            }
        }
    }
}
