# StrukturData-Q1-2501010122-DewaGedeReihanWaiswana-D

# 1. Karakteristik Memori dan Akses Data

Array memiliki kemampuan akses elemen yang sangat cepat karena data disimpan secara berurutan (kontinu) di dalam memori. Setiap elemen pada array memiliki indeks yang nilainya tetap dan tersusun secara teratur. Ketika program ingin mengambil suatu elemen, komputer cukup menghitung alamat memorinya menggunakan rumus:

Alamat Elemen = Base Address + (Index × Ukuran Data)

Karena alamat memori dapat dihitung secara langsung, proses pengambilan data tidak perlu melewati elemen lain terlebih dahulu. Oleh sebab itu, kompleksitas waktu akses pada array adalah O(1) atau waktu konstan.

Sebagai contoh, jika ingin mengambil data pada indeks ke-50, sistem dapat langsung menuju alamat memori elemen tersebut tanpa memeriksa elemen indeks 0 sampai 49.

Berbeda dengan Array, Singly Linked List menyimpan data secara tidak berurutan (non-kontinu) di memori. Setiap node pada linked list terdiri dari:

* Data
* Pointer atau alamat menuju node berikutnya

Karena node-node tersebar di berbagai lokasi memori, komputer tidak dapat langsung menghitung lokasi elemen tertentu berdasarkan indeks. Untuk menemukan data pada posisi tertentu, sistem harus melakukan traversal, yaitu menelusuri node satu per satu mulai dari head hingga posisi yang dicari.

Misalnya ingin mengambil data pada node ke-50, maka sistem harus melewati node ke-1, ke-2, dan seterusnya sampai node ke-50 ditemukan. Proses ini menyebabkan kompleksitas waktu akses menjadi O(n) atau linear.

Secara teori:

* Array unggul dalam akses data karena memori kontinu memungkinkan random access.
* Linked List lebih fleksibel dalam pengelolaan ukuran data tetapi memiliki akses yang lebih lambat karena harus traversal.

---

# 2. Analisis Efisiensi Operasi Manipulasi

Linked List lebih diunggulkan dibandingkan Array ketika program sering melakukan operasi insertion (penyisipan) dan deletion (penghapusan) data, terutama di bagian awal atau tengah struktur data.

Pada Array, setiap elemen memiliki posisi indeks yang harus tetap berurutan. Jika terjadi insertion di tengah array, maka seluruh elemen setelah posisi tersebut harus digeser satu langkah ke kanan agar terdapat ruang kosong untuk data baru.

Contoh:

```text
[10, 20, 30, 40]

Insert 25 di tengah:

[10, 20, 25, 30, 40]
```

Agar angka 25 dapat masuk, maka elemen 30 dan 40 harus dipindahkan terlebih dahulu. Hal ini membutuhkan waktu O(n).

Begitu juga pada operasi deletion. Jika suatu elemen dihapus, maka elemen setelahnya harus digeser ke kiri agar indeks tetap tersusun rapi.

Sebaliknya, pada Linked List proses insertion dan deletion jauh lebih efisien karena tidak perlu menggeser data lain. Operasi cukup dilakukan dengan mengubah pointer antar node.

Contoh insertion:

```text
A -> B -> C

Insert X setelah B:

A -> B -> X -> C
```

Sistem hanya perlu:

* Mengubah pointer B agar menunjuk ke X
* Mengubah pointer X agar menunjuk ke C

Tidak ada proses pemindahan data seperti pada Array.

Jika posisi node sudah diketahui, maka insertion dan deletion pada Linked List dapat dilakukan dalam kompleksitas O(1).

Namun, jika posisi node belum diketahui, maka traversal tetap diperlukan sehingga total kompleksitas bisa menjadi O(n).

Secara teoritis:

* Array lebih efisien untuk akses data.
* Linked List lebih efisien untuk manipulasi data dinamis.

Karena itu, Linked List cocok digunakan pada:

* Data yang sering berubah ukuran
* Sistem antrian
* Playlist musik
* Editor teks
* Manajemen memori dinamis

---

# 3. Konsep Doubly Linked List

Doubly Linked List adalah pengembangan dari Singly Linked List di mana setiap node memiliki dua pointer.

Struktur node pada Doubly Linked List terdiri dari:

1. Data
2. Pointer ke node berikutnya (next)
3. Pointer ke node sebelumnya (prev)

Ilustrasi:

```text
NULL <- A <-> B <-> C -> NULL
```

Berbeda dengan Singly Linked List yang hanya dapat bergerak satu arah, Doubly Linked List memungkinkan traversal ke dua arah:

* Dari depan ke belakang
* Dari belakang ke depan

