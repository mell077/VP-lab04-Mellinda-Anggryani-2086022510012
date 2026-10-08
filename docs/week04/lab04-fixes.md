# Lab 04 – Fix log

| Widget | Error / gejala | Aturan yang dilanggar | Perbaikan |
|---|---|---|---|
| StoreHeader | Row overflow ke kanan di 320 dp | Row memberi Column dan teks rating lebar tanpa batas | Column dibungkus `Expanded`, teks `maxLines: 1` + ellipsis, rating dipindah ke bawah jam buka |
| CategoryBar | Row chip overflow ke kanan | Row memberi chip lebih banyak dari lebar layar | Dibungkus `SingleChildScrollView` horizontal |
| PromoStrip / PromoCard | Dua kartu lebar 200 overflow di 320 dan 430 dp, dan `promos[1]` crash kalau promo kurang dari 2 | Anak berlebar tetap dalam Row tidak peduli lebar parent | `ListView.separated` horizontal, teks `maxLines` + ellipsis, strip disembunyikan kalau tidak ada promo |
| MenuTile | Row overflow ke kanan saat nama 200 karakter | Row memberi Column nama lebar tanpa batas (`Spacer` tidak membatasi) | `Expanded` pada Column, `maxLines: 2` + ellipsis |
| MenuScreen (body) | Overflow di bawah saat landscape dan keyboard terbuka | Column memberi anaknya tinggi tak terbatas, padahal layar terbatas | Satu `CustomScrollView` dengan sliver |
| MenuScreen (list) | List panjang dibangun sekaligus akan lambat | List dengan panjang tak diketahui harus lazy | `SliverList.builder` |
| MenuScreen (tablet) | Layout dipilih dengan `MediaQuery`, sel `GridView.count(4)` membuat kartu overflow | Layout harus mengikuti lebar yang diberikan parent | `LayoutBuilder` (>= 600 dp = grid), `SliverGridDelegateWithMaxCrossAxisExtent` + `SliverGrid.builder` |
| MenuCard | Gambar tinggi tetap 110 dp + teks overflow di bawah sel grid | Anak berukuran tetap di sel yang tingginya ditentukan parent | Area gambar dibungkus `Expanded`, teks `maxLines` + ellipsis |
| MenuScreen (kosong) | Data nol: layar kosong atau RangeError `promos[0]` | Kode mengira data selalu ada | `EmptyState` (key `empty-state`) berisi ikon, pesan, dan tombol reset |
| CartBar | Row overflow di 320 dp, tinggi tetap 72, tertutup gesture bar | Tombol lebar tetap 160 + teks panjang dalam Row, dan mengabaikan safe area | Teks dalam `Expanded` Column dengan ellipsis, tombol selebar isinya, `SafeArea` di dalam bar |