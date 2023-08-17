pipeline{
agent { label 'slave-2' }
    stages {
       stage ("1. install nginx") {
          steps{
              sh "sudo amazon-linux-extras install nginx1"
              sh "mkdir -p inbound"
              sh "mkdir -p outbound"
              }
          }
      stage ("2. service install"){
          steps{
                 sh "sudo yum update -y"
                 sh "sudo yum install docker -y"
              }
          }
      stage ("3. service start"){
          steps{
              sh "sudo systemctl restart docker"
              sh "sudo systemctl enable docker"
              }
          }
       stage ("4. verify nginx"){
          steps{
              sh "rpm -qa | grep nginx"
              }
          }
      stage ("5. execute date command and save in a file"){
          steps {
                sh "pwd"
                sh "cd /home/ec2-user/"
                sh "touch error.html"
                writeFile(file: "/home/ec2-user/index.html", text: "this is declarative pipeline", encoding: "UTF-8") 

              }
          }
        stage ("5. create file"){
          steps{
             sh "touch ~/newfile.txt"
              }
          }

 }

}
