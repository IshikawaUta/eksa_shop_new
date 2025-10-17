# Eksa Shop

Eksa Shop adalah aplikasi web e-commerce yang dibangun menggunakan **Flask** sebagai framework backend, **MongoDB** sebagai database, dan berbagai layanan eksternal seperti Imgur untuk unggah gambar dan Google OAuth untuk autentikasi. Aplikasi ini menyediakan fitur seperti manajemen produk, keranjang belanja, blog, kuis interaktif, ulasan produk, dan integrasi email untuk pengiriman struk pembelian.

## Fitur Utama
- **Manajemen Produk**: Admin dapat menambah, mengedit, dan menghapus produk dengan gambar yang diunggah ke Imgur.
- **Keranjang Belanja dan Checkout**: Pengguna dapat menambahkan produk ke keranjang, melihat subtotal, dan menyelesaikan pembelian dengan struk PDF yang dikirim melalui email.
- **Autentikasi Pengguna**: Mendukung login/registrasi manual dan login dengan Google OAuth.
- **Reset Kata Sandi**: Fitur pengaturan ulang kata sandi melalui email dengan tautan token yang aman.
- **Blog**: Admin dapat membuat, mengedit, dan menghapus postingan blog. Pengguna dapat menambahkan komentar dan balasan.
- **Kuis Interaktif**: Admin dapat membuat kuis dengan soal-soal terkait kategori tertentu, dan pengguna dapat mengikuti kuis untuk mendapatkan hasil skor.
- **Ulasan Produk**: Pengguna dapat memberikan ulasan dan rating untuk produk, dengan balasan dari admin.
- **Manajemen Kategori**: Admin dapat mengelola kategori produk dan kuis.
- **SEO dan Aksesibilitas**: Menyediakan sitemap.xml dan robots.txt untuk optimasi mesin pencari.
- **Integrasi Email**: Menggunakan Flask-Mail untuk mengirim struk pembelian dan email reset kata sandi.
- **PDF Generation**: Menggunakan ReportLab untuk membuat struk pembelian dalam format PDF.

## Teknologi yang Digunakan
- **Backend**: Flask (Python)
- **Database**: MongoDB (dengan PyMongo)
- **Autentikasi**: Google OAuth, Werkzeug untuk hashing kata sandi
- **Unggah Gambar**: Imgur API
- **Email**: Flask-Mail
- **PDF Generation**: ReportLab
- **Caching**: Flask-Caching
- **Frontend**: Jinja2 templates, HTML, CSS, JavaScript
- **Font**: Roboto (untuk PDF)
- **Lingkungan**: dotenv untuk pengelolaan variabel lingkungan

## Persyaratan
- Python 3.8+
- MongoDB (lokal atau cloud seperti MongoDB Atlas)
- Akun Imgur untuk API unggah gambar
- Akun Google Cloud untuk Google OAuth
- Layanan email SMTP (misalnya, Gmail) untuk pengiriman email
- File `.env` dengan konfigurasi berikut:
  ```plaintext
  SECRET_KEY=your-secret-key
  MONGO_URI=your-mongodb-uri
  IMGUR_CLIENT_ID=your-imgur-client-id
  GOOGLE_CLIENT_ID=your-google-client-id
  GOOGLE_CLIENT_SECRET=your-google-client-secret
  MAIL_SERVER=smtp.your-email-provider.com
  MAIL_PORT=587
  MAIL_USE_TLS=True
  MAIL_USERNAME=your-email-username
  MAIL_PASSWORD=your-email-password
  MAIL_DEFAULT_SENDER=your-email@example.com
  ```

## Struktur File Lengkap
Berikut adalah struktur direktori lengkap dari proyek ini. Struktur ini mencakup semua file dan folder utama yang diperlukan untuk menjalankan aplikasi.

