pipeline {
    agent any

    stages {
        stage('SSH Command Execution') {
            steps {
                // SSH credentials ID kullanarak sshagent adımını kullanın
                sshagent(credentials: ['ssh']) {
                    script {
                        // Komutları çalıştır
                        sh '''
                        # ~/.ssh dizini yoksa oluştur ve izinlerini ayarla
                        if [ ! -d ~/.ssh ]; then
                            mkdir ~/.ssh
                            chmod 0700 ~/.ssh
                        fi
                        
                        # Hedef sunucunun SSH anahtarını known_hosts'a ekle
                        ssh-keyscan -t rsa,dsa 192.168.1.121 >> ~/.ssh/known_hosts
                        
                        # NFS sunucusuna SSH üzerinden komutları çalıştır
                        # Burada örnek bir komut kullanıldı, ihtiyacınıza göre değiştirebilirsiniz.
                        ssh nfs@192.168.1.121 uptime
                        '''
                    }
                }
            }
        }
    }
}
