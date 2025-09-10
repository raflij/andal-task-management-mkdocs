# Post-Incident Response & Security Improvements

| Phase | Task | SubTask | Estimate Hour | Goal | Status |
|-------|------|---------|---------------|------|--------|
| **0** | **Mengamankan iDRAC** | | | | |
| | | Mengganti semua password dari dokumen lama | 1 | Menghilangkan potensi akses tidak sah melalui kredensial lama | Done |
| | | Membuat username devops baru | 1 | | Done |
| | | Menonaktifkan/Menghapus akses root dan user lain | 1 | Memisahkan akses administratif dengan kredensial unik | Done |
| | | Periksa Kunci SSH yang tersimpan | 2 | Menghapus akses berbasis SSH yang tidak sah | Done |
| | | Cek Integrasi Direktori (LDAP/Active Directory) | 2 | Memastikan integrasi sesuai kebijakan keamanan | Done |
| | | Audit Log | 2 | Mengidentifikasi aktivitas mencurigakan | Done |
| | | Implementasi Remote Syslog | 4 | Memastikan semua log terkirim ke server terpusat | Cancelled |
| | **Tracing IP mencurigakan 192.168.80.1 & 192.168.24.1 saat kejadian ransomware** | | | | |
| | | Capture log lalu lintas jaringan pada waktu kejadian | 4 | Mendapatkan bukti lalu lintas terkait serangan | Done |
| | | Identifikasi source & destination connection mencurigakan | 3 | Menentukan titik masuk & arah serangan | Cancelled |
| **1** | **Scanning RDP Windows Baru di Colo** | | | | |
| | | Membuat RDP baru di Colo | 1 | | Cancelled |
| | | Jalankan port scan untuk deteksi RDP terbuka | 1 | | Cancelled |
| | | Periksa konfigurasi keamanan RDP (NLA, whitelist IP) | 2 | Memastikan RDP aman | Cancelled |
| **2** | **Scanning RDP salah satu Customer di Colo** | | 6 | | Cancelled |
| **3** | **POC MikroTik di Blok C** | | | | |
| | | Deploy MikroTik lab dengan topologi VLAN sama persis (24, 25, 99, dll) | 4 | Replikasi environment Colo untuk testing | Done |
| | | Terapkan aturan masquerade yang sama seperti konfigurasi Colo (baseline) | 2 | Memastikan hasil uji identik dengan kondisi existing | Done |
| | | Uji logging saat serangan internal (ssh brute-force simulasi) | 2 | Validasi problem log visibility | Done |
| | | Terapkan perbaikan (hapus masquerade antar VLAN, segmentasi firewall, mgmt ACL) | 4 | Membuktikan solusi bisa jalan tanpa ganggu traffic | Done |
| | | Dokumentasikan hasil test (before/after config & log visibility) | 2 | Jadi referensi implementasi di Colo | Cancelled |
| **4** | **Perbaikan Konfigurasi MikroTik Colo** | | | | |
| | | Hapus aturan masquerade antar VLAN di /ip firewall nat | 2 | Pastikan IP source tercatat dengan benar di log | Cancelled |
| | | Terapkan aturan firewall antar VLAN (deny by default, allow by need) | 3 | Segmentasi lalu lintas internal | Cancelled |
| | | Audit NAT dan ACL lainnya | 2 | Pastikan tidak ada celah eskalasi | Done |
| **5** | **Deploy Visibility & Monitoring** | | | | |
| | | Implementasi remote syslog ke server SIEM/ELK | 6 | Centralized log untuk analisis | Done |
| | | Deploy EDR ringan (misal Wazuh/Velociraptor) di semua VM | 3 | Deteksi serangan endpoint real-time | Done |
| **6** | **Implementasi Kontrol Akses** | | | | |
| | | Deploy PAM untuk akun administratif | 3 | Kredensial administratif terkontrol | Planned |


---
*Last Updated: September 10, 2025*