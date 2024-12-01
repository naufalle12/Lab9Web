# Lab9Web

# header :
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Modularisasi Praktikum 8</title>
    <link href="modular/style.css" rel="stylesheet" type="text/css" media="screen" />
</head>
<body>
<div class="container">
    <header>
        <h1>Praktikum Modularisasi</h1>
    </header>
    <nav>
        <a href="pages/home.php">Home</a>
        <a href="pages/about.php">About</a>
        <a href="pages/kontak.php">Kontak</a>
        <a href="pages/database_page.php">Database</a>
    </nav>

## footer php
<footer>
    <p>&copy; <?php echo date('Y'); ?>, Informatika, Universitas Pelita Bangsa</p>
</footer>
</div>
</body>
</html>

## home php
<?php require('header.php'); ?>
<div class="content">
    <h2>ini halaman home</h2>
    <p>ini adalah bagian content dari halaman</p>
</div>

<?php require('footer.php');?>

# about php
<?php require('header.php'); ?>

<div class="content">
    <h2>ini halaman about</h2>
    <p>ini adalah bagian content dari halaman</p>
</div>

<?php require('footer.php'); ?>

# db config php
<?php
$host = 'localhost';
$user = 'root';
$password = '';
$database = 'nama_database';

$connection = mysqli_connect($host, $user, $password, $database);

if (!$connection) {
    die("Koneksi ke database gagal: " . mysqli_connect_error());
}
?>


# db page php
<?php
require('../modular/header.php');
require('../db_config.php');
?>
<div class="content">
    <h2>Data dari Database</h2>
    <table border="1">
        <tr>
            <th>ID</th>
            <th>Nama</th>
            <th>Email</th>
        </tr>
        <?php
        $query = "SELECT id, nama, email FROM users";
        $result = mysqli_query($connection, $query);

        if ($result) {
            while ($row = mysqli_fetch_assoc($result)) {
                echo "<tr>";
                echo "<td>{$row['id']}</td>";
                echo "<td>{$row['nama']}</td>";
                echo "<td>{$row['email']}</td>";
                echo "</tr>";
            }
        } else {
            echo "<tr><td colspan='3'>Data tidak tersedia</td></tr>";
        }
        ?>
    </table>
</div>
<?php
require('../modular/footer.php');
?>

![Screenshot (331)](https://github.com/user-attachments/assets/fb3340d2-6acc-4e5e-8695-f0153ccb7811)
