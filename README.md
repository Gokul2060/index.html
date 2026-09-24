```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Login</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #f4f6f8;
    }

    .login-container {
      width: 100%;
      max-width: 400px;
      padding: 20px;
    }

    .login-box {
      background: #ffffff;
      padding: 35px;
      border-radius: 12px;
      box-shadow: 0 8px 30px rgba(0, 0, 0, 0.08);
    }

    .login-box h2 {
      text-align: center;
      margin-bottom: 8px;
      color: #222;
    }

    .login-box .subtitle {
      text-align: center;
      color: #777;
      font-size: 14px;
      margin-bottom: 28px;
    }

    .form-group {
      margin-bottom: 18px;
    }

    .form-group label {
      display: block;
      margin-bottom: 7px;
      font-size: 14px;
      font-weight: 600;
      color: #333;
    }

    .form-group input {
      width: 100%;
      padding: 12px 14px;
      border: 1px solid #ddd;
      border-radius: 7px;
      font-size: 15px;
      outline: none;
      transition: 0.2s;
    }

    .form-group input:focus {
      border-color: #333;
      box-shadow: 0 0 0 3px rgba(0, 0, 0, 0.06);
    }

    .password-wrapper {
      position: relative;
    }

    .password-wrapper input {
      padding-right: 65px;
    }

    .show-password {
      position: absolute;
      right: 12px;
      top: 50%;
      transform: translateY(-50%);
      border: none;
      background: none;
      color: #555;
      cursor: pointer;
      font-size: 13px;
    }

    .login-button {
      width: 100%;
      padding: 13px;
      border: none;
      border-radius: 7px;
      background: #222;
      color: white;
      font-size: 15px;
      font-weight: 600;
      cursor: pointer;
      transition: 0.2s;
    }

    .login-button:hover {
      background: #000;
    }

    .login-button:active {
      transform: scale(0.98);
    }

    .message {
      margin-top: 15px;
      text-align: center;
      font-size: 14px;
      display: none;
    }

    .message.error {
      color: #d93025;
    }

    .message.success {
      color: #188038;
    }
  </style>
</head>

<body>

  <div class="login-container">
    <div class="login-box">

      <h2>Welcome Back</h2>
      <p class="subtitle">Please login to your account</p>

      <form id="loginForm">

        <div class="form-group">
          <label for="username">Username</label>
          <input
            type="text"
            id="username"
            placeholder="Enter your username"
            autocomplete="username"
          >
        </div>

        <div class="form-group">
          <label for="password">Password</label>

          <div class="password-wrapper">
            <input
              type="password"
              id="password"
              placeholder="Enter your password"
              autocomplete="current-password"
            >

            <button
              type="button"
              class="show-password"
              id="togglePassword"
            >
              Show
            </button>
          </div>
        </div>

        <button type="submit" class="login-button">
          Login
        </button>

        <div id="message" class="message"></div>

      </form>

    </div>
  </div>

  <script>
    const loginForm = document.getElementById("loginForm");
    const username = document.getElementById("username");
    const password = document.getElementById("password");
    const message = document.getElementById("message");
    const togglePassword = document.getElementById("togglePassword");

    // Show / Hide password
    togglePassword.addEventListener("click", () => {
      if (password.type === "password") {
        password.type = "text";
        togglePassword.textContent = "Hide";
      } else {
        password.type = "password";
        togglePassword.textContent = "Show";
      }
    });

    // Login validation
    loginForm.addEventListener("submit", (event) => {
      event.preventDefault();

      const usernameValue = username.value.trim();
      const passwordValue = password.value.trim();

      message.style.display = "block";

      if (!usernameValue || !passwordValue) {
        message.textContent = "Please enter username and password.";
        message.className = "message error";
        return;
      }

      // Demo login
      if (usernameValue === "admin" && passwordValue === "1234") {
        message.textContent = "Login successful!";
        message.className = "message success";
      } else {
        message.textContent = "Invalid username or password.";
        message.className = "message error";
      }
    });
  </script>

</body>
</html>
```
