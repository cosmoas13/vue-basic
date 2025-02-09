# Lifecycle Hooks di Vue.js

Vue.js menyediakan berbagai lifecycle hooks yang memungkinkan pengembang menjalankan logika tertentu pada tahapan berbeda dari siklus hidup sebuah komponen. Berikut adalah penjelasan untuk setiap hook:

---

## 1. `onBeforeMount`
- Dipanggil sebelum template komponen dirender ke dalam DOM.
- Cocok untuk logika awal yang tidak memerlukan akses ke DOM.

---

## 2. `onMounted`
- Dipanggil setelah template komponen selesai dirender dan dimasukkan ke dalam DOM.
- Cocok untuk operasi yang membutuhkan akses ke DOM, seperti manipulasi elemen atau inisialisasi data dari API.

---

## 3. `onBeforeUpdate`
- Dipanggil sebelum perubahan data memicu re-render komponen.
- Berguna untuk persiapan logika sebelum DOM diperbarui.

---

## 4. `onUpdated`
- Dipanggil setelah perubahan data menyebabkan DOM diperbarui.
- Digunakan untuk kode yang membutuhkan DOM dalam keadaan terbaru.

---

## 5. `onBeforeUnmount`
- Dipanggil sebelum komponen dilepas dari DOM.
- Berguna untuk membersihkan resource, seperti event listener atau timer.

---

## 6. `onActivated`
- Dipanggil saat komponen diaktifkan kembali (khusus untuk komponen dalam `<keep-alive>`).
- Berguna untuk memulihkan state atau data yang dinonaktifkan sementara.

---

## 7. `onDeactivated`
- Dipanggil saat komponen dinonaktifkan sementara (khusus untuk `<keep-alive>`).
- Cocok untuk menyimpan state sebelum komponen dinonaktifkan.

---

## 8. `onErrorCaptured`
- Dipanggil saat error terjadi di dalam child komponen.
- Digunakan untuk menangkap error, logging, atau menampilkan fallback UI.

---

## Catatan
- Semua hooks ini digunakan dalam Composition API dengan `setup()`.
- Untuk menggunakan hooks, impor dari Vue: `import { onMounted, onBeforeUnmount } from 'vue';`.

