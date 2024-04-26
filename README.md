# lab2_web

Nama : Fajri Al Jauhari

NIM  : 312210476

## Belajar PHP Dasar
![Screenshot 2024-04-26 122957](https://github.com/allfazri2001/lab2_web/assets/167978131/ec860cdf-0f54-40c3-a1b0-7c9dbf9478f3)




Hasil:

![Screenshot 2024-04-26 123010](https://github.com/allfazri2001/lab2_web/assets/167978131/dd096233-258f-4996-8311-808c6418299d)





## Menggunakan Variable
![Screenshot 2024-04-26 123824](https://github.com/allfazri2001/lab2_web/assets/167978131/ba7e26ce-584b-45b1-ab37-d1f65ed10792)



Hasil:
![Screenshot 2024-04-26 123839](https://github.com/allfazri2001/lab2_web/assets/167978131/444584d3-3a65-42ba-bc73-f8ee0208f0b5)




## Form Input
![Screenshot 2024-04-26 130113](https://github.com/allfazri2001/lab2_web/assets/167978131/ee30cb4c-7af8-458a-bdc1-2474996e8d37)


Hasil:
![Screenshot 2024-04-26 130125](https://github.com/allfazri2001/lab2_web/assets/167978131/c75d109b-35ee-4261-b6e3-4c8a9871baa3)




## Tugas
![Screenshot 2024-04-26 130310](https://github.com/allfazri2001/lab2_web/assets/167978131/a7dfec53-b135-4de8-87ea-0a183af2bf0c)



Hasil:
![Screenshot 2024-04-26 130354](https://github.com/allfazri2001/lab2_web/assets/167978131/b0d429f7-e828-4d1e-b536-9290b7db95f8)






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


