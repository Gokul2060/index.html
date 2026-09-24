index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>WanderGo Tours</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      background: #f5f8fc;
      color: #333;
    }

    /* Navigation */
    header {
      background: #0f766e;
      color: white;
      padding: 18px 8%;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .logo {
      font-size: 26px;
      font-weight: bold;
    }

    nav a {
      color: white;
      text-decoration: none;
      margin-left: 25px;
      font-size: 16px;
    }

    nav a:hover {
      color: #a7f3d0;
    }

    /* Hero Section */
    .hero {
      min-height: 450px;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      padding: 40px 20px;

      background:
        linear-gradient(rgba(0, 0, 0, 0.45), rgba(0, 0, 0, 0.45)),
        url("https://images.unsplash.com/photo-1507525428034-b723cf961d3e")
        center/cover;
    }

    .hero-content {
      color: white;
      max-width: 700px;
    }

    .hero h1 {
      font-size: 48px;
      margin-bottom: 15px;
    }

    .hero p {
      font-size: 19px;
      margin-bottom: 25px;
    }

    .btn {
      display: inline-block;
      background: #f59e0b;
      color: white;
      padding: 13px 28px;
      border-radius: 6px;
      text-decoration: none;
      font-weight: bold;
    }

    .btn:hover {
      background: #d97706;
    }

    /* Destinations */
    .destinations {
      padding: 60px 8%;
      text-align: center;
    }

    .destinations h2 {
      font-size: 32px;
      margin-bottom: 35px;
      color: #0f766e;
    }

    .cards {
      display: flex;
      justify-content: center;
      gap: 25px;
      flex-wrap: wrap;
    }

    .card {
      background: white;
      width: 280px;
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
      transition: 0.3s;
    }

    .card:hover {
      transform: translateY(-5px);
    }

    .card img {
      width: 100%;
      height: 180px;
      object-fit: cover;
    }

    .card-content {
      padding: 20px;
    }

    .card h3 {
      margin-bottom: 10px;
      color: #0f766e;
    }

    .card p {
      color: #666;
      line-height: 1.5;
    }

    /* Login Section */
    .login-section {
      min-height: 550px;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 50px 20px;
      background: #e6fffb;
    }

    .login-box {
      background: white;
      width: 380px;
      padding: 35px;
      border-radius: 12px;
      box-shadow: 0 8px 25px rgba(0,0,0,0.12);
    }

    .login-box h2 {
      text-align: center;
      color: #0f766e;
      margin-bottom: 10px;
    }

    .login-box .subtitle {
      text-align: center;
      color: #777;
      margin-bottom: 25px;
    }

    .input-group {
      margin-bottom: 18px;
    }

    .input-group label {
      display: block;
      margin-bottom: 7px;
      font-weight: bold;
    }

    .input-group input {
      width: 100%;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 15px;
      outline: none;
    }

    .input-group input:focus {
      border-color: #0f766e;
      box-shadow: 0 0 4px rgba(15,118,110,0.3);
    }

    .login-button {
      width: 100%;
      padding: 13px;
      border: none;
      border-radius: 6px;
      background: #0f766e;
      color: white;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
    }

    .login-button:hover {
      background: #115e59;
    }

    .forgot {
      display: block;
      text-align: right;
      margin: 10px 0 20px;
      color: #0f766e;
      text-decoration: none;
      font-size: 14px;
    }

    .signup {
      text-align: center;
      margin-top: 20px;
      color: #666;
    }

    .signup a {
      color: #0f766e;
      text-decoration: none;
      font-weight: bold;
    }

    /* Footer */
    footer {
      background: #134e4a;
      color: white;
      text-align: center;
      padding: 25px;
    }

    /* Responsive */
    @media (max-width: 600px) {
      header {
        flex-direction: column;
        gap: 15px;
      }

      nav a {
        margin: 0 8px;
      }

      .hero h1 {
        font-size: 35px;
      }

      .login-box {
        width: 100%;
        max-width: 380px;
      }
    }
  </style>
</head>

<body>

  <!-- Navigation -->
  <header>
    <div class="logo">🌍 WanderGo Tours</div>

    <nav>
      <a href="#home">Home</a>
      <a href="#destinations">Destinations</a>
      <a href="#login">Login</a>
    </nav>
  </header>


  <!-- Hero Section -->
  <section class="hero" id="home">
    <div class="hero-content">
      <h1>Explore the World With Us</h1>

      <p>
        Discover beautiful destinations, exciting adventures
        and unforgettable travel experiences.
      </p>

      <a href="#destinations" class="btn">Explore Tours</a>
    </div>
  </section>


  <!-- Destinations -->
  <section class="destinations" id="destinations">

    <h2>Popular Destinations</h2>

    <div class="cards">

      <div class="card">
        <img
          src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee"
          alt="Mountain destination">

        <div class="card-content">
          <h3>Mountain Escape</h3>
          <p>
            Enjoy peaceful mountains, fresh air and beautiful
            natural scenery.
          </p>
        </div>
      </div>


      <div class="card">
        <img
          src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e"
          alt="Beach destination">

        <div class="card-content">
          <h3>Tropical Beaches</h3>
          <p>
            Relax on beautiful beaches and enjoy an unforgettable
            tropical holiday.
          </p>
        </div>
      </div>


      <div class="card">
        <img
          src="https://images.unsplash.com/photo-1526772662000-3f88f10405ff"
          alt="City destination">

        <div class="card-content">
          <h3>City Adventures</h3>
          <p>
            Explore famous cities, local culture, food and
            exciting attractions.
          </p>
        </div>
      </div>

    </div>
  </section>


  <!-- Login Section -->
  <section class="login-section" id="login">

    <div class="login-box">

      <h2>Welcome Back!</h2>

      <p class="subtitle">
        Login to your WanderGo account
      </p>

      <form onsubmit="loginUser(event)">

        <div class="input-group">
          <label for="username">Username</label>

          <input
            type="text"
            id="username"
            placeholder="Enter your username"
            required>
        </div>


        <div class="input-group">
          <label for="password">Password</label>

          <input
            type="password"
            id="password"
            placeholder="Enter your password"
            required>
        </div>


        <a href="#" class="forgot">
          Forgot Password?
        </a>


        <button type="submit" class="login-button">
          Login
        </button>

      </form>


      <p class="signup">
        Don't have an account?
        <a href="#">Sign Up</a>
      </p>

    </div>

  </section>


  <!-- Footer -->
  <footer>
    <p>© 2026 WanderGo Tours | Travel • Explore • Discover</p>
  </footer>


  <!-- Login JavaScript -->
  <script>

    function loginUser(event) {

      event.preventDefault();

      const username =
        document.getElementById("username").value;

      const password =
        document.getElementById("password").value;

      if (username === "admin" && password === "1234") {

        alert("Login successful! Welcome to WanderGo Tours.");

      } else {

        alert("Invalid username or password.");

      }
    }

  </script>

</body>
</html>
```
