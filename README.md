# praktikum-basis-data-8
```
1. Tampilkan data karyawan yang bekerja pada departemen yang sama dengan karyawan yang bernama Dika
2. Tampilkan data karyawan yang gajinya lebih besar dari rata-rata gaji semua  karyawan. urutkan menurun berdasarkan besaran gaji
3. Tampilkan nik dan nama karyawan untuk semua karyawan yang bekerja di  department yang sama dengan karyawan dengan nama yang mengandung  huruf 'K'.
4. Tampilkan data karyawan yang bekerja pada departemen yang ada di  kantor pusat.
5 Tampilkan nik dan nama karyawan untuk semua karyawan yang bekerja di department yang sama dengan karyawan dengan nama yang mengandung huruf 'K'
dan yang gajinya lebih besar dari rata-rata gaji semua karyawan
```

1. Tampilkan data karyawan yang bekerja pada departemen yang sama dengan karyawan yang bernama Dika
```
SELECT 
kr.nik,
kr.nama,
kr.id_departemen
from karyawan kr
WHERE id_departemen = (SELECT id_departemen FROM karyawan WHERE nama = 'dika');
```

<img width="481" alt="Data karyawan" src="https://github.com/Muhamad-Raehan/Praktikum-basis-data-8/assets/116246238/47fb2ca8-a758-44e6-9b78-09a4c034699c">


2. Tampilkan data karyawan yang gajinya lebih besar dari rata-rata gaji semua  karyawan. urutkan menurun berdasarkan besaran gaji
```
SELECT 
kr.nik,
kr.nama,
kr.gaji_pokok
from karyawan kr
WHERE gaji_pokok > (SELECT avg(gaji_pokok) FROM karyawan );
```

<img width="370" alt="Data karyawan 2" src="https://github.com/Muhamad-Raehan/Praktikum-basis-data-8/assets/116246238/f20626f1-90f6-4e2d-bfcf-955c1348ae38">


3. Tampilkan nik dan nama karyawan untuk semua karyawan yang bekerja di  department yang sama dengan karyawan dengan nama yang mengandung  huruf 'K'.
```
SELECT 
kr.nik,
kr.nama,
kr.id_departemen
from karyawan kr
WHERE id_departemen in (SELECT id_departemen FROM karyawan WHERE nama LIKE '%K%');
```

<img width="493" alt="Data karyawan 3" src="https://github.com/Muhamad-Raehan/Praktikum-basis-data-8/assets/116246238/ae7a44b5-881d-45cb-9822-e0be75bc8a11">


4. Tampilkan data karyawan yang bekerja pada departemen yang ada di  kantor pusat.
```
SELECT 
d.id_perusahaan,
kr.nik,
kr.nama,
kr.id_departemen
from karyawan kr
LEFT JOIN departemen d on d.id_departemen = kr.id_departemen
WHERE id_perusahaan = 'p01';
```

<img width="381" alt="Data karyawan 4" src="https://github.com/Muhamad-Raehan/Praktikum-basis-data-8/assets/116246238/778faa69-bb30-4576-9d22-028edbd6dcb1">


5 Tampilkan nik dan nama karyawan untuk semua karyawan yang bekerja di department yang sama dengan karyawan dengan nama yang mengandung huruf 'K'
dan yang gajinya lebih besar dari rata-rata gaji semua karyawan
```
SELECT 
kr.nik,
kr.nama,
kr.id_departemen,
kr.gaji_pokok
from karyawan kr
WHERE gaji_pokok > (SELECT avg(gaji_pokok) from karyawan) AND nama LIKE '%K%';
```

<img width="479" alt="Data karyawan 5" src="https://github.com/Muhamad-Raehan/Praktikum-basis-data-8/assets/116246238/6fc9786a-a9cc-4b09-a0c9-fe1a5736f5cf">
