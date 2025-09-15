# FormulirMedfokom-
formulir 
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulir Pemesanan Desain</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
        }
        .container {
            background-color: #fff;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 600px;
            box-sizing: border-box;
            transition: all 0.5s ease;
        }
        h1 {
            text-align: center;
            color: #333;
            margin-bottom: 20px;
        }
        .form-group {
            margin-bottom: 15px;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input[type="text"], textarea, select {
            width: 100%;
            padding: 10px;
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 16px;
        }
        input[type="text"]:focus, textarea:focus, select:focus {
            border-color: #007bff;
            outline: none;
        }
        textarea {
            resize: vertical;
        }
        .required::after {
            content: " *";
            color: red;
        }
        .btn-kirim {
            display: block;
            width: 100%;
            padding: 12px;
            background-color: #007bff;
            color: #fff;
            border: none;
            border-radius: 4px;
            font-size: 18px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }
        .btn-kirim:hover {
            background-color: #0056b3;
        }
        .success-message {
            color: green;
            margin-top: 10px;
            display: none;
        }
        #text-to-copy {
            background-color: #f9f9f9;
            border: 1px solid #ddd;
            padding: 20px;
            border-radius: 4px;
            white-space: pre-wrap;
            word-wrap: break-word;
            text-align: left;
            margin-bottom: 20px;
            line-height: 1.6;
        }
        .btn-copy, .btn-whatsapp {
            padding: 12px 24px;
            border: none;
            border-radius: 4px;
            font-size: 18px;
            cursor: pointer;
            transition: background-color 0.3s ease;
            margin: 5px;
        }
        .btn-copy {
            background-color: #28a745;
            color: #fff;
        }
        .btn-copy:hover {
            background-color: #218838;
        }
        .btn-whatsapp {
            background-color: #25D366;
            color: #fff;
        }
        .btn-whatsapp:hover {
            background-color: #128C7E;
        }
        .whatsapp-note {
            margin-top: 10px;
            font-size: 14px;
            color: #555;
            text-align: center;
        }
        #halaman2 {
            display: none;
        }
    </style>
