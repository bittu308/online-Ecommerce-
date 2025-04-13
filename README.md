<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Online E-Commerce Store</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header>
    <h1>Welcome to Our E-Commerce Store</h1>
    <div id="cart">
      <button id="cart-button">Cart (<span id="cart-count">0</span>)</button>
    </div>
  </header>
  
  <main>
    <section id="product-list">
      <div class="product-card">
        <img src="product1.jpg" alt="Product 1">
        <h3>Product 1</h3>
        <p>Price: $20</p>
        <button class="add-to-cart" data-product="Product 1" data-price="20">Add to Cart</button>
      </div>
      <div class="product-card">
        <img src="product2.jpg" alt="Product 2">
        <h3>Product 2</h3>
        <p>Price: $30</p>
        <button class="add-to-cart" data-product="Product 2" data-price="30">Add to Cart</button>
      </div>
      <!-- Add more product cards as needed -->
    </section>
  </main>
  
  <div id="cart-modal" class="modal">
    <div class="modal-content">
      <span id="close-button" class="close">&times;</span>
      <h2>Your Cart</h2>
      <ul id="cart-items">
        <!-- Cart items will appear here -->
      </ul>
      <p>Total: $<span id="total-price">0</span></p>
      <button id="checkout-button">Checkout</button>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>
<csss--></csss-->
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
}

header {
  background-color: #333;
  color: white;
  padding: 10px;
  text-align: center;
}

#cart {
  position: absolute;
  top: 10px;
  right: 10px;
}

#cart-button {
  background-color: #ff6600;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
}

#cart-button:hover {
  background-color: #ff9900;
}

#product-list {
  display: flex;
  justify-content: center;
  gap: 20px;
  padding: 20px;
}

.product-card {
  background-color: white;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  padding: 20px;
  text-align: center;
  width: 200px;
}

.product-card img {
  width: 100%;
  height: auto;
  border-radius: 5px;
}

.product-card button {
  background-color: #28a745;
  color: white;
  border: none;
  padding: 10px;
  cursor: pointer;
  border-radius: 5px;
  margin-top: 10px;
}

.product-card button:hover {
  background-color: #218838;
}

#cart-modal {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  justify-content: center;
  align-items: center;
}

.modal-content {
  background-color: white;
  padding: 20px;
  border-radius: 10px;
  width: 300px;
  text-align: center;
}

.close {
  position: absolute;
  top: 10px;
  right: 10px;
  font-size: 24px;
  cursor: pointer;
}

#checkout-button {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 10px 20px;
  margin-top: 20px;
  cursor: pointer;
}

#checkout-button:hover {
  background-color: #0056b3;
}
//javascript
let cart = [];
let cartCount = document.getElementById('cart-count');
let cartModal = document.getElementById('cart-modal');
let closeButton = document.getElementById('close-button');
let cartItemsList = document.getElementById('cart-items');
let totalPrice = document.getElementById('total-price');

// Add event listeners for 'Add to Cart' buttons
document.querySelectorAll('.add-to-cart').forEach(button => {
  button.addEventListener('click', function() {
    let product = this.getAttribute('data-product');
    let price = parseInt(this.getAttribute('data-price'));
    
    // Add product to cart
    cart.push({ product, price });
    updateCart();
  });
});

// Update cart display and total price
function updateCart() {
  let cartItemsHtml = '';
  let total = 0;

  cart.forEach(item => {
    cartItemsHtml += `<li>${item.product} - $${item.price}</li>`;
    total += item.price;
  });

  cartItemsList.innerHTML = cartItemsHtml;
  totalPrice.textContent = total;
  cartCount.textContent = cart.length;
}

// Show cart modal
document.getElementById('cart-button').addEventListener('click', function() {
  cartModal.style.display = 'flex';
});

// Close cart modal
closeButton.addEventListener('click', function() {
  cartModal.style.display = 'none';
});

// Checkout button
document.getElementById('checkout-button').addEventListener('click', function() {
  alert('Proceeding to checkout...');
  cart = [];  // Clear cart
  updateCart();  // Update cart display
});


