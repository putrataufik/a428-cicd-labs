# a428-cicd-labs
Pertama itu harus Run Jenkins menggunakan perintah docker yaitu "docker network create jenkins"
nanti bakal terbuat docker:dind
abis itu bikin Dockerfile di C:\Users\ASUS/Dockerfile, isinya itu untuk install plugin Blue Ocean dan Docker Pipelines.
setelah itu buat image "docker build -t myjenkins-blueocean:2.346.1-1 ."
setelah build selesai baryu jalankan blueoceannya

kemudian masuk ke localhost:8080. disitu akan diminta administrator password yang bisa di liat dengan cara "docker logs jenkins-blueocean" . pass saya itu d78c864359934335b45cc123fa86xxxx. kemudian disuruh buat akun. dan memilih Install Suggested Plugins. 
Sekarang melakukan fork repo react app ke aku github saya dengan cara "git clone -b react-app https://github.com/putrataufik/a428-cicd-labs.git" dan saya clone di sini "C:\Users\ASUS\OneDrive\Documents\contoh\a428-cicd-labs"

masuk kembali ke jenkins untuk membuat pipelines nya dan atur pipeline menggunakan repo lokal yang tadi sudah di clone.

disini saya gunakan vscode, masuk ke branch react-app dan bikin Jenkinsfile, didalam file itu terdapat code seperti ini
pipeline {
    agent {
        docker {
            image 'node:16-buster-slim'      // Pakai image Docker Node.js untuk build
            args '-p 3000:3000'              // Publish port 3000 dari container
        }
    }
    stages {
        stage('Build') {    
                             // Tahap Build
            steps {
                sh 'npm install'             // iiuhiuh Install semua dependencies React Appg
            }
        }
    }
}
.kemudian save dan push ke github

kembali lagi ke jenkins trus buka Open Blue Oceannya. nah disitu sudah ada react-app yang sebelumnya sudah di atur pada saat membuat pipelines. kemudian klik run. nah nanti kalau sudah selesai nanti tampilan Blue Oceannya menjadi warna hijau.
