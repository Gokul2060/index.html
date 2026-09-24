# index.html
website
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Simple Website</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      background: #f4f4f4;
      color: #333;
    }

    header {
      background: #2563eb;
      color: white;
      padding: 20px;
      text-align: center;
    }

    nav {
      background: #1e40af;
      padding: 12px;
      text-align: center;
    }

    nav a {
      color: white;
      text-decoration: none;
      margin: 0 15px;
    }

    nav a:hover {
      text-decoration: underline;
    }

    .hero {
      text-align: center;
      padding: 80px 20px;
      background: white;
    }

    .hero h1 {
      font-size: 42px;
      margin-bottom: 15px;
    }

    .hero p {
      font-size: 18px;
      margin-bottom: 25px;
    }

    .button {
      display: inline-block;
      background: #2563eb;
      color: white;
      padding: 12px 25px;
      border-radius: 6px;
      text-decoration: none;
    }

    .button:hover {
      background: #1d4ed8;
    }

    .about {
      padding: 50px 20px;
      text-align: center;
    }

    .about h2 {
      margin-bottom: 15px;
    }

    footer {
      background: #222;
      color: white;
      text-align: center;
      padding: 20px;
      margin-top: 30px;
    }
  </style>
</head>

<body>

  <header>
    <h1>My Website</h1>
  </header>

  <nav>
    <a href="#">Home</a>
    <a href="#about">About</a>
    <a href="#contact">Contact</a>
  </nav>

  <section class="hero">
    <h1>Welcome to My Website</h1>
    <p>This is a simple website made with HTML and CSS.</p>
    <a href="#about" class="button">Learn More</a>
  </section>

  <section class="about" id="about">
    <h2>About Me</h2>
    <p>
      Hello! This is my first simple website.
      You can customize this section with your own information.
    </p>
  </section>

  <footer id="contact">
    <p>© 2026 My Website. All rights reserved.</p>
  </footer>

</body>
</html>
