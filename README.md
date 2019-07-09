Deployment Guideline
==================================
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

### Daftar Isi

- [Deployment ke production](#deployment-ke-production)
  - [Pedoman Deployment ke Production](#pedoman-deployment-ke-production)
- [Deployment sprint mobile android ke production](#deployment-sprint-mobile-android-ke-production)
  - [Pedoman Deployment sprint mobile android ke production](#pedoman-deployment-sprint-mobile-android-ke-production)

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



