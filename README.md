# jks-all-in-one
fresh and fast delivery service
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Online Grocery & Food Ordering</title>
<style>
  body {
    font-family: Arial, sans-serif;
    background: #f0f8ff;
    margin: 0; padding: 0;
  }
  header, nav, main, footer {
    padding: 10px 20px;
  }
  header {
    background: #87ceeb;
    color: white;
    font-size: 24px;
    font-weight: bold;
  }
  nav {
    background: #d3ecff;
    display: flex;
    gap: 15px;
  }
  nav button {
    background: #3498db;
    border: none;
    color: white;
    padding: 10px 15px;
    cursor: pointer;
    border-radius: 4px;
  }
  nav button:hover {
    background: #2471a3;
  }
  .grid-images {
    display: grid;
    grid-template-columns: repeat(auto-fill,minmax(150px,1fr));
    gap: 15px;
    margin-top: 15px;
  }
  .grid-images img {
    width: 100%;
    height: 100px;
    object-fit: cover;
    border-radius: 6px;
  }
  .folder-section {
    margin-top: 20px;
  }
  .folder-section h2 {
    margin-bottom: 5px;
  }
  .category-list {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }
  .category-list button {
    padding: 10px 12px;
    border: 1.5px solid #3498db;
    color: #3498db;
    background: white;
    cursor: pointer;
    border-radius: 4px;
  }
  .category-list button.active {
    background: #3498db;
    color: white;
  }
  form {
    margin-top: 20px;
    max-width: 400px;
  }
  form label {
    display: block;
    margin-top: 10px;
    font-weight: bold;
  }
  form input, form textarea {
    width: 100%;
    padding: 8px;
    margin-top: 4px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  form button {
    margin-top: 15px;
    padding: 10px 15px;
    background: #3498db;
    color: white;
    border: none;
    cursor: pointer;
    border-radius: 4px;
  }
  form button:hover {
    background: #2471a3;
  }
  .error-message {
    color: red;
    display: none;
  }
  footer {
    background: #87ceeb;
    color: white;
    text-align: center;
    padding: 8px;
    margin-top: 40px;
  }
  /* Camera video styling */
  #camera video {
    width: 100%;
    max-width: 400px;
    height: auto;
    border-radius: 6px;
    background: black;
  }
  /* Google Maps container */
  #map {
    width: 100%;
    height: 400px;
    border-radius: 6px;
    margin-top: 15px;
  }
</style>
</head>
<body>
<header>JKS Online Grocery & Food</header>
<nav>
  <button onclick="showPage('home')">Home</button>
  <button onclick="showPage('camera')">Camera</button>
  <button onclick="showPage('maps')">Google Maps</button>
  <button onclick="showPage('orders')">Orders</button>
</nav>

