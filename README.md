# Laporan Proyek Machine Learning - Klasifikasi Gambar Bunga

## Domain Proyek
Domain yang dipilih untuk proyek *machine learning* ini adalah **Pendidikan**, dengan judul **Klasifikasi Gambar Bunga**
- Latar Belakang

![Mengenali bunga](https://www.naeyc.org/sites/default/files/styles/page_header_media_large/public/022018/family-banner23.jpg?itok=HFo_J3pm)

Anak-anak biasanya memiliki rasa ingin tahu yang tinggi. Untuk itu pendidikan pada anak dirancang dengan semenarik mungkin dan menyenangkan bagi anak. Salah satu cara yang bisa dilakukan adalah dengan menggunakan teknologi sebagai penunjang pembelajaran. Penggunaan teknologi dalam menyelesaikan tugas pada siswa, juga dapat menimbulkan kreativitas dikalangan siswa dalam mengembangkan pengetahuan yang telah mereka miliki [[1](https://doi.org/10.31599/jki.v1i1.265)].
Untuk itu dalam proyek ini saya mengangkat judul **Klasifikasi Gambar Bunga** yang diharapkan nantinya dapat diimplementasikan menjadi sebuah aplikasi yang menarik bagi anak-anak untuk belajar mengenali jenis-jenis bunga di sekitar mereka.

## Business Understanding

### Problem Statements
Berdasarkan latar belakang di atas, berikut ini merupakan rincian masalah yang dapat diselesaikan pada proyek ini:
- Bagaimana membuat model machine learning yang dapat mengklasifikasikan bunga dengan baik?
- Model yang seperti apa yang memiliki akurasi paling baik?

### Goals
Tujuan dari proyek ini adalah:
- Membuat model machine learning yang dapat mengenali jenis-jenis bunga tertentu sehingga dapat dikembangkan lebih lanjut pada aplikasi dan dapat digunakan untuk pembelajaran bagi anak.
- Membandingkan beberapa pretrained model sehingga ditemukan akurasi model yang paling baik untuk mengklasifikasikan gambar bunga.

### Solution statements
Untuk mencapai tujuan tersebut, dalam proyek ini akan dibuat beberapa model yang berbeda untuk dibandingkan, diantaranya adalah menggunakan:
- **Convolutional Neural Network**. CNN merupakan jaringan saraf *deep learning* yang dirancang untuk memproses susunan data terstruktur seperti gambar [[2](https://deepai.org/machine-learning-glossary-and-terms/convolutional-neural-network)]. Jaringan saraf *convolutional* banyak digunakan dalam *computer vision* dan telah menjadi seni untuk banyak aplikasi visual seperti klasifikasi gambar, dan juga telah menemukan keberhasilan dalam pemrosesan bahasa alami untuk klasifikasi teks.
- **VGG16**. VGG16 (juga disebut *OxfordNet*) adalah arsitektur jaringan saraf *convolutional* yang dinamai oleh *Visual Geometry Group* dari Oxford, yang mengembangkannya. Arsitektur ini digunakan untuk memenangkan kompetisi ILSVRC2014 *(Large Scale Visual Recognition Challenge 2014)* pada tahun 2014 dan masih dianggap sebagai model yang sangat baik untuk *computer vision* [[3](https://medium.com/@nutanbhogendrasharma/deep-convolutional-networks-vgg16-for-image-recognition-in-keras-a4beb59f80a7)].
- **ResNet50**. Jaringan residual atau *Residual Network (ResNet)* adalah jaringan saraf tiruan dari jenis yang menumpuk blok residual di atas satu sama lain untuk membentuk jaringan [[4](https://viso.ai/deep-learning/resnet-residual-neural-network/)].

- **DenseNet201**. Jaringan ini menghubungkan setiap lapisan ke setiap lapisan lainnya secara *feed-forward*. DenseNets memiliki beberapa keuntungan yang menarik: jaringan ini meringankan masalah *vanishing-gradient*, memperkuat *feature propagation*, mendorong penggunaan kembali fitur, dan secara substansial mengurangi jumlah parameter [[5](https://arxiv.org/abs/1608.06993)].

## Data Understanding
Dataset yang digunakan dalam proyek ini adalah data kumpulan gambar bunga. Data ini dapat diunduh melalui Kaggle. Dataset ini berisi 4000 lebih gambar yang terbagi menjadi 5 jenis bunga, yaitu : `daisy`, `tulip`, `sunflower`, `dandelion`, dan `rose`

![Flowers Recognition Dataset](https://i.postimg.cc/1RbGNmqp/Screenshot-17.png)

Informasi Dataset:

Jenis | Keterangan
--- | ---
Title | Flowers Recognition
Source | [Kaggle](https://www.kaggle.com/alxmamaev/flowers-recognition)
Owner | [Alexander Mamaev](https://www.kaggle.com/alxmamaev)
License | Unknown
Visibility | Public
Tags | image data, multiclass classification, plants
Usability | 6.3
Type | Image

## Data Preparation
Teknik yang digunakan dalam penyiapan data *(Data Preparation)* yaitu:
- **Split Data** atau pembagian dataset menjadi data latih dan data uji menggunakan bantuan `ImageDataGenerator`. Pembagian dataset ini bertujuan agar nantinya dapat digunakan untuk melatih dan mengevaluasi kinerja model. Pada proyek ini, 80% dataset digunakan untuk melatih model, dan 20% sisanya digunakan untuk mengevaluasi model.
- **Image Augmentation** merupakan teknik menghasilkan gambar baru untuk melatih model *deep learning* [[6](https://medium.com/analytics-vidhya/image-augmentation-9b7be3972e27)]. Pada proyek ini, augmentasi gambar adalah dengan menambahkan layer untuk melakukan *fliping*, *rotating*, *zoom*, dan *scaling*.

## Modeling
Pada tahap modeling ini dibuat beberapa model dengan arsitektur jaringan saraf tiruan yang berbeda-beda. Pada proyek ini akan dibuat 4 model, diantaranya yaitu menggunakan CNN, VGG16, ResNet50, dan DenseNet201.
Setelah melatih keempat model tersebut, didapatkan metriks akurasi sebagai berikut seperti pada diagram di bawah ini.

![model validation accuracy](https://i.postimg.cc/ydJ1FPz8/Screenshot-6.png)

Dari hasil tersebut dapat diketahui bahwa model dengan DenseNet201 memiliki kinerja yang lebih baik. Untuk itu model tersebut yang akan dipilih untuk digunakan.

## Evaluation
Pada proyek ini, model yang dibuat merupakan kasus klasifikasi dan menggunakan metriks akurasi dan loss.

- **Akurasi**

Akurasi merupakan kalkulasi presentase jumlah ketepatan prediksi dari jumlah seluruh data yang diprediksi. Nilai akurasi dapat dihitung dengan rumus berikut.

![accuracy](https://i.postimg.cc/TwSPSscb/Screenshot-15.png)

Berikut ini adalah diagram metriks akurasi yang didapatkan setelah melatih model DenseNet201.

![DenseNet201 model accuracy](https://i.postimg.cc/PrDHfJd0/Screenshot-4.png)

- ***Loss***

*Loss* adalah nilai yang dihasilkan dari *loss function*.  *Function* tersebut memiliki dua properti penting, semakin sedikit nilainya maka semakin baik model sesuai dengan data dan itu harus terdiferensiasi [[7](https://mragungsetiaji.github.io/python/machine%20learning/2018/09/02/deeplearning-loss-function-metric.html)]. *Loss function* yang digunakan pada proyek ini adalah [categorical_crossentropy](https://peltarion.com/knowledge-center/documentation/modeling-view/build-an-ai-model/loss-functions/categorical-crossentropy) yang mana perhitungannya digambarkan pada rumus berikut ini.

![categorical_crossentropy loss function](https://i.postimg.cc/jjSk2xpz/Screenshot-16.png)

Nilai ini adalah ukuran yang sangat baik tentang bagaimana dua distribusi probabilitas diskrit dapat dibedakan satu sama lain. Dalam konteks ini, *yi* adalah peluang terjadinya peristiwa *ii* dan jumlah semua *yi* adalah 1, artinya tepat satu peristiwa dapat terjadi. Tanda minus memastikan bahwa kerugian semakin kecil ketika distribusi semakin dekat satu sama lain.
Berikut ini adalah diagram loss yang didapatkan setelah melatih model DenseNet201.

![DenseNet201 model loss](https://i.postimg.cc/6TJD4VBg/Screenshot-5.png)

## Referensi
[[1](https://doi.org/10.31599/jki.v1i1.265)] Siahaan, M. (2020). "Dampak Pandemi Covid-19 Terhadap Dunia Pendidikan". *Jurnal Kajian Ilmiah, 1(1)*. https://doi.org/10.31599/jki.v1i1.265

[[2](https://deepai.org/machine-learning-glossary-and-terms/convolutional-neural-network)] Wood, T. - . *Convolutional Neural Network*. DeepAI. https://deepai.org/machine-learning-glossary-and-terms/convolutional-neural-network

[[3](https://medium.com/@nutanbhogendrasharma/deep-convolutional-networks-vgg16-for-image-recognition-in-keras-a4beb59f80a7)] Nutan. (2020). *Deep Convolutional Networks VGG16 for Image Recognition in Keras*. Medium. https://medium.com/@nutanbhogendrasharma/deep-convolutional-networks-vgg16-for-image-recognition-in-keras-a4beb59f80a7

[[4](https://viso.ai/deep-learning/resnet-residual-neural-network/)] Boesch, G. (2021). *Deep Residual Networks (ResNet, ResNet50) – Guide in 2021*. viso.ai . https://viso.ai/deep-learning/resnet-residual-neural-network/

[[5](https://arxiv.org/abs/1608.06993)] Huang, G., Liu, Z., Van Der Maaten, L., & Weinberger, K. Q. (2017). Densely connected convolutional networks. *In Proceedings of the IEEE conference on computer vision and pattern recognition* (pp. 4700-4708). https://arxiv.org/abs/1608.06993

[[6](https://medium.com/analytics-vidhya/image-augmentation-9b7be3972e27)] Tanwar, S. (2021). *Image Augmentation - Improving Deep learning models*. Medium. https://medium.com/analytics-vidhya/image-augmentation-9b7be3972e27

[[7](https://mragungsetiaji.github.io/python/machine%20learning/2018/09/02/deeplearning-loss-function-metric.html)] Setiaji, A. (2018). *Deep Learning : Loss Function, Metric*. GitHub. https://mragungsetiaji.github.io/python/machine%20learning/2018/09/02/deeplearning-loss-function-metric.html
