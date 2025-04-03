# 📚 API Data Sekolah Seluruh Indonesia
API sekolah ini berisi informasi lengkap tentang sekolah-sekolah di Indonesia. API ini mencakup hampir semua jenjang pendidikan yang ada di Indonesia, mulai dari TK, SD, SMP, SMA, MA, sampai pendidikan non-formal.

# Dokumentasi
🌐 __URL API :__ `https://sekolah.devapi.id/sekolah`

📤 __HTTP Method :__ `GET`

## 📝 __Parameter API__
|Nama|Tipe Data|Deskripsi|
|-|-|-|
|nama|string|	Mencari sekolah berdasarkan nama (case-insensitive) (Min: __3 karakter__). Contoh: `SMA Negeri 1 Purwadadi` (exact match), `bina insani` (substring)|
|bentuk_pendidikan|string|Filter berdasarkan jenjang pendidikan. Contoh: `SMP`, `SD`, `MA`, `MTS`, `TK`, dll|
|npsn|string|Mencari sekolah berdasarkan Nomor Pokok Sekolah Nasional (NPSN). Contoh: `69901175`|
|negara|string|	Filter sekolah berdasarkan negara (default: Indonesia). Contoh: `Indonesia`, `Malaysia`, dll (sekolah yang terdaftar di indonesia)|
|akreditasi|string|Filter berdasarkan nilai akreditasi. Contoh: `A`, `B`, `C`, dll|
|kode_wilayah|integer|Mencari sekolah berdasarkan kode wilayah Kemendagri. Contoh: 3171 (Kota Jakarta Pusat), 350718 (Kecamatan Pakis, Kota Malang)  __[1]__|
|page|integer|Nomor halaman hasil pencarian. (Default: __10__)|
|limit|integer|Jumlah maksimal data yang ditampilkan per halaman. (Default: __10__, Max: __100__)|

### 📌 Catatan:
- Untuk referensi kode wilayah bisa dilihat di website [kodewilayah.id](https://kodewilayah.id). __[1]__
- Parameter bisa digabungkan untuk mempersempit pencarian.

## 💡 __Contoh Respons__
```
{
    "success": true,
    "message": "Get Data Success",
    "developer": "sayaturu (https://github.com/ikhsan-rfl/)",
    "data": [
        {
            "npsn": "P9984383",
            "nama": "PKBM MADANI",
            "bentukPendidikan": "PKBM",
            "jalurPendidikan": "NON FORMAL",
            "jenjangPendidikan": "PENDIDIKAN KEMASYARAKATAN",
            "kementerianPembina": "KEMENTERIAN PENDIDIKAN, KEBUDAYAAN, RISET DAN TEKNOLOGI",
            "statusSatuanPendidikan": "SWASTA",
            "akreditasi": "",
            "jenisPendidikan": "-",
            "dokumen_perizinan": {
                "sk_pendirian_sekolah": {
                    "nomor": "05",
                    "tanggal": "2006-10-23T00:00:00Z"
                },
                "sk_izin_operasional": {
                    "nomor": "890/150/I/2019",
                    "tanggal": "2019-01-15T00:00:00Z"
                }
            },
            "yayasan": {
                "nama": "",
                "npyp": ""
            },
            "alamat": {
                "jalan": "GALUNG",
                "rt": 0,
                "rw": 0,
                "nama_dusun": "DAYANGINNA",
                "nama_desa": "GALUNG",
                "nama_kecamatan": "TAPALANG",
                "nama_kabupaten": "KAB. MAMUJU",
                "nama_provinsi": "SULAWESI BARAT",
                "nama_negara": "INDONESIA",
                "kode_provinsi": 76,
                "kode_kabupaten": 2,
                "kode_kecamatan": 2,
                "kode_wilayah": 760202
            },
            "sarana_prasarana": {
                "luas_tanah_milik": "3 m2",
                "sumber_listrik": "MENUMPANG",
                "akses_internet": "TIDAK ADA"
            },
            "kontak": {
                "nomor_fax": "",
                "nomor_telepon": "085255986583",
                "email": "pkbmmadani11@gmail.com",
                "website": ""
            },
            "lokasi": {
                "koordinat": [
                    -2.876927,
                    118.951515
                ],
                "lintang": -2.876927,
                "bujur": 118.951515
            }
        }
    ],
    "limit": 1,
    "page": 1,
    "last_updated": "2025-02-25 09:38:38"
}
```

## 🚀 Contoh Penggunaan
### Pencarian Dasar
#### • Mencari sekolah bedasarkan nama
```
https://sekolah.devapi.id/sekolah?nama=madani
```
#### • Mencari sekolah bedasarkan nama dan bentuk pendidikan
```
https://sekolah.devapi.id/sekolah?bentuk_pendidikan=SMA
```
#### • Mencari sekolah bedasarkan NPSN
```
https://sekolah.devapi.id/sekolah?npsn=40604924
```
#### • Mencari sekolah bedasarkan akreditasi
```
https://sekolah.devapi.id/sekolah?akreditasi=A
```
#### • Mencari sekolah bedasarkan kode wilayah
```
https://sekolah.devapi.id/sekolah?kode_wilayah=327105
```
|Kode|Deskripsi|
|-|-|
|32|Provinsi Jawa Barat|
|71|Kota Bogor|
|05|Kecamatan Bogor Utara|
### Pencarian Lanjutan
#### • Nama + Limit
```
https://sekolah.devapi.id/sekolah?nama=hidayah&limit=20
```
#### • Nama + Akreditasi
```
https://sekolah.devapi.id/sekolah?nama=insan&akreditasi=A
```
#### • Nama + Bentuk Pendidikan + Kode Wilayah
```
https://sekolah.devapi.id/sekolah?nama=citra&bentuk_pendidikan=SMP&kode_wilayah=3174
```
|Parameter|Value|Deskripsi|
|-|-|-|
|nama|citra|Filter berdasarkan nama sekolah (case-insensitive, partial match)|
|bentuk_pendidikan|SMP|Jenis pendidikan (contoh: 'SMP' untuk Sekolah Menengah Pertama)|
|kode_wilayah|3174|Kode wilayah kemendagri (contoh: '3174' untuk Kota Cirebon, Provinsi Jawa Barat)|

## ℹ️ Informasi Tambahan
- API memiliki rate limit global yaitu 300 request / 1 menit.
- API memiliki sistem cache, jika request HIT maka tidak mengurangi sisa requests.

## Masalah atau Saran?
Jika ada masalah pada API ini atau memiliki saran, silakan:
- Kirim email ke ikhsan@devapi.id.
- Buat issue di repository ini.
