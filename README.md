# 👩‍🎓 Klasifikasi Pelamar Pekerjaan Berdasarkan _Skill_ dan _Job Requirement_ 

Untuk menerima seorang pelamar pekerjaan, seorang HR pastinya mempertimbangkan kesesuaian keahlian pelamar dengan keahlian yang dibutuhkan pada posisi tersebut. Akan tetapi, dengan banyaknya pelamar yang mendaftar, proses seleksi manual dapat memakan banyak waktu. Dengan demikian, projek ini bertujuan untuk mengklasifikasikan pelamar yang direkomendasikan dan tidak direkomendasikan berdasarkan keahlian serta _job requirements_. 

## 📂 Dataset 
Dataset yang digunakan pada projek ini berasal dari [Kaggle - Job Recommendation Dataset](https://www.kaggle.com/datasets/lastman0800/job-recomendation-dataset) yang terdiri dari: 

* `User_ID` : Unique identifiers for each user in the dataset
* `Job_ID` : Unique identifiers for each job listed in the dataset
* `User_Skills` : Contains a comma-separated list of skills that the user possesses
* `Job_Requirements` : Lists the required skills for each job
* `Match_Score` : Indicates how well the user's skills match the job requirements
* `Recommended` : Shows whether the job is recommended to the user based on the match score (0 is No, 1 is Yes).

## ⛓ WorkFlow

### 🛠 Preprocessing and EDA
* Memeriksa data duplikasi dan kardinalitas pada kolom kategori.
* Melakukan _cleaning_ pada entri kategori dengan menghilangkan spasi dan melakukan _lower case_ pada entri.
* Melakukan _sort_ pada urutan `User_Skills` dan `Job_Requirements` pada setiap entri di kolom kategori.

### 🧠 Training and Hyperparameter Tuning
Model utama yang digunakan pada proyek ini adalah `RandomForestClassifier`. Untuk mendapatkan performa prediksi yang optimal, dilakukan pencarian parameter terbaik (_hyperparameter tuning_) menggunakan `RandomizedSearchCV`. Berikut adalah parameter terbaik yang didapatkan dari proses tersebut:

* `n_estimators`: 200  
* `max_depth`: 7 
* `min_samples_leaf`: 6 

### 📊 Model Evaluation
Dengan menggunakan _best parameters_ di atas, model dievaluasi menggunakan data uji (_test set_) dan menghasilkan metrik sebagai berikut:

* **F1-Score**: 1.00

#### Analisis Confusion Matrix
Untuk memahami lebih dalam mengenai metrik _Precision_ dan _Recall_ yang dihasilkan, berikut adalah _Heatmap Confusion Matrix_ dari model evaluasi:

![Confusion Matrix](assets/confusion_matrix.png)
