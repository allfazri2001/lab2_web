# lab2_web

Nama : Fajri Al Jauhari

NIM  : 312210476

## Belajar PHP Dasar
![324306925-a5dded82-7a92-49bc-9d3e-fb7a32bd45b3](https://github.com/allfazri2001/lab2_web/assets/167978131/deff4bf8-2bd7-4e69-b79d-aea6a93c916e)



Hasil:

![image 2](https://github.com/allfazri2001/lab2_web/assets/167978131/fcc89a04-c7b6-463d-b598-e245f41a9f9c)




## Menggunakan Variable
![image 3](https://github.com/allfazri2001/lab2_web/assets/167978131/6716736e-9d0e-4e06-bad8-fa2140f2f3dc)


Hasil:

![image 4](https://github.com/allfazri2001/lab2_web/assets/167978131/53d5eb2b-d2a4-4f41-b194-b4d879e8c2c8)



## Form Input
![image 5](https://github.com/allfazri2001/lab2_web/assets/167978131/858125e5-9217-4962-8896-8a6cb29498d0)



Hasil:

![image 6](https://github.com/allfazri2001/lab2_web/assets/167978131/5b597bdf-21bb-4bce-8f35-bf9689ad8cd6)



## Tugas
![image 7](https://github.com/allfazri2001/lab2_web/assets/167978131/4bcfdc02-15f5-4845-97d3-9c4a0d9171d0)


Hasil:

![image 8](https://github.com/allfazri2001/lab2_web/assets/167978131/67652ad4-fdb3-4bf6-a93e-5b62a1eaf280)




## Penjelasan

1 struktur html 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>PHP Dasar</title>
</head>
<body>
    <h2>Form Input</h2>
    <form method="post">
        <label>Nama: </label>
        <input type="text" name="nama">
        <label>Tanggal Lahir: </label>
        <input type="date" name="tanggal_lahir">
        <label>Pekerjaan: </label>
        <select name="pekerjaan">
            <option value="Operator">Operator</option>
            <option value="Developer">Developer</option>
            <option value="Manager">Manager</option>
        </select>
        <input type="submit" value="Kirim">
    </form>

Input Nama: Pengguna memasukkan nama mereka.

Input Tanggal Lahir: Pengguna memilih tanggal lahir menggunakan kontrol input tanggal.

Pilihan Pekerjaan: Pengguna memilih pekerjaan dari dropdown, yang akan mempengaruhi perhitungan gaji.

2. logika PHP proses formulir

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST" && isset($_POST['nama']) && isset($_POST['tanggal_lahir']) && isset($_POST['pekerjaan'])) {
    $nama = htmlspecialchars($_POST['nama']);
    $tanggal_lahir = $_POST['tanggal_lahir'];
    $pekerjaan = $_POST['pekerjaan'];


Pengecekan Metode dan Data: Memeriksa apakah formulir telah dikirim menggunakan metode POST dan semua data yang diperlukan ada.

Sanitisasi Input: Fungsi htmlspecialchars digunakan untuk menghindari serangan XSS (Cross-Site Scripting) dengan membersihkan input nama dari tag HTML atau karakter khusus.


3. kalkulasi umur

    $birthdate = new DateTime($tanggal_lahir);
    $today = new DateTime('today');
    $age = $birthdate->diff($today)->y;

Objek DateTime: Digunakan untuk memanipulasi tanggal dengan mudah.

Perhitungan Selisih Tahun: Menghitung selisih tahun antara tanggal lahir dan hari ini untuk mendapatkan umur.

4.Perhitungan Gaji dan Pajak  

    $salaries = [
        "Operator" => 1000000,
        "Developer" => 3000000,
        "Manager" => 5000000
    ];
    $taxRates = [
        "Operator" => 0.1,
        "Developer" => 0.15,
        "Manager" => 0.2
    ];
    $gaji = isset($salaries[$pekerjaan]) ? $salaries[$pekerjaan] : 0;
    $pajak = isset($taxRates[$pekerjaan]) ? $taxRates[$pekerjaan] : 0;
    $thp = $gaji - ($gaji * $pajak);


Array: Menyimpan nilai gaji dan pajak berdasarkan jenis pekerjaan.

Kalkulasi Gaji Bersih: Menghitung gaji bersih dengan mengurangkan pajak dari gaji kotor.

5.Menampilkan Hasil

    echo "Selamat Datang $nama<br>";
    echo "Usia Anda: $age tahun<br>";
    echo "Pekerjaan: $pekerjaan<br>";
    echo "Gaji sebelum pajak = Rp. " . number_format($gaji, 0, ',', '.') . "<br>";
    echo "Gaji yang dibawa pulang = Rp. " . number_format($thp, 0, ',', '.');
}
?>
</body>
</html>


