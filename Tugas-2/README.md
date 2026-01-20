# Tugas 2  
## Pemrosesan Word Count

## Metode 1 MapReduce
1. buat direktori HDFS
2. isi direktori tadi dengan input.txt berisikan kata-kata
3. Buat mapper.py
<img width="1197" height="609" alt="TUGAS 2 GAMBAR 1" src="https://github.com/user-attachments/assets/6fb79dd5-125b-47e4-91ef-99d479b16446" />

4. buat reducer.py
<img width="1201" height="607" alt="TUGAS 2 GAMBAR 2" src="https://github.com/user-attachments/assets/309977a6-73d8-43a9-8d0d-75eb0b367388" />

5. Eksekusi program
`hadoop jar $HADOOP_HOME/share/hadoop/tools/lib/hadoop-streaming-*.jar \
-files mapper.py,reducer.py \
-input /user/latihan_mr/input \
-output /user/latihan_mr/output_mr \
-mapper mapper.py \
-reducer reducer.py`
6. Output Program
<img width="1198" height="620" alt="TUGAS 2 GAMBAR 3" src="https://github.com/user-attachments/assets/ab55231b-a78b-4091-aeaf-283acd891280" />


## Metode 2 Spark RDD
1. Install Apache Spark
2. jalankan spark shell dengan `pyspark`
3. Muat data dari hdfs dengan `lines_rdd = spark.sparkContext.textFile("input.txt")`
4. Pisahkan baris menjadi kata dengan flatmap `words_rdd = lines_rdd.flatMap(lambda line: line.lower().split(" "))`
5. buat pasangan kata `pairs_rdd = words_rdd.map(lambda word: (word, 1))`
6. Kurangi jumlah dengan menjumlahkan nilai berdasarkan key `counts_rdd = pairs_rdd.reduceByKey(lambda a, b: a + b)`
7. Ambil Hasil yang telah dihitung  `final_counts = counts_rdd.collect()`
8. Tampilkan 10 baris hasil `for word, count in final_counts[:10]: print(f"{word}: {count}")`
<img width="1208" height="621" alt="TUGAS 2 GAMBAR 4" src="https://github.com/user-attachments/assets/789f8854-92c1-417d-b781-1e1d40390451" />


## Metode 3 Spark DataFrame
1. Masuk ke spark shell `pyspark`
2. import module yang diperlukan   `from pyspark.sql.functions import explode, split, col`
3. Jadikan input sebagai dataframe `df = spark.read.text("input.txt")`
4. Transformasi dataframe `s_df = df.select(
 explode(split(col("value"), " ")).alias("word")
).filter(col("word") != "") # Filter kata kosong
`
5. Gabungkan menjadi satu grup dan hitung `counts_df = words_df.groupBy("word").count()`
6. Tampilkan 10 hasil teratas `counts_df.orderBy(col("count").desc()).show(10) `
<img width="1226" height="619" alt="TUGAS 2 GAMBAR 5" src="https://github.com/user-attachments/assets/1426b233-3f66-4e88-8051-c8c4b6480e95" />

