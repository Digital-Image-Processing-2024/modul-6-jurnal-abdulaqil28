[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/swTbasko)
# Resume Finger Simulation Experiment Abdul Aqil Murtadho - F1D022029


## Data Understanding
Pada proyek ini, digunakan 2100 gambar yang dikelompokkan ke dalam lima kelas (F1, F2, F3, F4, F5) dengan distribusi yang hampir merata: F1 (422 gambar), F2 (419 gambar), F3 (420 gambar), F4 (419 gambar), dan F5 (420 gambar). Data diperoleh dengan membaca gambar dari folder yang sesuai dengan kelasnya, setelah mengubah format warna dari BGR ke RGB, dan mengubah ukuran gambar menjadi 150x150 piksel. Pendekatan ini memastikan distribusi data yang seimbang di setiap kelas, penting untuk menghindari bias dalam pelatihan model klasifikasi gambar.

## Data Preparation

### Image Augmentation

kombinasi teknik augmentasi gambar berupa rotasi dan pencerminan (mirroring) untuk memperluas dataset, di mana setiap gambar asli diperbesar dengan menghasilkan 4 gambar tambahan. Teknik yang digunakan meliputi rotasi dengan sudut acak antara 5 hingga 360 derajat, dan pencerminan secara horizontal atau vertikal setelah rotasi. Setiap gambar asli dirotasi dan dicerminkan untuk menciptakan variasi yang lebih besar, menghasilkan total 5 gambar dari setiap gambar asli, yang membantu meningkatkan keragaman data.

### Preprocessing

teknik preprocessing untuk menyiapkan data gambar agar model pembelajaran mesin dapat bekerja dengan lebih efektif. Pertama, menggunakan penghapusan latar belakang dengan mendeteksi warna kulit pada model HSV dan operasi morfologi untuk memusatkan perhatian pada objek utama dan mengurangi kebisingan dari latar belakang yang tidak relevan. Kedua, gambar diubah menjadi grayscale menggunakan rata-rata tertimbang dari saluran warna RGB setelah pemfilteran Gaussian, yang membantu menyederhanakan data dan mengurangi kompleksitas komputasi. Ketiga, menerapkan equalisasi histogram untuk meningkatkan kontras gambar sehingga fitur penting menjadi lebih jelas dan perbedaan antar bagian gambar lebih menonjol. Keempat, deteksi tepi dilakukan dengan filter Sobel untuk mengidentifikasi batas dan bentuk objek, yang sangat penting dalam tugas pengenalan objek. Terakhir, normalisasi dilakukan dengan mengubah nilai piksel gambar ke rentang 0-255 berdasarkan nilai minimum dan maksimum untuk memastikan konsistensi data yang diberikan kepada model. Teknik-teknik ini dipilih berdasarkan percobaan dan analisis hasilnya terhadap akurasi model, sehingga meningkatkan kualitas data, mengurangi kebisingan, dan memastikan model dapat mengenali dan mengklasifikasikan objek dengan lebih akurat dan efisien.


### Feature Selection

Proses Feature Selection dalam percobaan ini dilakukan dengan mengimplementasikan berbagai metode ekstraksi fitur yang umum digunakan dalam analisis tekstur gambar, yaitu Contrast, Dissimilarity, Homogeneity, Energy, Correlation, ASM (Angular Second Moment), dan Entropy. Setiap metode memiliki keunikan dan memberikan informasi yang berbeda tentang tekstur gambar. Kontras, dissimilaritas, homogenitas, dan energi menggambarkan ciri-ciri kontras, variasi, homogenitas, dan kekuatan tekstur gambar, sementara korelasi menggambarkan keterkaitan antara intensitas piksel dalam gambar. ASM memberikan informasi tentang kekuatan tekstur dalam arah tertentu, sedangkan entropi mengukur tingkat ketidakpastian piksel dalam gambar. Melalui kombinasi fitur-fitur ini, dapat memperoleh representasi yang kaya tentang tekstur gambar, yang kemudian dapat digunakan untuk analisis lebih lanjut seperti klasifikasi atau deteksi pola. Oleh karena itu, pemilihan fitur ini bertujuan untuk memperoleh informasi yang cukup untuk membedakan dan menggambarkan berbagai tekstur gambar dengan akurat.

## Modeling

proses hyperparameter tuning akan dilakukan untuk memastikan model yang digunakan mencapai performa optimal. Pada code di projek ini, dapat melakukan tuning pada parameter-parameter model seperti jumlah tetangga (n_neighbors) untuk K-Nearest Neighbors (KNN), jenis kernel, C, dan gamma untuk Support Vector Machine (SVM), serta jumlah pohon (n_estimators), kedalaman maksimum (max_depth), dan jumlah fitur yang dipertimbangkan pada setiap split (max_features) untuk Random Forest. Proses tuning ini dilakukan untuk memperoleh kombinasi parameter terbaik yang menghasilkan akurasi prediksi tertinggi. Teknik tuning yang umum digunakan adalah Grid Search atau Randomized Search, di mana menguji berbagai kombinasi nilai parameter dan memilih kombinasi terbaik berdasarkan metrik evaluasi seperti akurasi, presisi, recall, atau F1-Score. Dengan melakukan hyperparameter tuning, dapat memastikan bahwa model yang kembangkan memiliki kinerja yang optimal dalam memecahkan masalah yang dihadapi.
## Evaluation
 
evaluasi dilakukann dengan visualisasi confusion matrix yang diperoleh untuk setiap model (KNN, SVM, dan RF), dapat mengevaluasi performa model berdasarkan kemampuannya dalam melakukan klasifikasi pada kelas-kelas yang berbeda. Dalam setiap percobaan, dapat memperhatikan peningkatan atau penurunan jumlah prediksi yang benar (true positives) dan salah (false positives), serta jumlah kasus yang tidak terklasifikasi dengan benar (misclassifications). Dengan melihat matriks, dapat mengevaluasi seberapa baik model dalam mengidentifikasi kelas-kelas yang berbeda dan memperbaiki kinerjanya dengan menyesuaikan hyperparameter atau fitur yang digunakan. Peningkatan performa model dapat dilihat dari peningkatan akurasi, presisi, recall, atau F1-Score pada berbagai percobaan yang telah dilakukan.

_Catatan:_

- _Tutorial mengenai penggunaan Markdown dapat dibaca [di sini](https://guides.github.com/features/mastering-markdown/)_
- _Kalian dapat melakukan copy untuk file `percobaan_n.ipynb` (ganti `n` dengan nomor percobaan) untuk setiap percobaan yang kalian lakukan._