```
eksa_shop_new/
├── static/                 # File statis seperti CSS, JS, dan gambar
│   ├── css/                # Folder untuk file CSS
│   │   ├── main.css        # CSS utama untuk styling aplikasi
│   │   └── admin.css       # CSS khusus untuk halaman admin
│   ├── js/                 # Folder untuk file JavaScript
│   │   ├── main.js         # JS utama untuk interaktivitas frontend
│   │   └── cart.js         # JS untuk manajemen keranjang belanja
│   └── images/             # Folder untuk gambar statis
│       └── placeholder.png # Gambar placeholder default
├── templates/              # Template Jinja2 untuk halaman HTML
│   ├── admin/              # Template khusus admin
│   │   ├── add_product.html
│   │   ├── edit_product.html
│   │   ├── blog_post_form.html
│   │   ├── quizzes.html
│   │   ├── add_quiz.html
│   │   ├── edit_quiz.html
│   │   ├── manage_questions.html
│   │   └── categories.html
│   ├── auth/               # Template untuk autentikasi
│   │   ├── login.html
│   │   ├── register.html
│   │   ├── create_first_admin.html
│   │   ├── forgot_password.html
│   │   └── reset_password.html
│   ├── cart/               # Template untuk keranjang dan checkout
│   │   ├── cart.html
│   │   └── checkout_success.html
│   ├── index.html          # Halaman utama
│   ├── product.html        # Daftar produk
│   ├── product_detail.html # Detail produk
│   ├── blog.html           # Daftar blog
│   ├── blog_detail.html    # Detail blog
│   ├── website_services.html
│   ├── help.html
│   ├── contact.html
│   ├── privacy_policy.html
│   ├── terms_and_conditions.html
│   ├── quiz_list.html      # Daftar kuis
│   ├── quiz_take.html      # Halaman mengerjakan kuis
│   ├── quiz_result.html    # Hasil kuis
│   └── 404.html            # Halaman error 404
├── index.py                # File utama aplikasi Flask
├── Roboto-Regular.ttf      # Font Roboto reguler untuk PDF
├── Roboto-Bold.ttf         # Font Roboto bold untuk PDF
├── logo.png                # Logo untuk struk PDF
├── requirements.txt        # Daftar dependensi Python
├── .env                    # File konfigurasi lingkungan (jangan commit ke repo)
├── .gitignore              # File untuk mengabaikan file tertentu di Git
├── LICENSE                 # File lisensi (misalnya MIT)
└── README.md               # Dokumentasi proyek ini
```

## Cara Instalasi
Ikuti langkah-langkah berikut untuk menginstal dan menjalankan aplikasi secara lokal.

1. **Kloning Repositori**
   ```bash
   git clone https://github.com/your-username/eksa_shop_new.git
   cd eksa_shop_new
   ```

2. **Buat Lingkungan Virtual**
   ```bash
   python -m venv venv
   source venv/bin/activate  # Untuk Linux/Mac
   venv\Scripts\activate     # Untuk Windows
   ```

3. **Instal Dependensi**
   Pastikan Anda memiliki `requirements.txt` dengan isi seperti:
   ```
   flask
   pymongo
   flask-mail
   flask-caching
   werkzeug
   markupsafe
   requests
   python-dotenv
   reportlab
   itsdangerous
   google-auth
   ```
   Jalankan:
   ```bash
   pip install -r requirements.txt
   ```

4. **Konfigurasi Database dan Layanan Eksternal**
   - Buat database MongoDB (lokal atau di Atlas) dan dapatkan URI-nya.
   - Daftar akun Imgur dan dapatkan Client ID.
   - Buat kredensial Google OAuth di Google Cloud Console.
   - Konfigurasi SMTP untuk email (misalnya, gunakan Gmail dengan app password).

5. **Buat File `.env`**
   Salin `example.env` (jika ada) ke `.env` dan isi dengan kredensial yang sesuai, seperti yang disebutkan di bagian Persyaratan.

6. **Jalankan Aplikasi**
   ```bash
   python index.py
   ```
   Aplikasi akan berjalan di `http://localhost:5000`. Akses melalui browser.

## Deployment
Untuk deploy aplikasi ke server produksi, ikuti panduan berikut. Disarankan menggunakan platform seperti Vercel, Heroku, atau server VPS (misalnya AWS EC2 atau DigitalOcean).

