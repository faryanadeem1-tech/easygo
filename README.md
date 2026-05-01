<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>EasyGo App</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 font-sans">

<!-- Header -->
<header class="bg-pink-600 text-white p-4 flex justify-between">
  <h1 class="text-2xl font-bold">EasyGo</h1>
  <div>
    <button onclick="showLogin()" class="bg-white text-pink-600 px-3 py-1 rounded">Login</button>
    <button onclick="showSignup()" class="bg-white text-pink-600 px-3 py-1 rounded">Sign Up</button>
  </div>
</header>

<!-- Auth Modal -->
<div id="authModal" class="hidden fixed inset-0 bg-black bg-opacity-50 flex justify-center items-center">
  <div class="bg-white p-6 rounded w-80">
    <h2 id="authTitle" class="text-xl font-bold mb-3">Login</h2>

    <input id="username" placeholder="Username" class="border p-2 w-full mb-2">
    <input id="password" type="password" placeholder="Password" class="border p-2 w-full mb-2">

    <button onclick="submitAuth()" class="bg-pink-600 text-white w-full py-2 rounded">Submit</button>
    <button onclick="closeModal()" class="mt-2 text-gray-500">Close</button>
  </div>
</div>

<!-- Main -->
<main class="p-6">

  <!-- Banner -->
  <div class="bg-pink-100 p-6 rounded mb-6">
    <h2 class="text-2xl font-bold">Free Delivery on First Order</h2>
    <p>Sign up now and enjoy EasyGo</p>
  </div>

  <!-- Restaurants -->
  <h2 class="text-xl font-bold mb-3">Restaurants</h2>
  <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
    <div class="bg-white p-4 rounded shadow">🍔 Burger House</div>
    <div class="bg-white p-4 rounded shadow">🍕 Pizza Point</div>
    <div class="bg-white p-4 rounded shadow">🍜 Asian Corner</div>
  </div>

</main>

<script>
let mode = "login";

function showLogin() {
  mode = "login";
  document.getElementById("authTitle").innerText = "Login";
  document.getElementById("authModal").classList.remove("hidden");
}

function showSignup() {
  mode = "signup";
  document.getElementById("authTitle").innerText = "Sign Up";
  document.getElementById("authModal").classList.remove("hidden");
}

function closeModal() {
  document.getElementById("authModal").classList.add("hidden");
}

function submitAuth() {
  const user = document.getElementById("username").value;
  const pass = document.getElementById("password").value;

  if (!user || !pass) {
    alert("Enter details");
    return;
  }

  if (mode === "signup") {
    localStorage.setItem("easygo_user", user);
    localStorage.setItem("easygo_pass", pass);
    alert("Signup successful!");
  } else {
    const savedUser = localStorage.getItem("easygo_user");
    const savedPass = localStorage.getItem("easygo_pass");

    if (user === savedUser && pass === savedPass) {
      alert("Login successful!");
    } else {
      alert("Invalid credentials");
    }
  }

  closeModal();
}
</script>

</body>
</html>
