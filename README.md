# Pertemuan 04 Seleksi Multi-Kondisi dan Validasi Input

Nama: Siti Maulida Putri Irawan
NIM: 2225250107
Kelas: 3A

## Tujuan

Membuat program yang dapat menerima dan memvalidasi nilai ujian, nilai tugas, dan persentase kehadiran. Program menggunakan percabangan if-elif-else untuk menentukan predikat nilai dan status kelulusan berdasarkan nilai akhir serta syarat kehadiran.

## Cara Menjalankan

Program dapat dijalankan melalui Terminal VS Code dengan perintah:

```bash
python praktik/validasi_klasifikasi_nilai.py
```

## Tabel Keputusan

| Cabang | Kategori | Syarat | Contoh masukan |
| --- | --- | --- | --- |
| except ValueError | Penolakan tipe | Ada masukan yang bukan angka | 80, 80, abc |
| if not (0 <= ujian <= 100) | Penolakan nilai ujian | ujian < 0 atau ujian > 100 | 105, 80, 90 |
| elif not (0 <= tugas <= 100) | Penolakan nilai tugas | tugas < 0 atau tugas > 100 | 80, -5, 90 |
| elif not (0 <= hadir <= 100) | Penolakan kehadiran | hadir <0 atau hadir > 100 | 80, 80, 105 |
| if hadir < 80 | Tidak memenuhi syarat kehadiran | Kehadiran < 80 | 90, 90, 75 |
| if akhir >=85 | Predikat A | Nilai akhir minimal 85 dan kehadiran memenuhi syarat | 90, 80, 95 |
| elif akhir >= 70 | Predikat B | 70 ≤ nilai akhir < 85 dan kehadiran ≥ 80 | 75, 70, 85 | 
| elif akhir >=60 | Predikat C | 60 ≤ nilai akhir < 70 dan kehadiran ≥ 80 | 60, 60, 80 |
| elif akhir >= 50 | Predikat D | 50 ≤ nilai akhir < 60 dan kehadiran ≥ 80 | 55, 50, 90 |
| else predikat | Predikat E | Nilai akhir < 50 dan kehadiran ≥ 80 | 40, 30, 100 |
| if predikat in ("A", "B", "C") | Lulus | Predikat = A, B, atau C | 90, 80, 95 |
| else | Belum lulus | Predikat = D atau E | 55, 50, 90 |

## Hasil Pengujian

| Test Case | Masukan | Keluaran yang diharapkan | Keluaran aktual | Status |
| --- | --- | --- | --- | --- |
| 1 | 90, 80, 95 | Nilai akhir 86.00, Predikat A, Lulus | Nilai akhir 86.00, Predikat A, Lulus | Berhasil |
| 2 | 75, 70, 85 | Nilai akhir 73.00, Predikat B, Lulus | Nilai akhir 73.00, Predikat B, Lulus | Berhasil |
| 3 | 60, 60, 80 | Nilai akhir 60.00, Predikat C, Lulus | Nilai akhir 60.00, Predikat C, Lulus | Berhasil |
| 4 | 55, 50, 90 | Nilai akhir 53.00, Predikat D, Belum lulus | Nilai akhir 53.00, Predikat D, Belum lulus | Berhasil |
| 5 | 40, 30, 100 | Nilai akhir 36.00, Predikat E, Belum lulus | Nilai akhir 36.00, Predikat E, Belum lulus | Berhasil |
| 6 | 90, 90, 75 | Nilai akhir 90.00, tidak memenuhi syarat kehadiran | Nilai akhir 90.00, Tidak memenuhi syarat kehadiran | Berhasil |
| 7 | 105, 80, 90 | Penolakan rentang nilai ujian | Masukan ditolak: nilai ujian di luar rentang 0 sampai 100 | Berhasil |
| 8 | 80, -5, 90 | Penolakan rentang nilai tugas | Masukan ditolak: nilai tugas di luar rentang 0 sampai 100 | Berhasil |
| 9 | 80, 80, abc | Penolakan tipe | Masukan ditolak: seluruh data harus berupa angka | Berhasil |

## refleksi 

Masukan tidak valid yang semula dapat terlewat adalah nilai ujian 105. Nilai tersebut tidak sesuai dengan rentang nilai yang ditentukan, yaitu 0 sampai 100. Cara menanganinya adalah dengan memeriksa nilai ujian menggunakan kondisi 0 ≤ nilai ujian ≤ 100. Jika nilai ujian kurang dari 0 atau lebih dari 100, program menampilkan pesan bahwa nilai ujian berada di luar rentang dan tidak melanjutkan perhitungan. 