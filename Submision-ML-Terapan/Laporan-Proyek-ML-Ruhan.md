# Laporan Proyek Machine Learning - Ruhan Masykuri

## Project Overview

Industri per-film-an telah berkembang sangat pesat selama 20 tahun terakhir. Produksi film dan layanan akses terhadap film juga terus mengalami peningkatan signifikan. Peristiwa COVID-19 juga turut mempengaruhi perilaku masyarakat terhadap peningkatan penggunaan layanan streaming untuk mengakses film. Berbagai kemudahan dan banyaknya jumlah film mengakibatkan sebagian orang terkendala untuk memilih film apa yang akan mereka tonton. Fenomena ini dapat ditanggulangi dengan sebuah fasilitas rekomendasi film. Fasilitas ini diharapkan dapat memudahkan dan mengurangi waktu pengguna menentukan film apa yang akan mereka tonton.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Setiap tahun, industri perfilman tak henti-hentinya menghasilkan karya-karya baru. Sebagai contoh, pada tahun 2019, sejumlah 835 film dirilis di Amerika Serikat dan Kanada, menunjukkan peningkatan sebanyak 70 film dibandingkan tahun sebelumnya [1].
- Sistem rekomendasi kini sangat populer di industri hiburan, terutama dalam dunia perfilman, dan telah diterapkan di berbagai platform, seperti Netflix [2].
- Sebagai salah satu platform utama untuk penayangan film secara daring, Netflix menyediakan beragam serial dan film orisinal [3].


## Business Understanding

Banyaknya jumlah konten film dapat menimbulkan kebingungan pengguna untuk menentukan pilihan. Hal ini memungkinkan pengguna untuk menghabiskan banyak waktu dalam menentukan pilihan atau bahkan tidak jadi menggunakan layanan untuk menonton film. Permasalahan inilah yang akan dijawab menggunakan sistem rekomendasi. Sistem ini akan merekomendasikan film yang sesuai dengan preferensi pengguna sehingga pengguna tidak perlu kebingungan dan menghabiskan waktu cukup lama untuk menentukan pilihan film yang akan ditonton.


### Problem Statements

Permasalahan yang dihadapi adalah:
- Pengguna kesulitan menentukan film dikarenakan jumlah pilihan yang sangat banyak.
- Pengguna kesulitan menemukan film yang sesuai dengan preferensinya
- Pengguna kesulitan menemukan film dengan genre yang mirip dengan film yang pernah ditonton sebelumnya

### Goals

Proyek ini dapat memberikan jawaban sebagai berikut:
- Memberikan rekomendasi film kepada penguna
- Memudahkan pengguna mencari film yang sesuai dengan preferensinya
- Merekomendasikan film yang mirip dengan film yang pernah disukai pengguna
- Menggunakan pendekatan Content Based Filtering. Ide dari sistem rekomendasi berbasis konten (content-based filtering) adalah merekomendasikan item yang mirip dengan item yang disukai pengguna di masa lalu.


## Data Understanding
Dataset yang digunkan adalah [MovieLens full 25-million recommendation data 🎬](https://www.kaggle.com/datasets/patriciabrezeanu/movielens-full-25-million-recommendation-data), hasil rating dan tagging dari situs MovieLens, sebuah layanan rekomendasi film. Data terdiri dari 25.000.095 ratings dan 1.093.360 tag pada 62.423 film. Data ini dibuat oleh 162.541 users dari 09 Januari 1995sampai 21 November 2019.

file yang digunakan dalam project ini adaah movie.csv. File ini terdiri dari variabel movieId, title, dan genres.

Word cloud genre-image

## Data Preparation
Ada beberapa hal yang harus dilakukan untuk mempersiapkan data agar dapat diolah dan memberikan insight maksimal. 

**Tahap persiapan data dilakukan sebagai berikut**: 
- Terdapat 5.062 film yang tidak memiliki genre (no genres listed). Karena jumlahnya yang tidak signifikan maka dapat di drop.
- Karena keterbatasan RAM dari perangkat yang digunakan, film yang digunakan dibatasi hanya 20.000 film.


## Modeling
Sistem rekomendasi film dibuat menggunakan pendekatan Content Based Filtering. Pendekatan ini menggunakan genre film untuk menentukan rekomendasi film yang memiliki genre paling serupa dengan film yang ditentukan pengguna.

**Tahapan yang dilakukan adalah**: 
- Menggunakan TF-IDF Vectorizer untuk menjadi representasi genre dari film
- Tahap selanjutnya menggunakan cosine similarity untuk menemukan kecocokan antar film berdasarkan genrenya.
- Kemudian dibuat fungsi rekomendasi yang akan mengurutkan 5 film paling mirip dengan film yang ditentukan pengguna
- Kelebihan pendekatan ini adalah kesederhanaannya yang tetap memberikan hasil optimal.

## Evaluation
Dilakukan pengujian menggunkan film  Toy Story (1995) dengan genres Adventure|Animation|Children|Comedy|Fantasy. Rekomendasi yg diberikan adalah Shrek the Third (2007),  Asterix and the Vikings (Astérix et les Vikings) (2006), DuckTales: The Movie - Treasure of the Lost Lamp (1990), Emperor's New Groove, The (2000), 	Wild, The (2006). Seluruh hasil rekomendasi meiliki genre yang sama dengan film Toy Story (1995).

Pengujian kedua dilakukan dengan film Waiting to Exhale (1995) dengan genres Comedy|Drama|Romance. Rekomendasi yang diberikan adalah Kal Ho Naa Ho (2003), Walking and Talking (1996), Creator (1985), Racing with the Moon (1984), Last Holiday (1950). Seluruh hasil rekomendasi memiliki genre yang sama dengan film Waiting to Exhale (1995)

Berdasarkan Dua kali pengujian tersebut dapat disimpulkan bahwa model yang dhaslkan memiliki kaurasi 100%.


## Reverences
[1] R. A. Abarja, “Movie Rating Prediction using Convolutional Neural Network based on Historical Values,” International Journal of Emerging Trends in Engineering Research, vol. 8, no. 5, pp. 2156–2164, 2020, https://doi.org/10.30534/ijeter/2020/109852020.

[2] industry, and have been implemented in various platforms such as Netflix [4] S. Tobias, “The Future of Film Talk Is on Letterboxd,” The Ringer, Accessed: Dec. 26, 2023. [Online]. Available: https://www.theringer.com/movies/2020/9/18/21444082/letterboxd-filmdiscussion-site-streamingmovies.

[3] Z. Yu, “Netflix recommends: algorithms, film choice, and the history of the taste,” Inf Commun Soc, pp. 1–3, 2023, https://doi.org/10.1080/1369118x.2023.2252485.

**---Ini adalah bagian akhir laporan---**
