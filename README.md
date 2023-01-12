# Materi
## Apa itu CNN?
Convolutional Neural Network (CNN) merupakan sebuah algoritma pengembangan dari Neural Network yang berguna untuk permasalahan computer vision. Struktur dari CNN terbagi menjadi 2 bagian utama yaitu Feature Extraction dan juga Fully Connected Layer. Contoh arsitektur dari CNN dapat dilihat pada gambar di bawah ini. 

![image](https://user-images.githubusercontent.com/54859935/134260588-61ac7c37-2fc7-49ea-ae06-460eb54474ab.png)

Input dari algoritma ini berupa gambar yang biasanya memiliki 3 channel atau RGB. Input Gambar dari CNN akan dilakukan proses ekstraksi fitur menggunakan Convolutional layer yang berfungsi untuk melakukan konvolusi yang bertujuan menghasilkan filter-filter dari suatu gambar yang dapat digunakan sebagai fitur pengenal gambar tersebut. Setelah dilakukan operasi konvolusi, gambar tersebut akan dilakukan pemrosesan menggunakan layer pooling yang biasanya bertujuan untuk mengurangi ukuran dari gambar. Setelah fitur dari gambar tersebut dipelajari oleh model CNN, fitur tersebut kemudian masuk ke tahap klasifikasi. Tahap klasifikasi dilakukan dengan fully connected layer yang dibantu dengan bantuan softmax layer. Setelah tahapan klasifikasi dilakukan, maka prediksi dari CNN model akan berupa persentase dari kemungkinan label yang ada pada data yang digunakan. Penjelasan mengenai bagaimana cara kerja dari layer pada CNN akan di bahas pada point-point di bawah ini.

### Convolutional Layer
Convolutional layer merupakan blok bangunan inti dari arsitektur CNN karena sebagian proses komputasi dilakukan pada lapisan ini. Convolutional layer terdiri dari neuron yang tersusun sedemikian rupa sehingga membentuk sebuah filter dengan panjang dan tinggi (piksel). Filter menjadi peran utama pada proses pelatihan mesin dikarenakan filter inilah yang akan diperbaharui nilainya pada proses pelatihan. Konvolusi dilakukan dengan menggeser filter pada inputan citra dan akan dilakukan operasi dot product antara input dan nilai filter sehingga menghasilkan sebuah activation map atau feature map. Contoh operasi konvolusi dapat dilihat seperti pada gambar di bawah ini.

![image](https://user-images.githubusercontent.com/54859935/134260658-d7d253a8-8360-43e7-af6e-986d8bdf248a.png)

Gambar di atas merupakan ilustrasi proses konvolusi pada citra yang merupakan array dua dimensi I dengan bobot K (dua dimensi). Pada gambar tersebut, citra berukuran 4x3 konvolusi dengan menggunakan kernel berukuran 2x2. Citra yang dihasilkan adalah berukuran 3x2. Elemen pertama pada citra hasil konvolusi adalah merupakan jumlah dari perkalian bobot kernel dengan nilai citra yang bersangkutan. Terdapat 2 parameter yang dapat mempengaruhi bagaimana proses konvolusi terjadi, yakni stride dan padding. 

### Stride
Stride adalah sebuah parameter yang akan menentukan banyaknya jumlah pergeseran filter. Sebagai contoh apabila parameter stride bernilai 1, maka convolutional filter akan bergeser sebanyak 1 piksel secara horizontal lalu vertical. Semakin kecil nilai stride maka akan semakin detail informasi yang didapatkan dari sebuah citra, namun hal ini membutuhkan komputasi yang besar jika dibandingkan dengan nilai stride yang besar.

### Padding
Padding atau biasa disebut juga dengan zero padding adalah parameter yang menentukan jumlah piksel (bernilai 0) yang akan ditambahkan pada setiap sisi dari suatu input citra. Penambahan padding bertujuan untuk memanipulasi dimensi output dari convolutional layer. Tujuan dari penggunaan padding adalah dimensi output dari convolutional layer selalu lebih kecil dari inputnya, kecuali penggunaan 1x1 filter dengan nilai stride sama dengan satu. Output ini akan digunakan kembali sebagai input dari convolutional layer selanjutnya, sehingga semakin banyak informasi yang terbuang.

### Pooling Layer
Pooling layer adalah sebuah lapisan yang berguna untuk melakukan pengurangan matriks dengan menggunakan operasi pooling. Terdapat dua jenis pooling yang biasa digunakan pada CNN yaitu average pooling dan max pooling. Dalam operasi average pooling, nilai yang diambil adalah nilai rata-rata, sedangkan pada max pooling nilai yang diambil adalah nilai maksimal. Pada dasarnya pooling layer terdiri dari sebuah filter dengan ukuran dan stride tertentu yang akan bergeser sesuai dengan feature map. Tujuan utama dari operasi ini adalah untuk mengurangi dimensi dari feature map, sehingga mempercepat komputasi karena parameter yang harus diperbaharui dalam proses pelatihan semakin sedikit dan juga berfungsi untuk mengurangi kemungkinan terjadinya overfit. 

### Dropout Layer
Dropout layer adalah sebuah tipe lapisan yang bertujuan untuk menonaktifkan sebagian neuron yang terdapat pada sebuah arsitektur model deep learning. Penggunaan dropout layer biasanya bertujuan untuk mengurangi kemungkinan model deep learning overfit dengan data training. Cara kerja dropout layer adalah dengan tidak mengikut sertakan sekian persen parameter sehingga weight yang terdapat pada layer tersebut tidak ikut diperbaharui ketika proses forward dan juga backward propagation.

Nah, kita telah mengenal jenis-jenis layer yang biasa digunakan dalam suatu model CNN. Selanjutnya kita akan membahas mengenai salah satu komponen dalam model deep learning yang tidak kalah penting yaitu Fungsi aktivasi.

## Apa itu Fungsi Aktivasi?
Fungsi aktivasi adalah sebuah persamaan matematika yang bertujuan untuk mengaktifkan node yang ada pada suatu neural network. Node yang aktif akan menghasilkan output sesuai dengan jenis fungsi aktivasinya. Terdapat beberapa jenis fungsi aktivasi yang dapat digunakan sesuai dengan kebutuhan. Penjelasan mengenai beberapa fungsi aktivasi yang biasa digunakan dapat dilihat pada point-point di bawah ini.

### Rectrified Liniear Unit (ReLU)
Rectified Linear Unit (ReLU) adalah sebuah fungsi aktivasi yang biasa digunakan dalam pembuatan model pembelajaran mesin. Fungsi ReLU sering digunakan pada proses pembuatan model dikarenakan fungsi ini memungkinkan suatu model deep learning menghitung non-linear dan efek interaksi spesifik. Efek interaksi adalah suatu kondisi dimana suatu variabel dapat mempengaruhi prediksi tergantung pada nilai tersebut. Funsgi ReLU sering digunakan dikarenakan kesederhanaan komputasi yang dilakukan oleh fungsi ini. Hal ini dikarenakan  tidak adanya komputasi yang terlalu rumit sehingga membuat proses pelatihan suatu model dapat dijalankan dalam waktu yang relatif singkat. Secara garis besar cara kerja fungsi ReLU adalah fungsi ini akan mengembalikan nilai 0 jika menerima inputan negatif dan akan mengembalikan nilai positif yang sesuai dengan nilai inputan jika menerima inputan positif. Grafik fungsi ReLU dapat di lihat pada gambar di bawah ini.

![image](https://user-images.githubusercontent.com/54859935/134260822-94d7db95-6e66-4f7b-98e2-3c8236b9c610.png)

Kenapa si ReLU dikatakan fungsi yang minim komputasi? Nah jawabannya ada pada grafik diatas. Pada grafik tersebut, untuk setiap nilai inputan X yang negatif akan menghasilkan output 0 dan setelah inputan X bernilai positif, grafik mulai miring ke atas. Hal ini dikarenakan rumus dari fungsi ReLu yaitu R(z) = max(0, z) yang akan selalu mengembalikan nilai terbesar dari parameter inputan fungsi ReLU. 

### Leaky ReLU
Leaky ReLU adalah sebuah fungsi aktivasi varian dari ReLU yang memiliki tujuan untuk mengatasi permasalahan yang ada pada fungsi ReLU. Meskipun dari segi komputasi fungsi ReLU ringan tetapi memiliki kekurangan yang biasa disebut dying ReLU. Pada saat menggunakan fungsi ReLU terkadang terdapat neuron yang mati. Mati di sini maksudnya adalah neuron tersebut tidak mengeluarkan output selain 0. untuk mengatasi permasalahan ini maka diciptakanlah fungsi Leaky ReLU. Leaky ReLU di desinisikan sebagai:

![image](https://user-images.githubusercontent.com/54859935/134260870-8693cb59-a033-4692-878d-ba56aaa90641.png)

Dengan keterangan:
- a : merupakan hyperparamter yang menunjukkan seberapa banyak fungsi tersebut leaks. Parameter ini merupakan “slope of the function” untuk z< 0 dan biasanya nilai yang digunakan adalah 0.01. Slope kecil ini bertujuan untuk memastikan bahwa tidak ada neuron yang mati ketika training.

### Softmax
Softmax adalah sebuah fungsi aktivasi yang mengubah vektor nilai real X menjadi vektor nilai real X yang berjumlah 1. Fungsi softmax akan mengubah nilai inputan menjadi nilai dengan rentang 0 sampai dengan 1, sehingga hal ini dapat diinterpretasikan sebagai probabilitas. Nilai probabilitas softmax tergantung dengan besar nilai inputan yang masuk ke dalam fungsi ini. Jika salah satu besar nilai input adalah kecil ataupun negatif, maka nilai output dari fungsi softmax akan berupa nilai probabilitas kecil. Nilai probabilitas yang besar akan didapat jika fungsi ini mendapatkan nilai input yang besar atau positif. Semua nilai output dari fungsi softmax tetap berada dalam rentang 0 sampai dengan 1. 
Fungsi softmax biasa digunakan dalam problem klasifikasi dengan syarat jika kelas-kelas pada data saling eksklusif. Hasil dari komputasi MLP biasanya berupa skor bernilai nyata dan tidak mudah untuk diskalakan dan sulit untuk dikerjakan. Softmax berfungsi mengubah skor tersebut menjadi nilai probabilitas yang dinormalisasi dan nilai probabilitas ini dapat digunakan sebagai input ke dalam sistem lain. Hal inilah yang menjadi dasar penggunaan fungsi aktivasi softmax pada layer output pada suatu model deep learning seperti CNN. 

![image](https://user-images.githubusercontent.com/54859935/134268233-136afaf0-c75e-434a-9106-841705c18200.png)

![image](https://user-images.githubusercontent.com/54859935/134268290-1e4145ed-65a1-4d29-87a3-889090f8935f.png)

## Apa itu Optimizer?
Optimizer adalah sebuah algoritma yang berfungsi untuk meminimalkan fungsi kesalahan atau untuk memaksimalkan efisiensi produksi. Optimizer biasanya berupa fungsi matematika yang bergantung pada parameter model yang dapat dipelajari seperti bobot dan bias. Optimizer dapat membantu proses pelatihan suatu model deep learning dengan cara mengubah bobot dan bias untuk mengurangi kerugian. 

### Gradient Descent
Gradient Descent adalah sebuah algoritma optimasi yang paling dasar dan banyak digunakan seperti dalam permasalahan regresi dan juga klasifikasi. Contoh penggunaan gradient descent adalah pada saat proses propagasi balik yang telah dijelaskan pada sub bab sebelumnya. Algoritma ini bergantung pada turunan orde pertama dari fungsi kerugian (loss function) dan akan menghitung arah tujuan bobot yang harus diubah sehingga nilai kerugian mencapai nilai minimum. Propagasi balik akan mengirim nilai kerugian dari satu lapisan ke lapisan berikutnya. Parameter model akan dimodifikasi tergantung pada nilai kerugian, sehingga dapat diminimalkan. Gradient Descent memiliki persamaan sebagai berikut:

![image](https://user-images.githubusercontent.com/54859935/134268382-80448fa9-ad86-49ef-a269-3bec81c98644.png)

### Stochastic Gradient Descent
Stochastic Gradient Descent (SGD) adalah suatu fungsi optimasi varian dari gradient descent. Pada fungsi SGD, parameter model akan diperbaharui lebih sering dibandingkan dengan fungsi optimasi gradient descent. Parameter model yang sering diperbaharui menyebabkan fluktuasi fungsi kerugian pada intensitas yang berbeda dan juga parameter model memiliki varians yang tinggi. Persamaan SGD adalah sebagai berikut:

![image](https://user-images.githubusercontent.com/54859935/134268436-2109e184-247b-4e6f-b2a6-568432374e6b.png)

### Adam
Adam adalah algoritma optimasi yang biasa digunakan sebagai pengganti SGD klasik untuk memperbaharui weight network secara iteratif pada data latih. Adam bekerja dengan momentum orde pertama dan orde kedua. Prinsip utama algoritma ini adalah bahwa suatu proses perubahan nilai tidak terjadi begitu cepat karena dapat melewati nilai minimum. Proses perubahan nilai dilakukan secara perlahan untuk mendapatkan hasil yang tepat. Secara khusus, algoritma ini menghitung rata-rata eksponensial dari gradien sebelumnya M(t). M(t) dan V(t) adalah nilai momen pertama yang merupakan Mean dan momen kedua yang masing-masing merupakan varians tidak terpusat dari gradien.

![image](https://user-images.githubusercontent.com/54859935/134268476-37b98ec7-31d1-415b-995f-0741bfbfd25f.png)

Di sini, kita mengambil mean dari M(t) dan V(t) sehingga E[m(t)] dapat sama dengan E[g(t)] di mana, E[f(x)] adalah nilai harapan dari f(x). Untuk memperbaharui parameter, berikut bentuk formulanya:

![image](https://user-images.githubusercontent.com/54859935/134268517-a417f21c-4ac1-41a7-a179-5d0830b11570.png)


### AdamW
AdamW adalah sebuah alrogritma Adaptive Momentum dengan tambahan weight decay. Prinsip utama optimizer ini sama dengan Adam yaitu suatu proses perubahan nilai tidak terjadi begitu cepat karena dapat melewati nilai minimum. Proses perubahan nilai dilakukan secara perlahan untuk mendapatkan hasil yang tepat. Weight decay  di sini berfungsi untuk mendapatkan nilai learning rate yang optimal karena pada saat mencari nilai learning rate yang optimal, bobot weight decay berpengaruh. AdamW menyatukan algoritma adam dengan weight decay yaitu hyperparameter yang dapat diset. Algoritma dari AdamW dapat di lihat pada gambar di bawah ini.

![image](https://user-images.githubusercontent.com/54859935/134268535-6da29118-f656-499d-8893-5915f421d631.png)

## Loss Function
Loss function adalah sebuah cara untuk mengukur seberapa bagus performa yang dihasilkan oleh model dalam melakukan prediksi terhadap target kelas yang ada pada data. Fungsi ini bekerja ketika model memberikan kesalahan yang perlu kita perhatikan pada saat proses training. Loss function yang baik adalah loss function yang menghasilkan nilai error yang paling rendah. 

### Cross entropy
Cross entropy merupakan loss function yang biasa digunakan dalam multi-class classification. Fungsi ini dapat mengetahui seberapa besar nilai error yang dilakukan deep learning dengan nilai output berupa probabilitas. Fungsi ini akan mengukur entropy relatif antara dua distribusi probabilitas pada data yang sama dengan cara mengurangi log negatif dari dataset. Persamaan fungsi ini antara lain:

![image](https://user-images.githubusercontent.com/54859935/134268574-fda666ff-a3b7-453e-8ea6-779096d56f04.png)
