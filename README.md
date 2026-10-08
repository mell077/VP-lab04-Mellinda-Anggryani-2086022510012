Jawaban Check Yourself (Lab 04)

**1. Text di dalam Row overflow. Bagian mana dari "constraints go down, sizes go up, parent sets position" yang dilanggar, dan oleh widget apa?**

Yang dilanggar adalah "constraints go down", oleh widget Row: ia tidak memberi batas lebar yang jelas kepada Text. Analogi: Row itu bangku angkot yang panjangnya terbatas, Text penumpang yang membawa barang sebesar apa pun, dan tidak ada kernet yang bilang "jatah Anda cuma segini". Akhirnya barangnya menonjol keluar pintu. Expanded berperan sebagai kernet yang memberi jatah tempat.

**2. Mengapa menambah width: 150 pada teks adalah perbaikan yang salah, walaupun garis kuning-hitam hilang?**

Angka 150 hanya cocok untuk satu ukuran layar atau satu panjang teks, jadi masalahnya cuma pindah ke layar lain. Analogi: menjahit semua baju seukuran 150. Pas untuk satu orang, tapi sesak untuk orang lain. Perbaikan yang benar adalah mengatur hubungan parent dan child, bukan menulis angka baru.

**3. Kamu memperbaiki overflow landscape dengan SingleChildScrollView dan shrinkWrap: true pada list. Tes mana yang gagal, dan mengapa penting ketika data dari API?**

Yang gagal adalah tes Long list (500 item, dibangun lazy), karena shrinkWrap: true memaksa semua item dibangun sekaligus. Analogi: restoran yang memasak 500 piring sebelum tamu memesan, padahal seharusnya memasak sesuai pesanan. Kalau data berasal dari API, jumlahnya bisa ribuan dan di luar kendali kita, sehingga aplikasi menjadi lambat dan boros memori.

**4. Mengapa layout tablet memakai LayoutBuilder, bukan MediaQuery.sizeOf(context) ?**

LayoutBuilder memberi tahu lebar yang benar-benar diberikan parent kepada widget itu, sedangkan MediaQuery hanya memberi ukuran seluruh layar. Analogi: menanyakan "luas ruangan yang dipinjamkan kepadaku" lebih tepat daripada "luas seluruh gedung". Kalau widget ditaruh di panel sempit atau di bingkai harness, MediaQuery bisa memilih layout yang salah.

**5. Crash data kosong bukan error layout. Mengapa tetap termasuk lab layout?**

Layout bergantung pada isi, dan "tidak ada isi" adalah salah satu kondisinya. Analogi: toko yang stoknya habis seharusnya memasang papan "Stok habis, coba lagi", bukan etalase kosong atau penjaga yang pingsan. Kode yang mengira data selalu ada (seperti promos[0]) crash saat datanya nol, jadi empty state adalah bagian dari desain layout.