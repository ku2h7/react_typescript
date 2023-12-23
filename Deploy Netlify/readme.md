# How to Deploy React Project to Netlify

Berikut step - step untuk deploy project ke Netlify via terminal:

**1. Build React Project:**

Pertama deploy dulu project kalian dengan script berikut.

    npm run build

**2. Instalasi CLI Netlify:**

Instal CLI Netlify agar dapat mendeploy melalui baris perintah.

    npm install -g netlify-cli

**3. Masuk ke Akun Netlify:**

Gunakan perintah netlify login untuk masuk ke akun Netlify Anda.

    netlify login

**4. Inisialisasi Proyek di Netlify:**

Gunakan perintah netlify init untuk menginisialisasi proyek dan mengonfigurasi pengaturan deploy awal.

    netlify init

Pilih direktori build (biasanya dist) sebagai direktori yang akan di-deploy.

**5. Deploy ke Netlify:**

Setiap kali Anda ingin mendeploy perubahan, gunakan perintah berikut:

    netlify deploy

Ikuti instruksi yang muncul di terminal untuk menyelesaikan proses deploy.

**6. Deploy ke Production:**

    netlify deploy --prod

Project sudah ter deploy ke production Netlify
