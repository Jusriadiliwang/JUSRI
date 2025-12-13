pipeline {
    agent any

    stages {
        stage('Hello World Stage') {
            steps {
                echo 'Tahap 1: Persiapan dan Build awal selesai.'
            }
        }

        stage('Manual Approval for Prod') {
            steps {
                // Timeout diatur selama 15 menit
                timeout(time: 15, unit: 'MINUTES') {
                    input(
                        message: "PERHATIAN: Apakah Anda yakin ingin melakukan Deployment ke Production?",
                        ok: "Lanjutkan Deployment",
                        submitter: 'authenticated',
                        id: 'ProductionApproval'
                    )
                }
            }
        }

        stage('Production Deployment') {
            steps {
                echo 'Tahap 3: Deployment ke Production disetujui dan dimulai!'
                // PERBAIKAN: Menggunakan 'bat' untuk kompatibilitas Windows
                bat 'echo %DATE% %TIME%' 
                echo 'Deployment selesai.'
            }
        }
    }
}