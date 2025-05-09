# Laporan Proyek Machine Learning - Ruhan Masykuri

## Project Overview

Industri per-film-an telah berkembang sangat pesat selama 20 tahun terakhir. Produksi film dan layanan akses terhadap film juga terus mengalami peningkatan signifikan. Peristiwa COVID-19 juga turut mempengaruhi perilaku masyarakat terhadap peningkatan penggunaan layanan streaming untuk mengakses film. Berbagai kemudahan dan banyaknya jumlah film mengakibatkan sebagian orang terkendala untuk memilih film apa yang akan mereka tonton. Fenomena ini dapat ditanggulangi dengan sebuah fasilitas rekomendasi film. Fasilitas ini diharapkan dapat memudahkan dan mengurangi waktu pengguna menentukan film apa yang akan mereka tonton.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Setiap tahun, industri perfilman tak henti-hentinya menghasilkan karya-karya baru. Sebagai contoh, pada tahun 2019, sejumlah 835 film dirilis di Amerika Serikat dan Kanada, menunjukkan peningkatan sebanyak 70 film dibandingkan tahun sebelumnya [1].
- Sistem rekomendasi kini sangat populer di industri hiburan, terutama dalam dunia perfilman, dan telah diterapkan di berbagai platform, seperti Netflix [2].
- Sebagai salah satu platform utama untuk penayangan film secara daring, Netflix menyediakan beragam serial dan film orisinal [3].


## Business Understanding

Industri hiburan, khususnya layanan streaming film dan video on-demand, semakin berkembang pesat. Platform seperti Netflix, Disney+, dan Amazon Prime menawarkan ribuan judul film, membuat pengguna sering kesulitan memilih tontonan yang sesuai dengan preferensi mereka. Dalam situasi ini, sistem rekomendasi menjadi sangat penting untuk meningkatkan pengalaman pengguna dengan memberikan saran film yang relevan dan personal.


### Problem Statements

Pengguna sering merasa kewalahan dengan banyaknya pilihan film yang tersedia, sehingga tidak dapat dengan mudah menemukan film yang sesuai dengan selera mereka. Selain itu, platform penyedia layanan hiburan juga menghadapi tantangan dalam menjaga keterlibatan dan loyalitas pengguna jika tidak mampu menyajikan konten yang relevan secara konsisten.

### Goals

Tujuan dari proyek ini adalah membangun sistem rekomendasi berbasis machine learning yang dapat menyarankan film kepada pengguna berdasarkan preferensi mereka terhadap film-film sebelumnya. Dengan sistem ini, diharapkan:
- Pengalaman pengguna menjadi lebih personal dan memuaskan.
- Waktu pencarian film dapat dikurangi.
- Meningkatkan rata-rata waktu tonton per pengguna per sesi.
- Mengurangi bounce rate atau exit rate pada halaman pencarian film.
- Meningkatkan jumlah film yang ditonton berdasarkan hasil rekomendasi sistem.



