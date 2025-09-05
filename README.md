<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Online Store</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background: #f5f5f5;
    }
    header {
      background: #333;
      color: #fff;
      padding: 1rem;
      text-align: center;
    }
    .container {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      margin: 20px;
    }
    .product {
      background: #fff;
      border: 1px solid #ddd;
      border-radius: 8px;
      width: 200px;
      margin: 10px;
      padding: 15px;
      text-align: center;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    .product img {
      width: 100%;
      height: 150px;
      object-fit: cover;
      border-radius: 5px;
    }
    button {
      margin-top: 10px;
      padding: 8px 12px;
      background: #28a745;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background: #218838;
    }
    #cart {
      background: #fff;
      padding: 15px;
      margin: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
  </style>
</head>
<body>

  <header>
    <h1>My Online Store 🛒</h1>
  </header>

  <div class="container" id="product-list">
    <div class="product">
      <img src="https://via.placeholder.com/200x150" alt="Product 1">
      <h3>Product 1</h3>
      <p>$10</p>
      <button onclick="addToCart('Product 1', 10)">Add to Cart</button>
    </div>
    <div class="product">
      <img src="https://via.placeholder.com/200x150" alt="Product 2">
      <h3>Product 2</h3>
      <p>$20</p>
      <button onclick="addToCart('Product 2', 20)">Add to Cart</button>
    </div>
    <div class="product">
      <img src="https://via.placeholder.com/200x150" alt="Product 3">
      <h3>Product 3</h3>
      <p>$15</p>
      <button onclick="addToCart('Product 3', 15)">Add to Cart</button>
    </div>
  </div>

  <div id="cart">
    <h2>Shopping Cart</h2>
    <ul id="cart-items"></ul>
    <p><strong>Total: $<span id="total">0</span></strong></p>
    <button onclick="checkout()">Checkout</button>
  </div>

  <script>
    let cart = [];
    let total = 0;

    function addToCart(product, price) {
      cart.push({ product, price });
      total += price;
      updateCart();
    }

    function updateCart() {
      const cartItems = document.getElementById("cart-items");
      cartItems.innerHTML = "";
      cart.forEach((item, index) => {
        const li = document.createElement("li");
        li.textContent = `${item.product} - $${item.price}`;
        const removeBtn = document.createElement("button");
        removeBtn.textContent = "Remove";
        removeBtn.style.marginLeft = "10px";
        removeBtn.onclick = () => removeFromCart(index);
        li.appendChild(removeBtn);
        cartItems.appendChild(li);
      });
      document.getElementById("total").textContent = total;
    }

    function removeFromCart(index) {
      total -= cart[index].price;
      cart.splice(index, 1);
      updateCart();
    }

    function checkout() {
      if (cart.length === 0) {
        alert("Your cart is empty!");
      } else {
        alert("Thank you for your purchase!");
        cart = [];
        total = 0;
        updateCart();
      }
    }
  </script>

</body>
</html>
