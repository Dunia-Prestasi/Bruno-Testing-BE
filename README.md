# DuniaPrestasi Tes — Bruno

Collection ini mencakup **227 route**: 225 operasi Swagger dan 2 route operasional router (`GET /health` dan `GET /swagger/*any`).

Cakupan diverifikasi terhadap `internal/delivery/http/router_contract_test.go` — daftar rute otoritatif yang di-assert sama persis dengan router. Per verifikasi terakhir: **0 rute tanpa request, 0 request menunjuk rute yang sudah tidak ada.** Pemetaan rute ke file ada di `coverage.json`.

> Catatan: alur registrasi publik + approval (`/protected/registrations/*`) sudah dihapus dari backend dan digantikan `POST /registrations/offline`. Folder `01 Public - Registration` tetap ada dan kini berisi request offline tersebut.

## Cara pakai

1. Buka folder collection ini di Bruno dan pilih environment `Local`.
2. Ubah `base_origin`/`base_url` jika port API berbeda.
3. Isi kredensial `admin_*`, `teacher_*`, dan `student_*` pada environment.
4. Jalankan helper di folder `00 Test Setup` untuk menyimpan bearer token setiap role.
5. Jalankan request create terlebih dahulu. ID respons akan disimpan otomatis ke environment untuk request berikutnya.
6. Parameter query opsional tersedia tetapi dinonaktifkan secara default.

## Catatan penting

- Folder `05 Public - Catalog` memakai header `X-API-Key`, bukan bearer token. Isi variabel `public_api_key` pada environment dengan nilai `PUBLIC_API_KEY` milik backend, jika tidak seluruh request di folder itu akan menjawab 401.
- Folder `36 Admin - Dashboard and Reports` berisi dua endpoint yang mengembalikan file `.xlsx` biner, bukan JSON. Blok `financial` pada dashboard summary hanya muncul untuk pemegang `reports:financial`; export order menolak dengan 403 tanpa permission itu.
- Variabel `package_id` masih berisi UUID dummy; isi dengan ID paket asli sebelum menjalankan request attach/detach package.
- Request multipart sudah menunjuk ke asset dummy di folder `assets`.
- Bulk import memakai `assets/student-bulk-import.xlsx`; sesuaikan `course_slug` dan `batch_name` dengan data database.
- Endpoint delete, pembayaran, approval, dan webhook dapat mengubah data. Jalankan secara manual dan periksa environment sebelum mengirim.
- OAuth Google, email token, Midtrans, SMTP, R2, PostgreSQL, dan Redis tetap memerlukan konfigurasi backend yang aktif.