<main id="contentArea">
  <!-- Home page with 10 sample images -->
  <section id="home" class="page">
    <h1>Welcome to JKS Online Grocery & Food</h1>
    <p>Explore our categories and place your order via WhatsApp.</p>
    <div class="grid-images">
      <img src="https://source.unsplash.com/150x100/?groceries" alt="Grocery" />
      <img src="https://source.unsplash.com/150x100/?fruits" alt="Fruits" />
      <img src="https://source.unsplash.com/150x100/?vegetables" alt="Vegetables" />
      <img src="https://source.unsplash.com/150x100/?milk" alt="Milk" />
      <img src="https://source.unsplash.com/150x100/?meat" alt="Meat" />
      <img src="https://source.unsplash.com/150x100/?pizza" alt="Pizza" />
      <img src="https://source.unsplash.com/150x100/?ice-cream" alt="Ice Cream" />
      <img src="https://source.unsplash.com/150x100/?tiffin" alt="Tiffin" />
      <img src="https://source.unsplash.com/150x100/?flowers" alt="Flowers" />
      <img src="https://source.unsplash.com/150x100/?medicine" alt="Medicine" />
    </div>
    <div class="folder-section">
      <h2>Folders:</h2>
      <button onclick="openFolder('groceries')">Groceries</button>
      <button onclick="openFolder('food')">Food</button>
      <button onclick="openFolder('pharmacy')">Pharmacy</button>
    </div>
  </section>

  <!-- Groceries page -->
  <section id="groceries" class="page" style="display:none;">
    <h2>Groceries</h2>
    <div class="category-list">
      <button onclick="selectGroceriesCategory('milk')">Milk</button>
      <button onclick="selectGroceriesCategory('meat')">Meat</button>
      <button onclick="selectGroceriesCategory('fruits')">Fruits</button>
      <button onclick="selectGroceriesCategory('vegetables')">Vegetables</button>
      <button onclick="selectGroceriesCategory('flowers')">Flowers</button>
      <button onclick="selectGroceriesCategory('others')">Others</button>
    </div>
    <div id="groceries-category-content"></div>
    <button onclick="showPage('home')">Back to Home</button>
  </section>

  <!-- Food page -->
  <section id="food" class="page" style="display:none;">
    <h2>Food</h2>
    <div class="category-list">
      <button onclick="selectFoodCategory('biriyani')">Biriyani</button>
      <button onclick="selectFoodCategory('tiffins')">Tiffins</button>
      <button onclick="selectFoodCategory('icecream')">Ice Cream</button>
      <button onclick="selectFoodCategory('pizza')">Pizza</button>
      <button onclick="selectFoodCategory('burgers')">Burgers</button>
      <button onclick="selectFoodCategory('rolls')">Rolls</button>
    </div>
    <div id="food-category-content"></div>
    <button onclick="showPage('home')">Back to Home</button>
  </section>

  <!-- Pharmacy page -->
  <section id="pharmacy" class="page" style="display:none;">
    <h2>Pharmacy</h2>
    <div id="pharmacy-content"></div>
    <button onclick="showPage('home')">Back to Home</button>
  </section>

  <!-- Camera -->
  <section id="camera" class="page" style="display:none;">
    <h2>Camera Page</h2>
    <video id="video" autoplay muted playsinline></video>
    <button onclick="showPage('home')">Back to Home</button>
  </section>

  <!-- Google Maps -->
  <section id="maps" class="page" style="display:none;">
    <h2>Google Maps</h2>
    <div id="map"></div>
    <button onclick="showPage('home')">Back to Home</button>
  </section>

  <!-- Orders page -->
  <section id="orders" class="page" style="display:none;">
    <h2>Your Orders</h2>
    <p>No orders yet.</p>
    <button onclick="showPage('home')">Back to Home</button>
  </section>
</main>

<footer>
  Contact us: <a href="tel:+918977143043">+91 89771 43043</a> | WhatsApp: <a href="https://wa.me/918977143043" target="_blank">+91 89771 43043</a>
</footer>

