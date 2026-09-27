AZHURA WEB — repository GitHub TERPISAH
=======================================
Unggah seluruh isi folder ini langsung ke ROOT repository baru bernama AZHURA_WEB.
Jangan upload folder pembungkus azhura_web_standalone.

RAILWAY: gunakan SERVICE WEB YANG SUDAH ADA (diplomatic-intuition).
Settings > Source > Disconnect repository lama, lalu Connect Repo -> AZHURA_WEB.
Root Directory: / (atau kosong)
Build Command: pip install -r requirements.txt
Start Command: gunicorn app:app --bind 0.0.0.0:$PORT --workers 2 --threads 4 --timeout 45

JANGAN mengubah service bot lama dan jangan membuat database baru.
Variables: pertahankan variabel web yang sudah ada. DATABASE_URL harus menunjuk PostgreSQL yang sama dengan bot.
BOT_TOKEN, BOT_USERNAME, WEB_SESSION_SECRET, GOOGLE_CLIENT_ID, ADMIN_ID,
ADMIN_USERNAME, FIVESIM_API_KEY, RUMAHOTP_API_KEY, PREMOTP_API_KEY,
MIDTRANS_SERVER_KEY, MIDTRANS_IS_PRODUCTION, WEB_ORDER_ENABLED
sesuai fitur yang digunakan. Jangan menyalin secret ke GitHub.
Domain web Railway yang sudah ada tetap pada service web yang sama.

CATATAN PENTING:
- database.py dan premotp.py adalah salinan modul dari ZIP terakhir, agar web bisa
  berjalan tanpa mengambil file dari repository bot. Mengubah skema atau API bot
  kelak perlu menyelaraskan salinan web.
- Fitur transaksi dan webhook pembayaran belum diuji dengan API/DB produksi.
- Tombol konfirmasi QRIS manual hanya notifikasi admin; admin memverifikasi mutasi.
- Pastikan endpoint Midtrans notification tetap menuju webhook aktif pada bot.
- Cadangkan PostgreSQL sebelum melakukan pengujian transaksi sungguhan.
