# Tugas 2  
## Pemrosesan Word Count

## Metode 1 MapReduce
1. buat direktori HDFS
2. isi direktori tadi dengan input.txt berisikan kata-kata
3. Buat mapper.py
<img width="1314" height="665" alt="Screenshot 2026-01-20 173004" src="https://github.com/user-attachments/assets/b26968cf-7e33-4e12-ab25-cacab312bda4" />

4. buat reducer.py
<img width="1197" height="609" alt="Screenshot 2026-01-20 173016" src="https://github.com/user-attachments/assets/0c0757c8-3bf1-4456-b5fb-e01031235d10" />

5. Eksekusi program
`hadoop jar $HADOOP_HOME/share/hadoop/tools/lib/hadoop-streaming-*.jar \
-files mapper.py,reducer.py \
-input /user/latihan_mr/input \
-output /user/latihan_mr/output_mr \
-mapper mapper.py \
-reducer reducer.py`
6. Output Program
<img width="1198" height="621" alt="Screenshot 2026-01-20 173026" src="https://github.com/user-attachments/assets/5b8ce092-edda-4f87-be38-eea3ac6d8080" />


## Metode 2 Spark RDD
1. Install Apache Spark
2. jalankan spark shell dengan `pyspark`
3. Muat data dari hdfs dengan `lines_rdd = spark.sparkContext.textFile("input.txt")`
4. Pisahkan baris menjadi kata dengan flatmap `words_rdd = lines_rdd.flatMap(lambda line: line.lower().split(" "))`
5. buat pasangan kata `pairs_rdd = words_rdd.map(lambda word: (word, 1))`
6. Kurangi jumlah dengan menjumlahkan nilai berdasarkan key `counts_rdd = pairs_rdd.reduceByKey(lambda a, b: a + b)`
7. Ambil Hasil yang telah dihitung  `final_counts = counts_rdd.collect()`
8. Tampilkan 10 baris hasil `for word, count in final_counts[:10]: print(f"{word}: {count}")`
<img width="1208" height="616" alt="Screenshot 2026-01-20 173039" src="https://github.com/user-attachments/assets/1b43200d-0fe2-448b-830b-3b63090d263a" />


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
<img width="1217" height="616" alt="Screenshot 2026-01-20 173049" src="https://github.com/user-attachments/assets/35908966-1d90-417d-bb59-114d67c2c03f" />

