# Log Prompt AI --- UTS Coding Akuntansi

Dokumen ini mencatat prompt yang digunakan dalam penyusunan purwarupa Voucher Entri Transaksi Kas Keluar dan evaluasi logika sistem.

---

## 1. Gemini Canvas --- Pembuatan Purwarupa HTML

### Prompt yang Digunakan:
> "Buat prototipe aplikasi web Voucher Entri Transaksi Kas Keluar menggunakan HTML5, Tailwind CSS CDN, dan Vanilla JavaScript. Integrasikan rancangan dengan struktur database PostgreSQL, yaitu chart_of_accounts, journal_headers, dan journal_lines dengan fitur live balanced indicator dan zero discrepancy."

---

## 2. NotebookLM --- Verifikasi Aturan Bisnis & Kepatuhan PSAK

- **Pengakuan Kas Keluar**: Transaksi Kas Keluar mencatat akun Kas/Bank pada posisi **Kredit** (mengurangi aset) dan akun Beban/Utang pada posisi **Debit**.
- **Asas Zero Discrepancy**: Sesuai prinsip *double-entry bookkeeping*, `Total Debit == Total Kredit` sebelum tombol submit diaktifkan.

---

## 3. Mekanisme Jejak Audit (Audit Trail & Immutability)

- Transaksi berstatus `'POSTED'` dikunci melalui fungsi trigger database PostgreSQL agar tidak dapat diubah (`UPDATE`) atau dihapus (`DELETE`).
- Penerapan metadata `created_by`, `created_at`, dan `hash_checksum` untuk menjaga integritas data akuntansi.