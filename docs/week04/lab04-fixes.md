Lab 04 

Tiap baris berisi: widget yang bermasalah, gejalanya, aturan constraint yang dilanggar, dan cara aku memperbaikinya.

**StoreHeader**: Row meluap ke kanan di layar 320 dp. Penyebabnya Row memberi lebar tanpa batas ke Column dan teks rating. Kuperbaiki dengan membungkus Column pakai Expanded, memberi teks maxLines: 1 dan ellipsis, lalu memindah rating ke bawah jam buka.

**CategoryBar**: deretan chip meluap ke kanan. Row memberi ruang lebih banyak daripada lebar layar yang ada. Kuperbaiki dengan membungkusnya pakai `SingleChildScrollVie horizontal.

**PromoStrip dan PromoCard**: dua kartu lebar 200 meluap di 320 dan 430 dp, dan promosi error kalau promo kurang dari dua. Penyebabnya kartu berlebar tetap di dalam Row tidak peduli lebar parent-nya. Kuganti dengan ListView.separated horizontal, teks diberi maxLines dan ellipsis, dan strip disembunyikan kalau tidak ada promo.

**MenuTile**: Row meluap ke kanan saat nama menu 200 karakter. Row memberi lebar tanpa batas ke Column nama (Spacer tidak membatasi apa-apa). Kuperbaiki dengan Expanded pada Column, maxLines: 2, dan ellipsis.

**MenuScreen (body)**: meluap ke bawah saat landscape dan saat keyboard terbuka. Column memberi tinggi tak terbatas ke anak-anaknya, padahal tinggi layar terbatas. Kuganti dengan satu CustomScrollView berisi sliver supaya seluruh halaman bisa di-scroll.

**MenuScreen (list)**: list panjang dibangun sekaligus, jadi berat kalau datanya ratusan. List yang panjangnya tidak diketahui harus dibangun lazy. Kupakai SliverList.builder.

**MenuScreen (tablet)**: layout dipilih pakai MediaQuery dan sel GridView.count(4) membuat kartu meluap. Layout seharusnya mengikuti lebar yang diberikan parent. Kuganti dengan LayoutBuilder (600 dp ke atas jadi grid), SliverGridDelegateWithMaxCrossAxisExtent, dan SliverGrid.builder.

**MenuCard**: gambar setinggi tetap 110 dp ditambah teks meluap ke bawah di dalam sel grid. Tinggi sel ditentukan parent, jadi isinya tidak boleh memaksa ukuran sendiri. Area gambar kubungkus Expanded dan teks diberi maxLines dan ellipsis.

**MenuScreen (data kosong)**: layar kosong atau error promos[0] saat datanya nol. Kodenya mengira data pasti ada. Kutambahkan widget EmptyState (key empty-state) berisi ikon, pesan, dan tombol reset filter.

**CartBar**: Row meluap di 320 dp, tingginya dipatok 72, dan tombolnya tertutup gesture bar. Penyebabnya tombol berlebar tetap 160 dan teks panjang berada dalam satu Row, serta tidak memperhitungkan safe area. Teks kupindah ke Column dalam Expanded dengan ellipsis, tombol dibiarkan selebar isinya, dan isi bar dibungkus SafeArea.