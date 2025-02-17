# Klasifikasi Gambar

Proyek ini untuk submission [Dicoding](dicoding.com) pada learning path **Machine Learning** pada course **Belajar Machine Learning untuk Pemula**.

## Hasil

:star::star::star:

- Overall Project

  Well done! submission yang kamu kirimkan memiliki train accuracy sebesar **90%**  dan validation accuracy **92%** Hal ini menunjukkan modelnya **good fit**.

- Code Review dan Saran

  - Kamu juga dapat mencoba untuk menerapkan callback accuracy dan val accuracy dengan threshold yang lebih tinggi misalnya:
    ```python
    if(logs.get('accuracy')>0.98 and logs.get('val_accuracy')>0.98)
    ```
  - Selain menggunakan library zipfile, kamu juga bisa menggunakan command !unzip untuk ekstrak file yang berbentuk zip dengan contoh sebagai berikut:
    ```py
    !unzip “path dataset” atau !unzip file_location.zip
    ```
  - Data Augmentation pada validation data  sebaiknya tidak digunakan untuk memperbanyak data dan memproduksi image yang berbeda. Kamu bisa menggunakan augmentasi pada data test tanpa menambahkan data dengan hanya melakukan rescale pada data testnya serta menggunakan validation_split untuk membagi datasetnya menjadi 40%.
    ```py
    validation_datagen = ImageDataGenerator(rescale=1./255, validation_split = 0.4)
    ```
  - Data augmentasi dilakukan hanya pada data train karena data dibuat lebih banyak untuk melatih model, bukan untuk melakukan evaluasi model. Jika data augmentation dilakukan di data tes maka dapat menghasilkan evaluasi model yang bias. Kamu dapat mempelajari [data augmentasi tidak dilakukan di validation set](https://machinelearningmastery.com/how-to-configure-image-data-augmentation-when-training-deep-learning-neural-networks/)
  - Terkadang, epoch yang terlalu banyak ketika training dapat menyebabkan Overfiting. Sehingga perlu ditetapkan threshold (batas) khusus terhadap salah satu atau beberapa parameter metrics saat training. Ketika threshold tercapai, training model harus berhenti. Untuk itu, menerapkan [Callback](https://www.tensorflow.org/api_docs/python/tf/keras/callbacks/Callback) untuk stop training pada threshold metric tertentu sebagai solusinya.
  - Dropout juga digunakan untuk mereduksi kemungkinan overfitting pada model yang dibuat. Kamu bisa pelajari penggunaan Dropout [disini](https://www.tensorflow.org/api_docs/python/tf/keras/layers/Dropout).
  - Ketika memprediksi gambar, model akan memberikan hasil prediksi yang baik ketika gambar yang di upload memiliki background green screen tetapi ketika image tidak memiliki background greenscreen hasil prediksi sering tidak sesuai.
  - Hal ini dikarenakan dataset yang dipakai untuk training memiliki background yang seragam sehingga model hanya mengenali background green screen. Untuk mengatasi hal tersebut kamu bisa menambahkan data image yang lebih beragam atau menggunakan pretrained model dan melakukan [Transfer Learning](https://www.tensorflow.org/tutorials/images/transfer_learning) atau kamu bisa menghilangkan background dengan [Remove Image Background](https://data-flair.training/blogs/python-remove-image-background/)
  - Kamu juga dapat melakukan evaluasi model yang telah dibuat menggunakan [confusion matrix](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html) dan [classification report](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.classification_report.html)
  - Untuk meningkatkan accuracy dan validation accuracy, kamu dapat coba [Transfer Learning - Fine Tuning](https://www.tensorflow.org/tutorials/images/transfer_learning)
  - Ketika ada data yang tidak seimbang atau imbalance, kamu dapat melakukan [Handle imbalance dataset](https://towardsdatascience.com/methods-for-dealing-with-imbalanced-data-5b761be45a18) dan [Mengatasi imbalance dataset](https://towardsdatascience.com/methods-for-dealing-with-imbalanced-data-5b761be45a18)
  - Kamu dapat download dataset dari Kaggle dengan menggunakan [Kaggle API](https://github.com/Kaggle/kaggle-api) dan [download datasets from Kaggle to Google Colab](https://medium.com/geekculture/how-to-download-datasets-from-kaggle-to-google-colab-7bb3c5a44c51) dan [cara menghubungkan drive ke colab](https://medium.com/@dede.brahma2/cara-menggunakan-google-colaboratory-5f5e4393ac2f#:~:text=Menggunakan%20Colab&text=Masuk%20kedalam%20google%20drive%20kemudian,colab%E2%80%9D%20setelah%20muncul%20klik%20connect.&text=Setelah%20berhasil%20instalasi%2C%20buat%20folder,kemudian%20masuk%20kedalam%20folder%20tersebut)
  - Kamu juga dapat mempelajari model yang kamu buat apakah sudah goodfit atau belum [Perbedaan Goodfit, Overfit dan Underfit](https://machinelearningmastery.com/learning-curves-for-diagnosing-machine-learning-model-performance)
  - Kamu juga bisa menerapkan beberapa saran lainnya agar penulisan kode dan pengetahuan machine learning kamu bertambah.
  - Beberapa saran yang dapat kamu terapkan:
    - [Image Segmentation OpenCV](https://machinelearningknowledge.ai/image-segmentation-in-python-opencv/)
    - [Rock Paper Scissors Menggunakan OpenCV](https://learnopencv.com/playing-rock-paper-scissors-with-ai/)
    - [Padding dan stride pada Convolutional Layer](https://machinelearningmastery.com/padding-and-stride-for-convolutional-neural-networks/)
    - [Memahami Impact Learning Rate Pada Neural Network](https://machinelearningmastery.com/understand-the-dynamics-of-learning-rate-on-deep-learning-neural-networks/fit)
    - [Dropout Regularization Pada Deep Learning](https://machinelearningmastery.com/dropout-regularization-deep-learning-models-keras/)
    - [Menerapkan Custom Callback](https://keras.io/api/callbacks/)

## Instruksi Submission:

### Kriteria utama yang harus dipenuhi:

1. Dataset yang dipakai haruslah dataset berikut : rockpaperscissors, atau gunakan link ini pada wget command: https://github.com/dicodingacademy/assets/releases/download/release/rockpaperscissors.zip.
2. Dataset harus dibagi menjadi train set dan validation set.
3. Ukuran validation set harus 40% dari total dataset (data training memiliki 1314 sampel, dan data validasi sebanyak 874 sampel).
4. Harus mengimplementasikan augmentasi gambar.
5. Menggunakan image data generator.
6. Model harus menggunakan model sequential.
7. Pelatihan model tidak melebihi waktu 30 menit.
8. Program dikerjakan pada Google Colaboratory.
9. Akurasi dari model minimal 85%.
10. Dapat memprediksi gambar yang diunggah ke Colab.
11. Menambahkan data diri (sesuai profil Dicoding) pada submission/project yang dikirimkan.

### Kriteria opsional

- Menggunakan lebih dari 1 hidden layer.
- Menerapkan lebih banyak augmentasi gambar.
- Menggunakan optimizer dan loss-function yang tidak diajarkan di kelas.
- Akurasi dari model di atas 95%.
- Menggunakan tiga atau lebih teknik yang tidak diajarkan di modul seperti penggunaan Callback.

### Submission ditolak

- Akurasi dari model Anda di bawah 85%.
- Proses pelatihan model Anda memakan waktu lebih dari 30 menit.
- Tidak menambahkan data diri (sesuai profil Dicoding) pada submission/project yang dikirimkan.

#### Note

- Pastikan file yang dikirim telah dijalankan alias sudah ada output-nya.
- Tips: Ganti runtime type ke GPU (T4) saat menjalankannya di Google Colaboratory agar lebih cepat.
