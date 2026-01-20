# TUGAS 1
## Installasi HDFS
Untuk melakukan installasi HDFS pertama download semua program yang dibutuhkan:
- Apache Hadoop
- WSl (jika di windows)
- SSH

### Langkah-langkah
1. Download dan Ekstrak File Hadoop ke WSL
2. Format NameNode untuk pertama kali dengan `hdfs namenode -format`
3. Jalankan HDFS dengan `start-dfs.sh`
<img width="1210" height="584" alt="tugas 1 gambar 1" src="https://github.com/user-attachments/assets/bc485e10-58f7-410b-9b69-6d80816c01d4" />

4. Jalankan yarn dengan `start-yarn.sh`
![yarn localhost:8088](yarn.sh-png)
5. Cek status dengan `jps` atau `hdfs dfsadmin -report`
<img width="1210" height="612" alt="tugas 1 gambar 2" src="https://github.com/user-attachments/assets/1ed17690-6fbf-49cc-a914-864cb4afb237" />


6. Buat script agar command bisa dipakai di direktori apapun <sup>*opsional*</sup>
<img width="1207" height="606" alt="tugas 1 gambar 3" src="https://github.com/user-attachments/assets/0afd1d9e-404f-455c-b4b2-b6aea35f8a33" />


### Test HDFS
1. jalankan hdfs `start-dfs.sh`
2. buat direktori pada namenode `hdfs dfs -mkdir /praktikum`
3. taruh file kedalam hdfs `hdfs dfs -put *nama file* /praktikum`
4. tampilkan isi file dengan `hdfs dfs -cat *nama file* /praktikum`
<img width="1212" height="614" alt="tugas 1 gambar 4" src="https://github.com/user-attachments/assets/df73baad-aacd-4a92-8060-67824dc72ec3" />