<script>
  // Folder/page display control
  function showPage(pageId) {
    document.querySelectorAll('.page').forEach(p => p.style.display = 'none');
    document.getElementById(pageId).style.display = 'block';

    if(pageId === 'camera') {
      openCamera();
    }
    if(pageId === 'maps') {
      initMap();
    }
  }

  const groceriesCategories = {
    milk: {
      images: [
        'https://source.unsplash.com/300x200/?milk,bottle',
        'https://source.unsplash.com/300x200/?milk,carton',
        'https://source.unsplash.com/300x200/?milk,powder',
        'https://source.unsplash.com/300x200/?milk,glass',
        'https://source.unsplash.com/300x200/?milk,cream',
        'https://source.unsplash.com/300x200/?milk,buffalo',
        'https://source.unsplash.com/300x200/?milk,cow',
        'https://source.unsplash.com/300x200/?milk,food',
        'https://source.unsplash.com/300x200/?milk,dairy',
        'https://source.unsplash.com/300x200/?milk,yogurt',
      ]
    },
    meat: {
      images: [
        'https://source.unsplash.com/300x200/?meat',
        'https://source.unsplash.com/300x200/?chicken',
        'https://source.unsplash.com/300x200/?steak',
        'https://source.unsplash.com/300x200/?bbq',
        'https://source.unsplash.com/300x200/?meat,dish',
        'https://source.unsplash.com/300x200/?mutton',
        'https://source.unsplash.com/300x200/?lamb',
        'https://source.unsplash.com/300x200/?pork',
        'https://source.unsplash.com/300x200/?sausages',
        'https://source.unsplash.com/300x200/?meat,food',
      ]
    },
    fruits: {
      images: [
        'https://source.unsplash.com/300x200/?apple,fruit',
        'https://source.unsplash.com/300x200/?banana,fruit',
        'https://source.unsplash.com/300x200/?orange,fruit',
        'https://source.unsplash.com/300x200/?mango,fruit',
        'https://source.unsplash.com/300x200/?berry,fruit',
        'https://source.unsplash.com/300x200/?fruit,basket',
        'https://source.unsplash.com/300x200/?fruit,market',
        'https://source.unsplash.com/300x200/?fruit,food',
        'https://source.unsplash.com/300x200/?fruit,salad',
        'https://source.unsplash.com/300x200/?tropical,fruit',
      ]
    },
    vegetables: {
      images: [
        'https://source.unsplash.com/300x200/?vegetables',
        'https://source.unsplash.com/300x200/?carrot',
        'https://source.unsplash.com/300x200/?spinach',
        'https://source.unsplash.com/300x200/?cabbage',
        'https://source.unsplash.com/300x200/?tomato',
        'https://source.unsplash.com/300x200/?potato',
        'https://source.unsplash.com/300x200/?onion',
        'https://source.unsplash.com/300x200/?broccoli',
        'https://source.unsplash.com/300x200/?cucumber',
        'https://source.unsplash.com/300x200/?lettuce',
      ]
    },
    flowers: {
      images: [
        'https://source.unsplash.com/300x200/?flowers',
        'https://source.unsplash.com/300x200/?rose',
        'https://source.unsplash.com/300x200/?tulip',
        'https://source.unsplash.com/300x200/?lily',
        'https://source.unsplash.com/300x200/?marigold',
        'https://source.unsplash.com/300x200/?orchid',
        'https://source.unsplash.com/300x200/?daisy',
        'https://source.unsplash.com/300x200/?bouquet',
        'https://source.unsplash.com/300x200/?garden',
        'https://source.unsplash.com/300x200/?bloom',
      ]
    },
    others: {
      images: [
        'https://source.unsplash.com/300x200/?groceries',
        'https://source.unsplash.com/300x200/?snacks',
        'https://source.unsplash.com/300x200/?food',
        'https://source.unsplash.com/300x200/?bag',
        'https://source.unsplash.com/300x200/?package',
        'https://source.unsplash.com/300x200/?shopping',
        'https://source.unsplash.com/300x200/?basket',
        'https://source.unsplash.com/300x200/?market',
        'https://source.unsplash.com/300x200/?store',
        'https://source.unsplash.com/300x200/?storefront',
      ]
    },
  };

  const foodCategories = {
    biriyani: {
      images: [
        'https://source.unsplash.com/300x200/?biriyani',
        'https://source.unsplash.com/300x200/?biryani,dish',
        'https://source.unsplash.com/300x200/?indian,food',
        'https://source.unsplash.com/300x200/?rice,dish',
        'https://source.unsplash.com/300x200/?spices',
        'https://source.unsplash.com/300x200/?chicken,curry',
        'https://source.unsplash.com/300x200/?meat,food',
        'https://source.unsplash.com/300x200/?food,restaurant',
        'https://source.unsplash.com/300x200/?indian,spices',
        'https://source.unsplash.com/300x200/?plate',
      ]
    },
    tiffins: {
      images: [
        'https://source.unsplash.com/300x200/?tiffin',
        'https://source.unsplash.com/300x200/?south,indian,food',
        'https://source.unsplash.com/300x200/?dosa',
        'https://source.unsplash.com/300x200/?idli',
        'https://source.unsplash.com/300x200/?uttapam',
        'https://source.unsplash.com/300x200/?upma',
        'https://source.unsplash.com/300x200/?chapati',
        'https://source.unsplash.com/300x200/?paratha',
        'https://source.unsplash.com/300x200/?sambar',
        'https://source.unsplash.com/300x200/?vada',
      ]
    },
    icecream: {
      images: [
        'https://source.unsplash.com/300x200/?icecream',
        'https://source.unsplash.com/300x200/?icecream,cone',
        'https://source.unsplash.com/300x200/?gelato',
        'https://source.unsplash.com/300x200/?dessert',
        'https://source.unsplash.com/300x200/?popsicle',
        'https://source.unsplash.com/300x200/?sweet',
        'https://source.unsplash.com/300x200/?cold,food',
        'https://source.unsplash.com/300x200/?ice,cream',
        'https://source.unsplash.com/300x200/?frozen',
        'https://source.unsplash.com/300x200/?sundae',
      ]
    },
    pizza: {
      images: [
        'https://source.unsplash.com/300x200/?pizza',
        'https://source.unsplash.com/300x200/?italian,food',
        'https://source.unsplash.com/300x200/?cheese,pizza',
        'https://source.unsplash.com/300x200/?pepperoni',
        'https://source.unsplash.com/300x200/?pizzeria',
        'https://source.unsplash.com/300x200/?fast-food',
        'https://source.unsplash.com/300x200/?slice',
        'https://source.unsplash.com/300x200/?dough',
        'https://source.unsplash.com/300x200/?crust',
        'https://source.unsplash.com/300x200/?delivery',
      ]
    },
    burgers: {
      images: [
        'https://source.unsplash.com/300x200/?burger',
        'https://source.unsplash.com/300x200/?fast-food',
        'https://source.unsplash.com/300x200/?cheeseburger',
        'https://source.unsplash.com/300x200/?fries',
        'https://source.unsplash.com/300x200/?sandwich',
        'https://source.unsplash.com/300x200/?classic,burger',
        'https://source.unsplash.com/300x200/?delicious-burger',
        'https://source.unsplash.com/300x200/?patty',
        'https://source.unsplash.com/300x200/?buns',
        'https://source.unsplash.com/300x200/?ketchup',
      ]
    },
    rolls: {
      images: [
        'https://source.unsplash.com/300x200/?rolls',
        'https://source.unsplash.com/300x200/?food,roll',
        'https://source.unsplash.com/300x200/?kebab',
        'https://source.unsplash.com/300x200/?wrap',
        'https://source.unsplash.com/300x200/?grill',
        'https://source.unsplash.com/300x200/?food',
        'https://source.unsplash.com/300x200/?recipe',
        'https://source.unsplash.com/300x200/?cuisine',
        'https://source.unsplash.com/300x200/?meal',
        'https://source.unsplash.com/300x200/?dinner',
      ]
    }
  };

  const pharmacyImages = [
    'https://source.unsplash.com/300x200/?medicine',
    'https://source.unsplash.com/300x200/?pharmacy',
    'https://source.unsplash.com/300x200/?health',
    'https://source.unsplash.com/300x200/?medicines',
    'https://source.unsplash.com/300x200/?drugstore',
    'https://source.unsplash.com/300x200/?healthcare',
    'https://source.unsplash.com/300x200/?pharmaceutical',
    'https://source.unsplash.com/300x200/?pharmacy,items',
    'https://source.unsplash.com/300x200/?health,products',
    'https://source.unsplash.com/300x200/?pharmaceuticals',
  ];

  function openFolder(folderName) {
    showPage(folderName);
    clearContent(folderName);
    if(folderName === 'groceries') {
      loadGroceriesCategories();
    } else if(folderName === 'food') {
      loadFoodCategories();
    } else if(folderName === 'pharmacy') {
      loadPharmacyContent();
    }
  }

  // Utility to clear content containers
  function clearContent(folderName) {
    if(folderName === 'groceries') {
      document.getElementById('groceries-category-content').innerHTML = '';
    } else if(folderName === 'food') {
      document.getElementById('food-category-content').innerHTML = '';
    } else if(folderName === 'pharmacy') {
      document.getElementById('pharmacy-content').innerHTML = '';
    }
  }

  // Load categories list on Groceries page
  function loadGroceriesCategories() {
    selectGroceriesCategory('milk');
  }

  // Display category content with images and order form for groceries
  function selectGroceriesCategory(category) {
    const container = document.getElementById('groceries-category-content');
    container.innerHTML = '';
    const catData = groceriesCategories[category];
    if (!catData) return;

    const imageGrid = document.createElement('div');
    imageGrid.className = 'grid-images';
    catData.images.forEach(url => {
      const img = document.createElement('img');
      img.src = url;
      imageGrid.appendChild(img);
    });
    container.appendChild(imageGrid);
    container.appendChild(createOrderForm(category));
  }

  // Load food categories list
  function loadFoodCategories() {
    selectFoodCategory('biriyani');
  }

  // Display food category content
  function selectFoodCategory(category) {
    const container = document.getElementById('food-category-content');
    container.innerHTML = '';
    const catData = foodCategories[category];
    if (!catData) return;

    const imageGrid = document.createElement('div');
    imageGrid.className = 'grid-images';
    catData.images.forEach(url => {
      const img = document.createElement('img');
      img.src = url;
      imageGrid.appendChild(img);
    });
    container.appendChild(imageGrid);
    container.appendChild(createOrderForm(category));
  }

  // Load pharmacy content with 10 images and order form
  function loadPharmacyContent() {
    const container = document.getElementById('pharmacy-content');
    container.innerHTML = '';
    const imageGrid = document.createElement('div');
    imageGrid.className = 'grid-images';
    pharmacyImages.forEach(url => {
      const img = document.createElement('img');
      img.src = url;
      imageGrid.appendChild(img);
    });
    container.appendChild(imageGrid);
    container.appendChild(createOrderForm('pharmacy'));
  }

  // Create order form element
  function createOrderForm(category) {
    const form = document.createElement('form');
    form.onsubmit = (e) => {
      e.preventDefault();
      submitOrder(form, category);
    };
    form.innerHTML = `
      <label for="name">Name:</label>
      <input type="text" id="name" name="name" required placeholder="Your name" />
      
      <label for="phone">Mobile Number:</label>
      <input type="tel" id="phone" name="phone" pattern="[6-9][0-9]{9}" maxlength="10" required placeholder="10-digit mobile number" />
      <span class="error-message">Please enter a valid 10-digit mobile number starting with 6-9.</span>

      <label for="orderItem">Order Item:</label>
      <textarea id="orderItem" name="orderItem" rows="2" required placeholder="Enter order details"></textarea>

      <label for="deliveryAddress">Delivery Address:</label>
      <textarea id="deliveryAddress" name="deliveryAddress" rows="2" required placeholder="Enter delivery address"></textarea>

      <button type="submit">Place Order via WhatsApp</button>
    `;
    const phoneInput = form.querySelector('#phone');
    const errorMsg = form.querySelector('.error-message');
    phoneInput.addEventListener('input', () => {
      if (phoneInput.validity.patternMismatch) {
        errorMsg.style.display = 'block';
      } else {
        errorMsg.style.display = 'none';
      }
    });
    return form;
  }

  // Handle form submission & open WhatsApp with order details
  function submitOrder(form, category) {
    const name = form.name.value.trim();
    const phone = form.phone.value.trim();
    const orderItem = form.orderItem.value.trim();
    const address = form.deliveryAddress.value.trim();

    if (!name || !phone || !orderItem || !address) {
      alert('Please fill all fields properly.');
      return;
    }
    const whatsappNumber = '918977143043';
    const message = encodeURIComponent(
      `Order from JKS Online Store\nCategory: ${category}\nName: ${name}\nMobile: ${phone}\nOrder: ${orderItem}\nDelivery Address: ${address}`
    );
    const whatsappUrl = `https://wa.me/${whatsappNumber}?text=${message}`;
    window.open(whatsappUrl, '_blank');
  }

  // Open camera and stream video
  function openCamera() {
    const video = document.getElementById('video');
    if (!navigator.mediaDevices || !navigator.mediaDevices.getUserMedia) {
      video.outerHTML = '<p>Camera not supported on this browser.</p>';
      return;
    }
    navigator.mediaDevices.getUserMedia({ video: true })
      .then(stream => {
        video.srcObject = stream;
      })
      .catch(error => {
        video.outerHTML = `<p>Unable to access camera: ${error.message}</p>`;
      });
  }

  // Initialize Google Map
  function initMap() {
    if (window.mapInitialized) return; // Prevent multiple inits
    window.mapInitialized = true;
    const centerCoords = { lat: 17.3850, lng: 78.4867 }; // Hyderabad coordinates
    const map = new google.maps.Map(document.getElementById('map'), {
      center: centerCoords,
      zoom: 12
    });
  }

  // Initialize with home page visible
  showPage('home');

</script>
<script async defer src="https://maps.googleapis.com/maps/api/js?key=YOUR_GOOGLE_MAPS_API_KEY"></script>

</body>
</html>
