<?php 
if (session_status() === PHP_SESSION_NONE) {
    session_start();
}
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rolsa Technologies</title>
    <link rel="stylesheet" href="css/header.css">
</head>
<body>

<header>
    <div class="logo">
        <img src="images/logo.png" alt="Rolsa Logo">
    </div>

    <nav>
        <ul class="nav-links">
            <li><a href="home.php">Home</a></li>
            <li><a href="solar.php">Solar Panel</a></li>
            <li><a href="ev.php">EV</a></li>
            <li><a href="smart.php">Smart Home Energy</a></li>
        </ul>

        <div class="nav-icons">
            <!-- Font Size Dropdown -->
<div class="dropdown text-size-dropdown">
    <button aria-label="Text Size Options">
        <img src="images/Aa-icon.png" alt="Text Size Icon">
    </button>
    <div class="dropdown-content">
        <p class="dropdown-title">Font Size</p>
        <a href="#" onclick="setFontSize('12px')">Extra Small</a>
        <a href="#" onclick="setFontSize('14px')">Small</a>
        <a href="#" onclick="setFontSize('16px')">Medium</a>
        <a href="#" onclick="setFontSize('18px')">Large</a>
        <a href="#" onclick="setFontSize('20px')">Extra Large</a>
    </div>
</div>

            <!-- Theme Mode Dropdown -->
            <div class="dropdown mode-dropdown">
                <button aria-label="Mode Options">
                    <img src="images/mode-icon.png" alt="Mode Icon">
                </button>
                <div class="dropdown-content">
                <a href="#" onclick="setTheme('light')">Light</a>
                <a href="#" onclick="setTheme('dark')">Dark</a>
                </div>
            </div>

            <!-- Account Dropdown -->
            <div class="account-dropdown">
                <img src="images/account.png" alt="Account" class="account-icon">
                <ul class="account-dropdown-content">
                    <?php 
                    if (isset($_SESSION['first_name']) && isset($_SESSION['last_name'])) { 
                        echo "<li class='hello-user'>Hello, " . htmlspecialchars($_SESSION['first_name']) . " " . htmlspecialchars($_SESSION['last_name']) . "!</li>";
                        echo "<li><a href='profile.php'>Profile</a></li>";
                        echo "<li><a href='logout.php'>Log Out</a></li>";
                    } else { 
                        echo "<li><a href='login.php'>Log In</a></li>";
                        echo "<li><a href='signup.php'>Sign Up</a></li>";
                    } 
                    ?>
                </ul>
            </div>

           
        </div>
    </nav>
</header>

<script>
    function setFontSize(size) {
        document.documentElement.style.fontSize = size;
        localStorage.setItem('textSize', size);
    }

    function setTheme(theme) {
        document.body.setAttribute('data-theme', theme);
        localStorage.setItem('theme', theme);
    }

    document.addEventListener('DOMContentLoaded', () => {
        const savedSize = localStorage.getItem('textSize') ;
        setFontSize(savedSize);

        const savedTheme = localStorage.getItem('theme') ;
        setTheme(savedTheme);
    });
</script>


body {
    background: url('../images/background.png') no-repeat center center;
    background-size: cover;
    margin: 0;
    font-family: Arial, sans-serif;
    color: #133B1E;
  }
  

  .hero {
    background: url('../images/hero-image.png') no-repeat center center;
    background-size: 100% auto;
    height: 500px;
    position: relative;
    width: 100%;
    
    
  }
  
  .hero::before {
    content: "";
    position: absolute;
    top: 0; left: 0;
    right: 0; bottom: 0;
    background-color: rgba(0, 0, 0, 0.5);
  }
  
  .hero-text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    color: #fff;
    z-index: 1;
    padding: 20px 40px;
  }
  
  .hero-text h1 {
    font-size: 3rem;
    margin-bottom: 10px;
  }
  
  .hero-text p {
    font-size: 1.4rem;
  }

  .services-heading {
    text-align: center;
    padding: 40px 20px 20px;
    background-color: #f1f7f2;
  }
  
  .services-heading h2 {
    font-size: 2.4rem;
    color: #133B1E;
    margin-bottom: 10px;
  }
  
  .services-heading p {
    font-size: 1.2rem;
    color: #3E2723;
  }
  
  .services {
    display: flex;
    justify-content: space-around;
    padding: 60px 40px;
    background-color: #ffffff;
    flex-wrap: wrap;
    gap: 30px;
  }
  
  .service-card {
    background-color: #f1f7f2;
    border-radius: 12px;
    padding: 25px;
    text-align: center;
    flex: 1 1 250px;
    max-width: 300px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    transition: transform 0.2s ease;
  }
  
  .service-card:hover {
    transform: translateY(-5px);
  }
  
  .service-card img {
    width: 250px;
  height: 250px;
    object-fit: contain;
    margin-bottom: 15px;
  }
  
  .service-card h3 {
    font-size: 20px;
    margin-bottom: 10px;
  }
  
  .service-card p {
    font-size: 14px;
    margin-bottom: 15px;
  }
  
  .learn-more {
    display: inline-block;
    background-color: #133B1E;
    color: white;
    padding: 10px 20px;
    border-radius: 8px;
    text-decoration: none;
    font-weight: bold;
    transition: background-color 0.3s ease;
  }
  
  .learn-more:hover {
    background-color: #A5D6A7;
    color: #133B1E;
  }
  
  .carbon-footprint {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #f9fbf9;
    padding: 60px 40px;
    gap: 40px;
    flex-wrap: wrap;
  }
  
  .carbon-image img {
    width: 100%;
    max-width: 400px;
    object-fit: contain;
    border-radius: 10px;
  }
  
  .carbon-text {
    max-width: 500px;
  }
  
  .carbon-text h2 {
    font-size: 28px;
    margin-bottom: 15px;
  }
  
  .carbon-text p {
    font-size: 16px;
    margin-bottom: 20px;
  }
  
  .cta-button {
    background-color: #133B1E;
    color: white;
    padding: 12px 25px;
    border: none;
    border-radius: 8px;
    font-weight: bold;
    text-decoration: none;
    transition: background-color 0.3s ease;
  }
  
  .cta-button:hover {
    background-color: #A5D6A7;
    color: #133B1E;
  }
