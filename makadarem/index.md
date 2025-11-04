<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Welcome to WizeWisdom Café</title>
  <style>
    body {
      font-family: "Poppins", sans-serif;
      background: #fafafa;
      text-align: center;
      padding: 60px 20px;
      color: #333;
    }
    h1 {
      color: #333;
      margin-bottom: 10px;
    }
    p {
      margin-bottom: 20px;
    }
    a.button {
      display: inline-block;
      margin-top: 20px;
      padding: 15px 30px;
      background: #4CAF50;
      color: white;
      text-decoration: none;
      border-radius: 8px;
      font-size: 18px;
      transition: background 0.3s;
    }
    a.button:hover {
      background: #43a047;
    }
    .preview-box {
      background: #fff;
      border: 1px solid #ddd;
      border-radius: 12px;
      max-width: 500px;
      margin: 30px auto;
      padding: 20px;
      box-shadow: 0 3px 8px rgba(0,0,0,0.05);
    }
    .gcash-box {
      background: #e8f5e9;
      border: 1px dashed #4CAF50;
      border-radius: 10px;
      padding: 15px;
      margin-top: 25px;
      font-size: 16px;
    }
    .gcash-number {
      font-weight: bold;
      color: #2e7d32;
      cursor: pointer;
    }
    .gcash-number:hover {
      text-decoration: underline;
    }
    .note {
      font-size: 13px;
      color: #666;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <h1>Welcome to WizeWisdom Café</h1>
  <p>Discover our delicious drinks and meals — order online below!</p>

  <a class="button" href="https://script.google.com/macros/s/AKfycbw8qrNZrv74c9RxVYVkiy9aaJjYl9CK_sGprkV3MjU06RLWWe9YQ9MroJ0e95xwgtYL/exec" target="_blank">
    🛒 Order Now
  </a>

  <div class="preview-box">
    <h2>🧾 Order Preview</h2>
    <p>
      After completing your order, you’ll receive an <b>Order Number</b> for tracking.
      Please make sure all details are correct before submitting.
    </p>
    <p>
      Payment can be made via <b>GCash</b> using the number below.
    </p>

    <div class="gcash-box">
      Send payment to:<br>
      <span class="gcash-number" id="gcashNumber">09178664404</span>
      <div class="note">(Tap to copy)</div>
    </div>
  </div>

  <script>
    // Copy GCash number
    const gcash = document.getElementById("gcashNumber");
    gcash.addEventListener("click", () => {
      navigator.clipboard.writeText(gcash.textContent).then(() => {
        const note = document.createElement("div");
        note.textContent = "✅ GCash number copied!";
        note.style.color = "#2e7d32";
        note.style.marginTop = "8px";
        note.style.fontSize = "14px";
        gcash.parentElement.appendChild(note);
        setTimeout(() => note.remove(), 2000);
      });
    });
  </script>
</body>
</html>
