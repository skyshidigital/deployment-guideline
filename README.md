Deployment Guideline
==================================
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

### Daftar Isi

- [Deployment ke production](#deployment-ke-production)
  - [Pedoman Deployment ke Production](#pedoman-deployment-ke-production)
- [Deployment sprint mobile android ke production](#deployment-sprint-mobile-android-ke-production)
  - [Pedoman Deployment sprint mobile android ke production](#pedoman-deployment-sprint-mobile-android-ke-production)
- [Pedoman penamaan versi apps android](#pedoman-penamaan-versi-apps-android)
- [Pedoman Dokumentasi Deployment](#pedoman-dokumentasi-deployment)
- [Pedoman Penangaan Request dari Klien untuk Join Source Code Management](#pedoman-penangaan-request-dari-klien-untuk-join-source-code-management) 

### Deployment ke production
#### Pedoman Deployment ke Production
Yang diperlukan saat Deployment ke Production adalah :
- Deployment hanya boleh dilakukan diluar jam kerja, jadwal deployment mengikuti jadwal sesuai kesepakatan dengan client atau product owner
- Apabila ada reschedule jadwal harus ada pemberitahuan kepada seluruh tim yang berkaitan dan tetap dilakukan diluar jam kerja
- Jadwal perencanaan rilis 1-2 hari sebelumnya
- Wajib sudah lolos UAT oleh QA
- Menyediakan dokumen planning migrasi jika ada penambahan atau perubahan konfigurasi dan jika ada penambahan atau perubahan pada struktur data
- Zero downtime, menggunakan cluster dengan minimum 2 nodes, sehingga auto failover ketika sedang dalam proses upgrade
- Siapkan dua server SIT dan UAT ( SIT adalah staging server dengan staging data, sedangkan UAT adalah staging server dengan live data. UAT mirip dengan live site, namun tidak diakses oleh user).
- Deployment terlebih dulu ke UAT, untuk menghindari failure pada saat deployment ke live
- Gunakan container seperti kubernetes untuk memudahkan deployment ke live site atau revert


### Deployment sprint mobile android ke production
#### Pedoman Deployment sprint mobile android ke production
Yang diperlukan saat Deployment sprint mobile android ke production adalah :
- Aktifkan beta release di Google Play Console, namun jika beta tidak boleh dipublish ke public maka bisa menggunakan alpha release atau closed invitation
- Upload APK yang terbaru di beta release pada google play console
- Tunggu beberapa saat, maka aplikasi akan muncul di PlayStore
- Undang client atau pihak lain yang akan terlibat untuk menguji aplikasi di live
- Setelah aplikasi berhasil diunduh dari playstore oleh client dan pihak tester, dan mendapat approval dari client
- Maka rollout aplikasi 25% ke production
- Cek Firebase secara berkala selama 3 hari berturut2, apakah ada laporan issue atau peningkatan crash rate ?
- Jika dalam 3 hari tidak ada laporan peningkatan crash rate atau issue aneh lainnya, maka tingkatkan rollout 3 hari berikutnya dan seterusnya hingga 50%, 75%, dan 100%

## Pedoman penamaan versi apps android
- Penamaan pada versi android dibagi menjadi 3 sequence, contoh : X menandakan versi major, Y menandakan versi sprint dan Z adalah hotfix jika dibutuhkan pada versi tersebut

- Pada setiap versi nomor hanya berisi angka, bernilai positif dan bernilai bulat tidak boleh menggunakan alphabet, bernilai negatif dan desimal. Contoh :
    - 1.1.0 bukan 1.2.0a
    - 1.2.0 bukan 1.2.0b
    
- Setiap hotfix yang dilakukan, akan ditambahkan berdasarkan update versi terbaru pada playstore, meskipun hotfix masih terkait dengan sprint pada periode sebelumnya, contoh :
    - 1.2.1
    - 1.2.2
    - 1.2.3
    
- Pada saat release sprint terbaru akan dimulai dengan versi hotfix 0, contoh :
    - 1.2.0
    - 1.3.0
    - 1.4.0
    
 ## Pedoman Dokumentasi Deployment
 Pada saat mengalami gagal deployment ke staging atau menemukan kendala mengenai deployment, dapat ditangani dengan langkah-langkah sebai berikut :
- Setiap ada kegagalan deployment, Developer wajib mencatat keluhan dan perbaikan pada `Document backlog guideline`
- Lead Developer melakukan analisa dan melakukan perubahan pada `Document Guideline`
- Publikasi dan sosialisasi perubahan yang terdapat pada `Document guideline` kepada seluruh Developer yang bersangkutan.

## Pedoman Penangaan Request dari Klien untuk Join Source Code Management
Pedoman penanganan request dari klien untuk join source management (gitlab.skyshi.io) sebagai berikut :
- Permintaan dari klien harus dikonfirmasi dan mendapat approval oleh COO
- Klien hanya diberikan akses _`read only`_

