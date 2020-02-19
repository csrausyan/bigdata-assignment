# Big Data Assignment #1

### Business Understanding

Dataset dapat digunakan untuk :
1. Melihat laju penyebaran coronavirus pada beberapa lokasi berdasarkan peningkatan jumlah _suspected_ dan _confirmed_ per hari
2. Membandingkan daerah mana yang mengalami pasien coronavirus terbanyak berdasarkan jumlah _confirmed_
3. Membandingkan daerah mana yang meninggal paling banyak akibat coronavirus berdasarkan total _death_
4. Memperkirakan lokasi penyebaran coronavirus selanjutnya dengan membandingkan letak geografis daerah sekelilingnya dengan peningkatan jumlah _suspected_

### Data Understanding

Dataset yang digunakan memiliki dimensi sebesar 367 baris dan 8 kolom, dimana masing-masing kolom secara berurutan adalah _Row id_,_Province_,_Country_,_Date Last Update_,_Confirmed_,_Suspected_,_Recovered_ dan _Death_. berikut masing-masing penjelasan dari setiap kolom:

- Row id      
- Province            : provinsi dimana terdapat penderita coronavirus
- Country             : negara dimana terdapat penderita coronavirus
- Date last update    : tanggal kapan laporan mengenai coronavirus diterima
- Confirmed           : jumlah penderita yang terkonfirmasi terjangkit coronavirus
- Suspected           : jumlah penderita yang diduga terjangkit coronavirus
- Recovered           : jumlah orang yang sembuh dari coronavirus
- Death               : jumlah korban yang tewas akibat terjangkit coronavirus

### Data Preparation

Berikut proses yang dilakukan dengan dataset tersebut:

![preparasi](/assignment-1/image/big.png)

Langkah pertama adalah mengekstrak data yang berada dalam file .csv dengan menggunakan CSV READER. berikut hasil dari bacaan CSV READER:

![CSVREADER](/assignment-1/image/0.1.png)

Setelah diekstrak, data yang diesktrak dipisah menjadi dua menggunakan _column splitter, yang pertama membuang tabel _suspected_ dan _death_, sedangkan yang kedua membuang tabel _recovered_ dan _confirmed_

Splitting 1
![splitting1](/assignment-1/image/4.png)

Hasil splitting 1
1[resultsplitting1](/assignment-1/image/4.1.png)

Splitting 2
![splitting2](/assignment-1/image/5.png)

Hasil splitting 2
1[resultsplitting2](/assignment-1/image/5.1.png)

### Modeling

Data yang sudah di-_split_, disimpan di dua file yang berbeda, ***coronavirus - suspected_death.csv*** dan ***coronavirus - recovered_confirmed.xlsx***. file tersebut bisa dilihat di folder assignment-1
![savesplittingresult](/assignment-1/image/2.png)

untung proses Join, tabel yang digunakan adalah tabel hasil penghilangan _suspected_ dan _death_ dari yang pertama, dan tabel _recovered_ dan _confirmed_ dari tabel kedua ( yang mana dibuang pada pada hasil split kedua ). kedua tabel tersebut dijoin dengan node Joiner

Konfigurasi Joiner
![jointable](/assignment-1/image/6.png)

### Evaluation

Hasil join dari kedua table sebelumnya.
![joinresult](/assignment-1/image/6.1.png)

### Deployment

Hasil join kemudian disimpan ke dalam file yang bernama ***coronavirus - combined_again.xlsx***, kemudian untuk menyimpan ke dalam database MySQL, diperlukan node _MySQL Connector ( Legacy )_ dan _Database Writer ( Legacy )_

Konfigurasi _MySQL Connector_
![mysqlconnector](/assignment-1/image/7.png)

Hasil sambungan _MySQL Connector_
![connection](/assignment-1/image/7.1.png)

Konfigurasi _Database Writer_
![databasewriter](/assignment-1/image/8.png)

Hasil _Database Writer_ yang telah terkoneksi ke database MySQL
![databaseresult](/assignment-1/image/8.1.png)