Keuntungan utama Doubly Linked List:

1. Traversal lebih fleksibel

   * Pengguna dapat bergerak maju dan mundur.
   * Sangat cocok untuk fitur undo-redo atau navigasi browser.

2. Penghapusan node lebih mudah

   * Sistem dapat langsung mengetahui node sebelumnya tanpa traversal ulang.

3. Insertion lebih efisien pada posisi tertentu

   * Karena hubungan antar node dua arah.

Namun, terdapat dampak terhadap penggunaan memori:

* Setiap node membutuhkan dua pointer.
* Memori yang digunakan lebih besar dibandingkan Singly Linked List.

Perbandingan:

| Struktur           | Pointer per Node |
| ------------------ | ---------------- |
| Singly Linked List | 1                |
| Doubly Linked List | 2                |

Selain penggunaan memori yang lebih besar, pengelolaan pointer juga menjadi lebih kompleks karena setiap perubahan node harus memperhatikan dua arah relasi.

Contoh penggunaan Doubly Linked List:

* Browser history
* Music playlist
* Undo/redo pada text editor
* Navigasi galeri foto

---

# 4. Mekanisme Circular Linked List

Circular Linked List adalah Linked List yang node terakhirnya tidak menunjuk ke NULL, melainkan kembali menunjuk ke node pertama sehingga membentuk lingkaran.

Ilustrasi:

```text
A -> B -> C
^         |
|_________|
```

Perbedaan utama dengan Linked List biasa:

| Linked List Biasa           | Circular Linked List                |
| --------------------------- | ----------------------------------- |
| Node terakhir menunjuk NULL | Node terakhir menunjuk node pertama |
| Traversal berhenti di akhir | Traversal dapat terus berulang      |
| Tidak membentuk siklus      | Membentuk siklus melingkar          |

Karena strukturnya melingkar, Circular Linked List sangat efektif digunakan pada sistem yang membutuhkan proses berulang tanpa henti.

Keuntungan Circular Linked List:

1. Tidak perlu kembali ke awal secara manual.
2. Sangat efisien untuk proses looping.
3. Cocok untuk sistem penjadwalan.

Salah satu contoh penggunaan paling umum adalah:

## Round Robin Scheduling

Pada sistem operasi, CPU memberikan waktu proses secara bergantian kepada setiap program.

Contoh:

```text
P1 -> P2 -> P3 -> kembali ke P1
```

Setelah proses terakhir selesai, sistem langsung kembali ke proses pertama tanpa harus membuat traversal ulang dari awal.

Contoh penggunaan lain:

* Playlist musik otomatis
* Sistem multiplayer turn-based
* Rotasi antrian printer
* Game berbasis giliran

Secara teori, Circular Linked List meningkatkan efisiensi traversal siklus karena hubungan antar node membentuk loop kontinu.

---

# 5. Array Dinamis di Python

Python list sebenarnya diimplementasikan menggunakan Dynamic Array.

Berbeda dengan array statis pada bahasa pemrograman tertentu yang ukurannya tetap, Dynamic Array dapat bertambah kapasitas secara otomatis saat data baru ditambahkan.

Ketika operasi append dilakukan, Python akan:

1. Memeriksa apakah kapasitas memori masih tersedia.

2. Jika masih ada ruang:

   * Data langsung ditambahkan.
   * Operasi berlangsung sangat cepat.

3. Jika kapasitas penuh:

   * Python membuat blok memori baru dengan ukuran lebih besar.
   * Seluruh elemen lama disalin ke memori baru.
   * Data baru ditambahkan.
   * Memori lama dilepaskan.

Contoh proses:

```text
Kapasitas awal: 4
[1,2,3,4]

Append 5:
- Buat array baru kapasitas lebih besar
- Copy seluruh data lama
- Tambahkan 5
```

Proses resize ini membutuhkan waktu O(n) karena seluruh elemen harus disalin ulang.

Namun, resize tidak terjadi setiap append. Python biasanya menambah kapasitas lebih besar dari kebutuhan saat ini agar resize tidak terlalu sering dilakukan.

Karena itu:

* Sebagian besar append berlangsung dalam O(1)
* Resize sesekali berlangsung O(n)

Secara keseluruhan, append pada Dynamic Array dianggap memiliki kompleksitas amortized O(1).

Keuntungan Dynamic Array:

* Ukuran fleksibel
* Mudah digunakan
* Akses data tetap cepat seperti array biasa

Kekurangannya:

* Resize membutuhkan penyalinan data
* Kadang menggunakan memori lebih besar dari jumlah data sebenarnya karena adanya kapasitas cadangan (overallocation)
