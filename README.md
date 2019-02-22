# SoalShift_modul1_A06
1. Anda diminta tolong oleh teman anda untuk mengembalikan filenya yang telah
   dienkripsi oleh seseorang menggunakan bash script, file yang dimaksud adalah
   nature.zip. Karena terlalu mudah kalian memberikan syarat akan membuka seluruh
   file tersebut jika pukul 14:14 pada tanggal 14 Februari atau hari tersebut adalah hari
   jumat pada bulan Februari.
   Hint: Base64, Hexdump
   
   Jawaban :
  * Langkah-Langkah :
  * a) unzip file nature.zip
  * b) lalu buatlah bash script dengan menggunakan fungsi perulangan yang isinya :
        i)  decrypt menggunakan base64 -d
        ii) reverse hexdump menggunakan xxd -r agar menjadi bentuk file
  * d) lalu buatlah cronjob dengan mengetikkan crontab -e dan atur waktu menjadi :
  * 14 14 14 2 * bash /home/hafidzasqalany28/nature/soal1.sh
  *  0  0  * 2 5 bash /home/hafidzasqalany28/nature/soal1.sh
2. Anda merupakan pegawai magang pada sebuah perusahaan retail, dan anda diminta
   untuk memberikan laporan berdasarkan file WA_Sales_Products_2012-14.csv.
   Laporan yang diminta berupa:
  * a. Tentukan negara dengan penjualan(quantity) terbanyak pada tahun 2012.
  * b. Tentukan tiga product line yang memberikan penjualan(quantity) terbanyak pada soal poin a.
  * c. Tentukan tiga product yang memberikan penjualan(quantity) 
           terbanyak berdasarkan tiga product line yang didapatkan pada soal
           poin b.
           
   jawaban :
  * Langkah-Langkah :
  * a) buatlah script awk untuk menyortir data agar hanya mendapatkan tabel negara dan quantity pada tahun 2012.
  * b) total semua quantity yang ada pada setiap negara.
  * c) tampilkan negara yang mempunyai nilai quantity terbanyak pada tahun 2012 dengan menggunakan perulangan.
  * d) buatlah script awk untuk menyortir data agar menampilkan tabel product line dan quantity pada negara yang di dapatkan pada             poin b.
  * e) total semua quantity pada product line.
  * f) tampilkan 3 product line yang mempunyai quantity terbanyak dengan menggunakan perulangan.
  * g) buatlah script awk untuk menyortir data agar menampilkan tabel product dan quantity pada product line yang didapatkan pada poin f.
  * h) total semua quantity pada product.
  * i) tampilkan 3 product yang mempunyai quantity terbanyak dengan menggunakan perulangan.

3. Buatlah sebuah script bash yang dapat menghasilkan password secara acak
   sebanyak 12 karakter yang terdapat huruf besar, huruf kecil, dan angka. Password
   acak tersebut disimpan pada file berekstensi .txt dengan ketentuan pemberian nama
   sebagai berikut:

   a. Jika tidak ditemukan file password1.txt maka password acak tersebut
   disimpan pada file bernama password1.txt
   b. Jika file password1.txt sudah ada maka password acak baru akan
   disimpan pada file bernama password2.txt dan begitu seterusnya.
   c. Urutan nama file tidak boleh ada yang terlewatkan meski filenya
   dihapus.
   d. Password yang dihasilkan tidak boleh sama.
   
   jawaban :
   * Langkah-Langkah :
   a) Masukkan integer untuk mengetahui bilangan awal
   b) Masukkan fungsi while test -e untuk mengecheck apakah telah terdapat file dengan nama yang sama
   c) Jika tidak ada maka file berinisial Password.txt akan terbuat, jika ada maka akan terbuat file baru bernama Password1.txt         dan seterusnya
   d) Masukkan integer untuk setiap file bernama fname kemudian touch untuk membuat file kosong
   e) Terakhir masukkan fungsi head /dev/urandom | tr -dc A-Za-z0-9 | head -c 12 untuk membuat string berisi 12 karakter acak berhuruf kapital dan kecil serta angka untuk menjadi Password kemudian save di file fname kosong yang telah terbuat
   
4. Lakukan backup file syslog setiap jam dengan format nama file “jam:menit tanggal-
   bulan-tahun”. Isi dari file backup terenkripsi dengan konversi huruf (string
   manipulation) yang disesuaikan dengan jam dilakukannya backup misalkan sebagai
   berikut:
  * a. Huruf b adalah alfabet kedua, sedangkan saat ini waktu menunjukkan
         pukul 12, sehingga huruf b diganti dengan huruf alfabet yang memiliki
         urutan ke 12+2 = 14.
  * b. Hasilnya huruf b menjadi huruf n karena huruf n adalah huruf ke
         empat belas, dan seterusnya.
  * c. setelah huruf z akan kembali ke huruf a
  * d. Backup file syslog setiap jam.
  * e. dan buatkan juga bash script untuk dekripsinya.
      jawaban :
  * Langkah-Langkah :
  * a) deklarasikan variabel date agar menyimpan data untuk memiliki format nama file “jam:menit tanggal-
         bulan-tahun”.
  * b) deklarasikan variabel agar dapat menyimpan data jam yang akan di print.
  * c) melihat semua proses syslog yang telah berjalan 
  * d) mengubah data syslog menjadi hexdump dan sortir menggunakan awk
  * e) membuat fungsi agar isi dari file poin a mempunyai ketentuan sesuai poin soal a-c.
  * f) membuat file crontab :
  * 0 * * * * bash /home/hafidzasqalany28/soal4.sh

   5. Buatlah sebuah script bash untuk menyimpan record dalam syslog yang memenuhi
   kriteria berikut:

   a. Tidak mengandung string “sudo”, tetapi mengandung string “cron”,
   serta buatlah pencarian stringnya tidak bersifat case sensitive,
   sehingga huruf kapital atau tidak, tidak menjadi masalah.
   b. Jumlah field (number of field) pada baris tersebut berjumlah kurang
   dari 13.
   c. Masukkan record tadi ke dalam file logs yang berada pada direktori
   /home/[user]/modul1.
   d. Jalankan script tadi setiap 6 menit dari menit ke 2 hingga 30, contoh
   13:02, 13:08, 13:14, dst.
   
   * Langkah-Langkah :
  * a) Masukkan fungsi cat untuk mengetahui data di dalam directory var/log/syslog kemudian pipe hasilnya
  * b) Masukkan fungsi awk yang bertujuan menyaring data tersebut sehingga hanya string yang memiliki baris kurang dari 13 saja yang ditampilkan kemudian pipe data tersebut
  * c) Masukkan fungsi grep -i yang bertujuan untuk menampilkan string yang di dalamnya terdapat kata cron serta bersifat incase-sensitive
  * d) Masukkan fungsi grep -v yang bertujuan untuk mencegah menampilkan string yang di dalamnya terdapat kata sudo
  * e) Kemudian save file ke dalam directory /home/[user]/modul1
  * f) Terakhir buatlah crontab 2-30/6 * * * * /home/[user]/[script] untuk membuat schedule bash script akan berjalan setiap 6 menit diantara menit ke 2 hingga menit ke 30