### 1. **Persiapan Deployment**
   - Pastikan semua dependensi terinstal dan `.env` dikonfigurasi dengan benar.
   - Tambahkan `Procfile` untuk platform seperti Heroku:
     ```
     web: gunicorn index:app
     ```
   - Instal Gunicorn jika belum:
     ```bash
     pip install gunicorn
     ```
   - Update `requirements.txt` dengan `pip freeze > requirements.txt`.

### 2. **Deployment ke Heroku**
   - Instal Heroku CLI dan login: `heroku login`.
   - Buat app baru: `heroku create nama-app-anda`.
   - Set variabel lingkungan: `heroku config:set SECRET_KEY=your-key` (lakukan untuk semua variabel di `.env`).
   - Push ke Heroku: `git push heroku main`.
   - Scale dyno: `heroku ps:scale web=1`.
   - Buka app: `heroku open`.

### 3. **Deployment ke Vercel**
   - Vercel lebih cocok untuk app Flask statis, tapi untuk full backend, gunakan Vercel dengan serverless functions atau deploy sebagai app Python.
   - Buat `vercel.json`:
     ```json
     {
       "version": 2,
       "builds": [
         { "src": "index.py", "use": "@vercel/python" }
       ],
       "routes": [
         { "src": "/(.*)", "dest": "index.py" }
       ]
     }
     ```
   - Deploy melalui Vercel CLI: `vercel --prod`.
   - Set environment variables di dashboard Vercel.

### 4. **Deployment ke VPS (Contoh: DigitalOcean)**
   - Buat droplet Ubuntu.
   - Instal Python, MongoDB, dan Nginx.
   - Clone repo, instal dependensi di virtualenv.
   - Jalankan dengan Gunicorn: `gunicorn --bind 0.0.0.0:5000 index:app`.
   - Konfigurasi Nginx sebagai reverse proxy.
   - Gunakan Supervisor atau systemd untuk menjaga app tetap berjalan.
   - Set environment variables di `/etc/environment` atau melalui script startup.

### Catatan Deployment
- Gunakan MongoDB Atlas untuk database cloud agar mudah skalabel.
- Pastikan SSL diaktifkan (gunakan Let's Encrypt atau cert dari platform).
- Monitor log dan error dengan tools seperti Sentry atau Heroku logs.
- Untuk produksi, set `DEBUG=False` di Flask config.

## Penggunaan
1. **Akses Halaman Utama**: Buka `http://localhost:5000` untuk melihat daftar produk.
2. **Login/Registrasi**: Gunakan `/login` atau `/register` untuk autentikasi.
3. **Blog**: Kunjungi `/blog` untuk melihat postingan.
4. **Kuis**: Akses `/quiz` untuk melihat daftar kuis.
5. **Keranjang dan Checkout**: Tambahkan produk ke keranjang melalui `/add_to_cart/<id>` dan selesaikan pembelian di `/checkout_success`.
6. **Struk PDF**: Struk akan dikirim ke email pengguna setelah checkout berhasil, atau dapat diunduh melalui `/generate-receipt/<order_id>`.

## Catatan Penting
- Pastikan semua variabel lingkungan diatur dengan benar di `.env` untuk menghindari kesalahan seperti kegagalan unggah gambar atau pengiriman email.
- File font (`Roboto-Regular.ttf`, `Roboto-Bold.ttf`) dan logo (`logo.png`) harus ada di direktori proyek untuk pembuatan PDF.
- Aplikasi menggunakan caching untuk meningkatkan performa, dengan timeout 2 detik untuk halaman yang sering diakses.

## Kontribusi
1. Fork repositori ini.
2. Buat branch baru (`git checkout -b feature/nama-fitur`).
3. Commit perubahan (`git commit -m 'Menambahkan fitur X'`).
4. Push ke branch (`git push origin feature/nama-fitur`).
5. Buat Pull Request.

## Lisensi
Proyek ini dilisensikan di bawah [MIT License](LICENSE).

## Kontak
Untuk dukungan atau pertanyaan, hubungi melalui email: [komikers09@gmail.com](mailto:komikers09@gmail.com) atau WhatsApp: +62895701060973.