</head>
<body>

    <div class="container" id="halaman1">
        <h1>Formulir Pemesanan Desain</h1>
        <form id="pemesananForm">
            <div class="form-group">
                <label for="atas_nama" class="required">ATAS NAMA:</label>
                <input type="text" id="atas_nama" name="atas_nama" required>
            </div>

            <div class="form-group">
                <label for="bidang" class="required">BIDANG:</label>
                <input type="text" id="bidang" name="bidang" required>
            </div>

            <div class="form-group">
                <label for="jenis_desain" class="required">JENIS DESAIN:</label>
                <select id="jenis_desain" name="jenis_desain" required>
                    <option value="" disabled selected>Pilih salah satu...</option>
                    <option value="Poster">Poster</option>
                    <option value="Undangan">Undangan</option>
                    <option value="custom">Custom</option>
                </select>
                <input type="text" id="custom_desain" name="custom_desain" style="display:none; margin-top: 10px;" placeholder="Masukkan jenis desain lainnya">
            </div>

            <div class="form-group">
                <label for="nama_acara" class="required">NAMA ACARA:</label>
                <input type="text" id="nama_acara" name="nama_acara" required>
            </div>

            <div class="form-group">
                <label for="tema" class="required">TEMA:</label>
                <input type="text" id="tema" name="tema" required>
            </div>

            <div class="form-group">
                <label for="yang_dibuat" class="required">APA SAJA YANG DIBUAT:</label>
                <textarea id="yang_dibuat" name="yang_dibuat" rows="3" required></textarea>
            </div>

            <div class="form-group">
                <label for="catatan">CATATAN:</label>
                <textarea id="catatan" name="catatan" rows="3" placeholder="Contoh: tambahkan elemen tunas kelapa di dalam desainnya"></textarea>
            </div>
            
            <button type="submit" class="btn-kirim">KIRIM</button>
        </form>
    </div>

    <div class="container" id="halaman2">
        <h1>SALIN DAN KIRIM</h1>
        <div class="whatsapp-note">
            Silakan salin teks di bawah ini dan kirimkan melalui WhatsApp ke:<br>
            **KOPASTAMA +62 813-1387-5095**
        </div>
        <pre id="text-to-copy">Teks formulir Anda akan muncul di sini...</pre>
        <button class="btn-copy">SALIN</button>
        <button class="btn-whatsapp">KIRIM VIA WHATSAPP</button>
        <div id="success-message" class="success-message">Teks berhasil disalin!</div>
    </div>

    <script>
        const form = document.getElementById('pemesananForm');
        const jenisDesain = document.getElementById('jenis_desain');
        const customDesain = document.getElementById('custom_desain');
        const catatanTextarea = document.getElementById('catatan');
        const halaman1 = document.getElementById('halaman1');
        const halaman2 = document.getElementById('halaman2');
        const textToCopyElement = document.getElementById('text-to-copy');
        const copyButton = document.querySelector('.btn-copy');
        const whatsappButton = document.querySelector('.btn-whatsapp');
        const successMessage = document.getElementById('success-message');

        // Menampilkan atau menyembunyikan input 'custom'
        jenisDesain.addEventListener('change', function() {
            if (this.value === 'custom') {
                customDesain.style.display = 'block';
                customDesain.setAttribute('required', 'required');
            } else {
                customDesain.style.display = 'none';
                customDesain.removeAttribute('required');
                customDesain.value = '';
            }
        });

        // Mengatur placeholder saat halaman pertama kali dimuat dan saat keluar fokus
        catatanTextarea.addEventListener('focus', function() {
            if (this.placeholder) {
                this.placeholder = '';
            }
        });
        catatanTextarea.addEventListener('blur', function() {
            if (!this.value) {
                this.placeholder = 'Contoh: tambahkan elemen tunas kelapa di dalam desainnya';
            }
        });
        document.addEventListener('DOMContentLoaded', function() {
            catatanTextarea.placeholder = 'Contoh: tambahkan elemen tunas kelapa di dalam desainnya';
        });

        // Event listener untuk pengiriman formulir
        form.addEventListener('submit', function(event) {
            event.preventDefault();

            // Ambil data dari semua input
            const dataForm = {
                atas_nama: document.getElementById('atas_nama').value,
                bidang: document.getElementById('bidang').value,
                jenis_desain: jenisDesain.value === 'custom' ? customDesain.value : jenisDesain.value,
                nama_acara: document.getElementById('nama_acara').value,
                tema: document.getElementById('tema').value,
                yang_dibuat: document.getElementById('yang_dibuat').value,
                catatan: document.getElementById('catatan').value,
            };

            // Format teks untuk disalin
            const formattedText = `
*FORMULIR PEMESANAN DESAIN*

*ATAS NAMA:* ${dataForm.atas_nama}
*BIDANG:* ${dataForm.bidang}
*JENIS DESAIN:* ${dataForm.jenis_desain}
*NAMA ACARA:* ${dataForm.nama_acara}
*TEMA:* ${dataForm.tema}
*APA SAJA YANG DIBUAT:* ${dataForm.yang_dibuat}
*CATATAN:* ${dataForm.catatan || '-'}
            `.trim();

            textToCopyElement.textContent = formattedText;

            // Tampilkan halaman 2 dan sembunyikan halaman 1
            halaman1.style.display = 'none';
            halaman2.style.display = 'block';
        });

        // Event listener untuk tombol Salin
        copyButton.addEventListener('click', function() {
            const textToCopy = textToCopyElement.textContent;
            navigator.clipboard.writeText(textToCopy).then(() => {
                successMessage.style.display = 'block';
                setTimeout(() => {
                    successMessage.style.display = 'none';
                }, 2000);
            }).catch(err => {
                console.error('Gagal menyalin teks: ', err);
                alert('Gagal menyalin teks. Silakan salin manual.');
            });
        });

        // Event listener untuk tombol Kirim via WhatsApp
        whatsappButton.addEventListener('click', function() {
            const textToCopy = textToCopyElement.textContent;
            const phoneNumber = '6281313875095'; // Ganti dengan nomor WhatsApp
            const encodedText = encodeURIComponent(textToCopy);
            const whatsappUrl = `https://wa.me/${phoneNumber}?text=${encodedText}`;
            window.open(whatsappUrl, '_blank');
        });
    </script>
</body>
</html>
