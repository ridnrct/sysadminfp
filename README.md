# sysadminfp
System Admin &amp; OS Server
Operating System CentOS 7 :
  1. SSH Server
  2. DHCP Server
  3. DNS Server
  4. Web Server
  5. Database Server

Setelah semua service terinstall, memulai konfigurasi final project :
Install php5 untuk support apache.
```
yum -y install php php-mysql php-pdo php-gd php-mbstring
```
Buat file index.php pada direktori /var/www/html
```
nano /var/www/html/index.php
```
Kemudian isikan :
```
<?php

/**
 * Use an HTML form to create a new entry in the
 * users table.
 *
 */

 if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    require "config.php";
    require "common.php";

try  {
 $connection = new PDO($dsn, $username, $password, $options);
 $komen = array(
            "nama"      => $_POST['nama'],
            "email"     => $_POST['email'],
            "subjek"    => $_POST['subjek']
        );
  $sql = sprintf(
  "INSERT INTO %s (%s) values (%s)",
  "profil",
  implode(", ", array_keys($komen)),
  ":" . implode(", :", array_keys($komen))
  );

  $statement = $connection->prepare($sql);
        $statement->execute($komen);
    } catch(PDOException $error) {
        echo $sql . "<br>" . $error->getMessage();
    }
}
?>


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio</title>
    <link rel="stylesheet" href="styles/styles.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css" integrity="sha512-1ycn6IcaQQ40/MKBW2W4Rhis/DbILU74C1vSrLJxCq57o941Ym01SwNsOMqvEBFlcgUa6xLiPY/NS5R+E6ztJQ==" crossorigin="anonymous" referrerpolicy="no-referrer" />
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800&display=swap" rel="stylesheet">
</head>
<body class="main-content">
    <header class="container header active" id="home">
        <div class="header-content">
            <div class="left-header">
                <div class="h-shape"></div>
                <div class="image">
                    <img src="img/hero.png" alt="">
                </div>
            </div>
            <div class="right-header">
                <h1 class="name">
                    Hallo, Saya <span>Ridha Nurrachmat.</span>
                </h1>
                <p>
                    Saya seorang mahasiswa yang menempuh perkuliahan di Universitas 
                    AMIKOM dengan prodi Teknik Komputer. 
                    Saya memiliki pengetahuan dalam bidang pengembangan berbasis web, mmencakup 
                    pengembangan front-end menggunakan HTML, CSS, dan JavaScript. 
                    Serta sedikit keahlian dalam penggunaan back-end seperti PHP 
                    dan memiliki pengalaman dengan basis 
                    data menggunakan MySQL.
                </p>
                <div class="btn-con">
                    <a href="img/CV.png" download="CV.png" class="main-btn">
                        <span class="btn-text">Download CV</span>
                        <span class="btn-icon"><i class="fas fa-download"></i></span>
                    </a>
                </div>
                <?php if (isset($_POST['submit']) && $statement) { ?>
                    <blockquote><?php echo $_POST['nama']; ?> successfully added message.</blockquote>
                <?php } ?>
            </div>
        </div>
    </header>
    <main>
    <section class="container" id="portfolio">
            <div class="main-title">
                <h2>My <span>Portfolio</span><span class="bg-text">My Work</span></h2>
            </div>
            <p class="port-text">
                Here is some of my work that I've done in various programming languages.
            </p>
            <div class="portfolios">
                <div class="portfolio-item">
                    <div class="image">
                        <img src="img/port1.jpg" alt="">
                    </div>
                    <div class="hover-items">
                        <h3>Project Source</h3>
                        <div class="icons">
                            <a href="#" class="icon">
                                <i class="fab fa-github"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-behance"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-youtube"></i>
                            </a>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item">
                    <div class="image">
                        <img src="img/port2.jpg" alt="">
                    </div>
                    <div class="hover-items">
                        <h3>Project Source</h3>
                        <div class="icons">
                            <a href="#" class="icon">
                                <i class="fab fa-github"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-behance"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-youtube"></i>
                            </a>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item">
                    <div class="image">
                        <img src="img/port3.jpg" alt="">
                    </div>
                    <div class="hover-items">
                        <h3>Project Source</h3>
                        <div class="icons">
                            <a href="#" class="icon">
                                <i class="fab fa-github"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-behance"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-youtube"></i>
                            </a>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item">
                    <div class="image">
                        <img src="img/port4.jpg" alt="">
                    </div>
                    <div class="hover-items">
                        <h3>Project Source</h3>
                        <div class="icons">
                            <a href="#" class="icon">
                                <i class="fab fa-github"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-behance"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-youtube"></i>
                            </a>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item">
                    <div class="image">
                        <img src="img/port5.jpg" alt="">
                    </div>
                    <div class="hover-items">
                        <h3>Project Source</h3>
                        <div class="icons">
                            <a href="#" class="icon">
                                <i class="fab fa-github"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-behance"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-youtube"></i>
                            </a>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item">
                    <div class="image">
                        <img src="img/port2.jpg" alt="">
                    </div>
                    <div class="hover-items">
                        <h3>Project Source</h3>
                        <div class="icons">
                            <a href="#" class="icon">
                                <i class="fab fa-github"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-behance"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-youtube"></i>
                            </a>
                        </div>
                    </div>
                </div>
                <div class="portfolio-item">
                    <div class="image">
                        <img src="img/port7.jpg" alt="">
                    </div>
                    <div class="hover-items">
                        <h3>Project Source</h3>
                        <div class="icons">
                            <a href="#" class="icon">
                                <i class="fab fa-github"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-behance"></i>
                            </a>
                            <a href="#" class="icon">
                                <i class="fab fa-youtube"></i>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        <section class="container contact" id="contact">
            <div class="contact-container">
                <div class="main-title">
                    <h2>Contact <span>Me</span><span class="bg-text">Contact</span></h2>
                </div>
                <div class="contact-content-con">
                    <div class="left-contact">
                        <h4>Contact me here</h4>
                        <p>
                            Hubungi dan kirimkan pesan kepada saya melalui contact person 
                            serta form pesan disamping :
                        </p>
                        <div class="contact-info">
                            <div class="contact-item">
                                <div class="icon">
                                    <i class="fas fa-map-marker-alt"></i>
                                    <span>Klaten, Jawa Tengah</span>
                                </div>
                            </div>
                            <div class="contact-item">
                                <div class="icon">
                                    <i class="fas fa-envelope"></i>
                                    <span>ridhanurrachmat@gmail.com</span>
                                </div>
                            </div>
                            <div class="contact-item">
                                <div class="icon">
                                    <i class="fas fa-user-graduate"></i>
                                    <span>Universitas AMIKOM Yogyakarta</span>
                                </div>
                               
                            </div>
                            <div class="contact-item">
                                <div class="icon">
                                    <i class="fas fa-phone"></i>
                                    <span>083862927534</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="right-contact">
                        <form method="post" class="contact-form">
                            <div class="input-control i-c-2">
                                <input type="text" required name='nama'  placeholder="YOUR NAME">
                                <input type="email" required name='email' placeholder="YOUR EMAIL">
                            </div>  
                            <div class="input-control">
                                <textarea name="subjek" id="" cols="15" rows="8" placeholder="Message Here..."></textarea>
                            </div>
                            <div class="btn-submit">
                                <!-- <button type="submit" class="btn">Submit</button> -->
                                <button type="submit" class="green-button" name="submit"><h3>Kirim</h3></button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <div class="controls">
        <div class="control active-btn" data-id="home" >
            <i class="fas fa-user"></i>
        </div>
        <div class="control" data-id="portfolio">
            <i class="fas fa-briefcase"></i>
        </div>
        <div class="control" data-id="contact">
            <i class="fas fa-envelope-open"></i>
        </div>
    </div>
    <div class="theme-btn">
        <i class="fas fa-adjust"></i>
    </div>
    <script src="app.js"></script>
</body>
</html>
```
Buat file app.js.
```
nano /var/www/html/app.js
```
Isi : 
```
(function () {
    [...document.querySelectorAll(".control")].forEach(button => {
        button.addEventListener("click", function() {
            document.querySelector(".active-btn").classList.remove("active-btn");
            this.classList.add("active-btn");
            document.querySelector(".active").classList.remove("active");
            document.getElementById(button.dataset.id).classList.add("active");
        })
    });
    document.querySelector(".theme-btn").addEventListener("click", () => {
        document.body.classList.toggle("light-mode");
    })
})();
```
Buat file common.php.
```
nano /var/www/html/common.php
```
Isi :
```
<?php

/**
 * Escapes HTML for output
 *
 */

function escape($html) {
        return htmlspecialchars($html, ENT_QUOTES | ENT_SUBSTITUTE, "UTF-8");
}
```
Buat file config.php untuk nantinya sebagai koneksi ke mysql.
```
nano /var/www/html/config.php
```
Isi :
```
<?php

/**
 * Escapes HTML for output
 *
 */

function escape($html) {
        return htmlspecialchars($html, ENT_QUOTES | ENT_SUBSTITUTE, "UTF-8");
}
```
Buat file sql untuk membuat database dab table pada direktori baru yaitu ini.sql.
```
mkdir /var/www/html/data
```
```
nano /var/www/html/data/init.sql
```
Isi : 
```
<?php

/**
 * Open a connection via PDO to create a
 * new database and table with structure.
 *
 */

require "config.php";

try {
	$connection = new PDO("mysql:host=$host", $username, $password, $options);
	$sql = file_get_contents("data/init.sql");
	$connection->exec($sql);
	
	echo "Database and table users created successfully.";
} catch(PDOException $error) {
	echo $sql . "<br>" . $error->getMessage();
}
```
Buat file install.php untuk memverifikasi bahwa database dan table berhasil di tambahkan.
```
nano /var/www/html/install.php
```
Isi :
```
<?php

/**
 * Open a connection via PDO to create a
 * new database and table with structure.
 *
 */

require "config.php";

try {
	$connection = new PDO("mysql:host=$host", $username, $password, $options);
	$sql = file_get_contents("data/init.sql");
	$connection->exec($sql);
	
	echo "Database and table users created successfully.";
} catch(PDOException $error) {
	echo $sql . "<br>" . $error->getMessage();
}
```
Tambahkan file direktori img dan styles pendukung index.php pada direktori github Assets diatas dengan winscp.
![](https://github.com/ridnrct/sysadminfp/blob/main/Assets/fp1.jpg)
Setelah itu pengujian dengan membuka web server dan kemudian kita cek apakah input data dalam database berhasil.
![](https://github.com/ridnrct/sysadminfp/blob/main/Assets/fp2.jpg)
![](https://github.com/ridnrct/sysadminfp/blob/main/Assets/fp3.jpg)
![](https://github.com/ridnrct/sysadminfp/blob/main/Assets/fp4.jpg)


