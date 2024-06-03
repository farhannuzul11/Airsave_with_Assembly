# Sistem Pemantauan Kualitas Udara dengan Peringatan Otomatis.
Proyek Akhir Mata Kuliah Sistem Siber Fisik 2024 Kelompok 8

Kelompok 8:
- Farhan Nuzul Noufendri (2206024442)
- Ivander Andreas Wijaya (2206031896)
- Nicholas Samosir (2206059396)
- Tanto Efrem Lesmana (2206031391)

## Dokumentasi

![Project Proteus](https://github.com/farhannuzul11/Airsave_with_Assembly/assets/112792115/751c9cd4-9881-4327-b167-1a5f061e7da5)


## Daftar Isi
- [Pengantar dan Solusi dari Permasalahan](#pengantar-dan-solusi-dari-permasalahan)
- [Desain dan Implementasi Perangkat Keras](#desain-dan-implementasi-perangkat-keras)
- [Detail Implementasi Perangkat Lunak](#detail-implementasi-perangkat-lunak)
- [Hasil Pengujian dan Evaluasi Kinerja](#hasil-pengujian-dan-evaluasi-kinerja)
- [Kesimpulan](#kesimpulan)

## Pengantar dan Solusi dari Permasalahan
### Pengantar
Kualitas udara yang buruk merupakan masalah serius yang berdampak langsung pada kesehatan masyarakat, menyebabkan gangguan pernapasan dan penyakit kardiovaskular akibat peningkatan polutan seperti karbon monoksida (CO). Sistem pemantauan kualitas udara konvensional seringkali terbatas dalam mobilitas, biaya, dan kecepatan respon, tidak mampu memberikan data real-time dan membutuhkan biaya tinggi untuk instalasi serta pemeliharaan. Oleh karena itu, diperlukan sistem pemantauan kualitas udara yang efektif, efisien, dan terjangkau untuk mengurangi risiko kesehatan dari udara tercemar.
### Solusi
Untuk mengatasi masalah kualitas udara, sistem AIRSAFE menggunakan mikrokontroler Arduino atmega328p dan sensor gas MQ-2 sebagai solusi efektif pemantauan real-time. Sistem ini terdiri dari sebuah Arduino dimana Arduino mengolah data dari sensor yang mendeteksi gas berbahaya seperti karbon monoksida (CO) serta memberikan peringatan dalam bentuk buzzer dan LED.

Data kualitas udara ditampilkan pada layar LCD, serta tiga LED (hijau, kuning, merah) dan alarm sebagai indikator visual dan auditori: hijau untuk kualitas baik, kuning untuk sedang, dan merah untuk buruk. Ketika kadar CO melebihi batas aman, LED merah menyala dan alarm berbunyi, memungkinkan pengguna segera bertindak. Dengan respons cepat terhadap perubahan kualitas udara dan kontrol pemrograman menggunakan bahasa assembly, teknologi ini diharapkan dapat meningkatkan efektivitas pemantauan kualitas udara dan pemahaman teknologi Arduino dan assembly.

## Desain dan Implementasi Perangkat Keras
### Desain Perangkat Keras
Adapun peralatan yang digunakan adalah sebagai berikut:
- Sensor Asap MQ-2 (1)
- Arduino UNO ATmega328p (1)
- Modul I2C (1)
- LCD (1)
- LED (3)
- Resistor 10k (3)
- Kabel Jumper
- Breadboard (1)

### Implementasi Perangkat Keras

Desain rangkaian kami dibuat dengan menggunakan aplikasi Proteus. Rangkaian dibuat sedemikian rupa dengan menggunakan sebuah arduino dengan mengimplementasikan modul I2C untuk menjalankan penampilan hasil pembacaan dan pendeteksian sensor terpisah dari peringatan LED dan buzzer. Buzzer dirangkai dengan konfigurasi sedemikian rupa agar dapat menyala. Setiap LED dilengkapi oleh resistor untuk membatasi tegangan yang lewat pada masing-masing LED.

Rangkaian asli dibuat langsung ke dalam arduino asli dengan meng-flash kode .S ke arduino dan merangkai pada breadboard.

Routine yang digunakan dalam program dapat dikategorikan menjadi beberapa bagian, yaitu Main Program Routine, ADC Routine, I2C Routine, LCD Routine, ASCII Routine dan Delay Routine. Main Program routine merupakan representasi langsung dari flowchart yang telah dibuat. ADC Routine adalah sekumpulan routine dalam assembly yang berisi serangkaian instruksi yang dilakukan untuk menerima nilai sensor dari input analog.

I2C Routine adalah sekumpulan routine yang berisi instruksi - instruksi untuk melakukan operasi pada I2C serial communication. LCD Routine adalah sekumpulan routine yang berisi instruksi - instruksi untuk melakukan operasi pada LCD. ASCII Routine adalah sekumpulan routine yang berisi instruksi - instruksi untuk mengubah nilai yang dibaca dari sensor analog menjadi nilai ASCIInya. Delay Routine adalah sekumpulan routine yang berisi instruksi - instruksi untuk membuat efek delay pada arduino.

### Implementasi Perangkat Lunak
Kode bahasa rakitan yang dibuat menghubungkan sensor MQ2 yang dihubungkan pada pin arduino melalui breadboard yang terhubung ke pin konverter analog digital (ADC) 0 yang kemudian kode tersebut akan membaca data analog yang masuk dari sensor dan akan memprosesnya menjadi data digital untuk mengirimkannya ke LCD (yang sebelumnya telah terhubung ke arduino menggunakan protokol I2C) yang kemudian akan menampilkan data mengenai kondisi tingkatan kandungan CO yang terdapat pada udara.

Selain itu kode ini akan menampilkan tingkatan tersebut kedalam 3 LED yang akan menampilkan data tersebut berdasarkan tingkatan yang telah diatur batasnya. 3 LED ini akan merepresentasikan tingkatan aman (hijau), waspada (kuning), dan bahaya (merah). Kemudian terdapat pin pada arduino yang akan digunakan untuk mengaktifkan buzzer yang akan menandakan tanda bahaya (ketika lampu LED merah menyala) yang menunjukkan bahwa tingkatan kandungan CO pada udara sudah dalam tahapan yang berbahaya.

### Evaluasi
Sistem tersebut mampu menunjukkan kadar CO dan memberikan aproksimasi tingkat CO yang terdapat pada udara disekitar dan menampilkannya pada LCD. Sistem ini dapat mengukur kadar CO dengan cukup akurat dan memberikan peringatan melalui buzzer jika kadar CO sudah dalam tahap berbahaya. Sistem ini juga mudah sekali digunakan karena tidak perlu interaksi dari pengguna dan mampu menampilkan status kadar CO ke 3 LED untuk memudahkan memantau tingkatan CO dalam udara. Sistem ini juga menggunakan sistem Arduino Uno berbasis ATMega 328p sehingga efisien dalam penggunaan daya, andal, dan mudah untuk diperbaiki.


## Kesimpulan
Berdasarkan serangkaian pengujian yang telah dilakukan, sistem ini berjalan dengan cukup baik pada rangkaian proteus dan rangkaian nyata. Sensor MQ2 yang digunakan dalam sistem ini mampu mendeteksi variasi kadar CO di udara. Protokol I2C yang digunakan untuk menghubungkan Arduino dengan LCD berfungsi dalam menampilan data CO secara real-time dan memberikan informasi yang jelas. Sistem indikator yang terdiri dari tiga LED (hijau, kuning, merah) berfungsi dengan baik dalam memberikan indikasi visual terhadap tingkat bahaya CO dengan ketentuan yang formatnya masih dalam ppm di mana LED hijau menyala pada kadar CO 0-141 ppm, LED kuning pada 141-216 ppm, dan LED merah menyala serta buzzer berbunyi ketika kadar CO melebihi 216 ppm.

Secara keseluruhan, sistem ini berhasil mengintegrasikan berbagai komponen untuk menciptakan alat deteksi CO sehingga dapat diimplementasikan dalam peningkatan kesehatan dengan memberikan peringatan dini terhadap paparan gas CO yang berbahaya.