## Data Understanding
Dataset yang digunkan adalah MovieLens full 25-million recommendation data 🎬 yang dapat didownload [di sini](https://www.kaggle.com/datasets/patriciabrezeanu/movielens-full-25-million-recommendation-data). Data ini merupakan hasil rating dan tagging dari situs MovieLens, sebuah layanan rekomendasi film. Data terdiri dari 25.000.095 ratings dan 1.093.360 tag pada 62.423 film. Data ini dibuat oleh 162.541 users dari 09 Januari 1995sampai 21 November 2019.

Data ini terbagi menjadi enam dataset sebagai berikut:
### movies.csv
  
File ini terdiri dari 62.423 baris. Dataset ini tidak memiliki missing values dan data duplikat. Pada kolom genres ada 5.062 film yang tidak memiliki list genre. Uraian fiture yang terdapat pada dataset ini adalah:
- movieId

62.423 identitas film yang digunakan untuk mempermudah pengolahan data. Id ini dimulai dari 1 - 209.171.
- title

62.423 judul film besertatahun rilisnya
- genres

62.423 pengkategorian genre film dimulai dari genre tunggal, kombinasi beberapa genre, dan "no genres listed".

### ratings.csv

File ini terdiri adri 25.000.095 baris data yang berisikan pemberian rating terhadap film oleh user. Dataset ini tidak memliki missing values dan data duplikat. Uraian fiture yang terdapat pada dataset ini adalah:
- userId

25.000.094 baris data identitas user yang terdiri dari Id 1 - 162541.
- movieId

62.423 identitas film yang digunakan untuk mempermudah pengolahan data. Id ini dimulai dari 1 - 209.171.
- rating

25.000.094 baris nilai rating diberikan pada skala 5 bintang, dengan penambahan setengah bintang (0,5 bintang - 5,0 bintang).
- timestapm

timestapm mewakili detik sejak tengah malam Waktu Universal Terkoordinasi (UTC) tanggal 1 Januari 1970.

### tags.csv

Dataset ini memiliki 10.93.360 baris dan empat kolom (userId, movieId, tag, timestamp). Terdapat 16 minssing values pada kolom tag dan tidak ada data duplikasi. Uraian fiture yang terdapat pada dataset ini adalah:
- userId

25.000.094 baris data identitas user yang terdiri dari Id 1 - 162541.
- movieId

62.423 identitas film yang digunakan untuk mempermudah pengolahan data. Id ini dimulai dari 1 - 209.171.

- tag

1.093.344 baris data tag adalah metadata yang dibuat pengguna tentang film. Setiap tag biasanya berupa satu kata atau frasa pendek. Arti, nilai, dan tujuan tag tertentu ditentukan oleh setiap pengguna. Terdapat 16 missing values pada fiture ini sehingga dilakukan drop terhadap data missing tersebut.
- timestamp

1.093.359  data timestapm mewakili detik sejak tengah malam Waktu Universal Terkoordinasi (UTC) tanggal 1 Januari 1970.


### links.csv

Dataset memiliki 62.423 baris data dan tiga fitur (movieId, imdbId, tmdbId).
terdapat 107 missing values pada  kolom tmdbId dan tidak ada duplikasi data. Uraian fiture yang terdapat pada dataset ini adalah:
- movieId

62.423 identitas film yang digunakan untuk mempermudah pengolahan data. Id ini dimulai dari 1 - 209.171.
- imdbId

imdbId adalah pengenal untuk film yang digunakan oleh <http://www.imdb.com>. Misalnya, film Toy Story memiliki tautan <http://www.imdb.com/title/tt0114709/>.
- tmdbId

tmdbId adalah pengenal untuk film yang digunakan oleh <https://www.themoviedb.org>. Misalnya, film Toy Story memiliki tautan <https://www.themoviedb.org/movie/862>. Terdapat 107 missing values pada fitur ini.
### genome-scores.csv

File ini terdiri dari 15.584.448 baris data dan tiga kolom (movieId, tagId, relevance). File ini tidak memiliki missing values dan data duplikasi. Uraian fiture yang terdapat pada dataset ini adalah:
- movieId

62.423 identitas film yang digunakan untuk mempermudah pengolahan data. Id ini dimulai dari 1 - 209.171.

- tagId

1.093.344 baris data tag adalah metadata yang dibuat pengguna tentang film. Setiap tag biasanya berupa satu kata atau frasa pendek. Arti, nilai, dan tujuan tag tertentu ditentukan oleh setiap pengguna. Terdapat 16 missing values pada fiture ini

- relevance

Berdasarkan paper yang dapat didownload [di sini](http://files.grouplens.org/papers/tag_genome.pdf), genom tag mengodekan seberapa kuat film menunjukkan sifat-sifat tertentu yang direpresentasikan oleh tag (atmosferik, menggugah pikiran, realistis, dll.). Genom tag dihitung menggunakan algoritma machine learinng pada feedback yang diberikan user termasuk tag, peringkat, dan ulasan tekstual.
### genome-tags.csv

Dataset ini terdiri dari 1.128 baris data dan dua kolom(tagId dan tag). file ini tidak memiliki missing values dan data duplikasi. Uraian fiture yang terdapat pada dataset ini adalah:
- tagId

1.093.344 baris data tag adalah metadata yang dibuat pengguna tentang film. Setiap tag biasanya berupa satu kata atau frasa pendek. Arti, nilai, dan tujuan tag tertentu ditentukan oleh setiap pengguna. Terdapat 16 missing values pada fiture ini

- tag

1.093.344 baris data tag adalah metadata yang dibuat pengguna tentang film. Setiap tag biasanya berupa satu kata atau frasa pendek. Arti, nilai, dan tujuan tag tertentu ditentukan oleh setiap pengguna. Terdapat 16 missing values pada fiture ini

## Data Preparation
Ada beberapa hal yang harus dilakukan untuk mempersiapkan data agar dapat diolah dan memberikan insight maksimal. 

**Tahap persiapan data dilakukan sebagai berikut**: 
- Terdapat 5.062 film yang tidak memiliki genre (no genres listed). Karena jumlahnya yang tidak signifikan maka yang digunakan hanyalah daata film yang memiliki genre.
- Karena keterbatasan RAM dari perangkat yang digunakan, film yang digunakan dibatasi hanya 20.000 film.
- Menggunakan TF-IDF Vectorizer untuk menghitung seberapa penting sebuah kata tarhadap seluruh kata. Nilai yang diperoleh akan digunakan untuk merepresentasikan genre film tersebut.

## Modeling
Sistem rekomendasi film dibuat menggunakan pendekatan Content Based Filtering. Pendekatan ini menggunakan genre film untuk menentukan rekomendasi film yang memiliki genre paling serupa dengan film yang ditentukan pengguna.

**Tahapan yang dilakukan adalah**: 

- Menggunakan cosine similarity untuk menemukan kecocokan antar film berdasarkan genrenya. Metode ini dapat mengukur kemiripan data berdasarkan nilai cosinus representasi vektor dari data yang dibandingkan.
- Dibuat fungsi rekomendasi yang akan mengurutkan 5 film paling mirip dengan film yang ditentukan pengguna
- Kelebihan pendekatan ini adalah kesederhanaan tanpa membutuhkan komputasi yang rumit namun tetap memberikan hasil optimal.

Berikut adalah rekomendasi berdasarkan film pilihan:
|Film Uji | Genre|
|---------|------|
|Toy Story (1995)| Adventure, Animation, Children, Comedy, Fantasy|

|No|Rekomendasi|Genre|
|--|-----------|-----|
|1|Emperor's New Groove, The (2000)|Adventure, Animation, Children, Comedy, Fantasy|
|2|Asterix and the Vikings (Astérix et les Vikings) (2006)|Adventure, Animation, Children, Comedy, Fantasy|
|3|Monsters, Inc. (2001)|Adventure, Animation, Children, Comedy, Fantasy|
|4|Tale of Despereaux, The (2008)|Adventure, Animation, Children, Comedy, Fantasy|
|5|Toy Story 2 (1999)|Adventure, Animation, Children, Comedy, Fantasy|


|Film Uji | Genre|
|---------|------|
|Waiting to Exhale (1995)| Comedy, Drama, Romance|

|No|Rekomendasi|Genre|
|--|-----------|-----|
|1|World According to Garp, The (1982)|Comedy, Drama, Romance|
|2|Battle in Heaven (Batalla en el cielo) (2005)|Comedy, Drama, Romance|
|3|Quality Street (1937)|Comedy, Drama, Romance|
|4|Bombshell (1933)|Comedy, Drama, Romance|
|5|Friends with Money (2006)	|Comedy, Drama, Romance|


## Evaluation
Evaluasi terhadap model dilakukan dengan menghitung presisi genre film referensi user dan genre film rekomendasi. Setelah dilakukan pengujian menggunakan 100 referensi film yang dipilih secara acak, diperoleh nilai presisi 100%

Sistem rekomendasi yang dihasilkan memiliki akurasi yang sangat tinggi. Hal ini akan memudahkan dan mempersingkat waktu pengguna untuk memilih film yang sesuai dengan film referensinya. Hal ini tentunya juga akan meningkatkan loyalitas pengguna karena kemudahan yang ditawarkan dalam menentukan film yang akan dipilih. Ini juga akan berdampak pada meningkatnya rata-rata waktu tonton per penggunda dan mengurangi exit rate pada halaman pencarian film. Pada akhirnya ini akan berimpikasi pada meningkatnya jumlah film yang ditonton berdasarkan hasil rekomendasi sistem.

Pada akhirnya daat disimpulkan bahwa projek ini dapat menjadi solusi dari permasalahan-permasalahan bisnis yang telah disampaikan di atas. Pada prinsipnya bisnis hiburan film tidak hanya berfokus pada penyediaan film-film berkualitas, namun juga memberikan layanan yang memudahkan pengguna menemukan film berkualitas yang sesuai dengan preferensinya.

## Reverences
[1] R. A. Abarja, “Movie Rating Prediction using Convolutional Neural Network based on Historical Values,” International Journal of Emerging Trends in Engineering Research, vol. 8, no. 5, pp. 2156–2164, 2020, https://doi.org/10.30534/ijeter/2020/109852020.

[2] industry, and have been implemented in various platforms such as Netflix [4] S. Tobias, “The Future of Film Talk Is on Letterboxd,” The Ringer, Accessed: Dec. 26, 2023. [Online]. Available: https://www.theringer.com/movies/2020/9/18/21444082/letterboxd-filmdiscussion-site-streamingmovies.

[3] Z. Yu, “Netflix recommends: algorithms, film choice, and the history of the taste,” Inf Commun Soc, pp. 1–3, 2023, https://doi.org/10.1080/1369118x.2023.2252485.

**---Ini adalah bagian akhir laporan---**
