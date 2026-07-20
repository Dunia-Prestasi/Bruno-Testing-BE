# DuniaPrestasi Tes — Bruno

Collection ini mencakup **209 route**: 206 operasi Swagger dan 3 route operasional router.

## Cara pakai

1. Buka folder collection ini di Bruno dan pilih environment `Local`.
2. Ubah `base_origin`/`base_url` jika port API berbeda.
3. Isi kredensial `admin_*`, `teacher_*`, dan `student_*` pada environment.
4. Jalankan helper di folder `00 Test Setup` untuk menyimpan bearer token setiap role.
5. Jalankan request create terlebih dahulu. ID respons akan disimpan otomatis ke environment untuk request berikutnya.
6. Parameter query opsional tersedia tetapi dinonaktifkan secara default.

## Catatan penting

- Request multipart sudah menunjuk ke asset dummy di folder `assets`.
- Bulk import memakai `assets/student-bulk-import.xlsx`; sesuaikan `course_slug` dan `batch_name` dengan data database.
- Endpoint delete, pembayaran, approval, dan webhook dapat mengubah data. Jalankan secara manual dan periksa environment sebelum mengirim.
- OAuth Google, email token, Midtrans, SMTP, R2, PostgreSQL, dan Redis tetap memerlukan konfigurasi backend yang aktif.
