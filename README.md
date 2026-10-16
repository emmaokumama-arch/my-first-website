<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Livingston Power Solutions</title>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #f4f7fb;
    color: #172033;
}

header {
    background: #101d35;
    color: white;
    padding: 22px 15px;
    text-align: center;
}

header h1 {
    margin: 0;
    font-size: 28px;
}

header p {
    color: #ffca28;
}

nav {
    background: #17345c;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 8px;
    padding: 12px;
}

nav button {
    background: transparent;
    color: white;
    border: 1px solid #55749b;
    padding: 10px 13px;
    border-radius: 5px;
    cursor: pointer;
}

nav button:hover {
    background: #087f8c;
}

.container {
    max-width: 1100px;
    margin: auto;
    padding: 20px;
}

.hero {
    background: linear-gradient(120deg, #123c69, #087f8c);
    color: white;
    padding: 45px 20px;
    text-align: center;
    border-radius: 12px;
}

.hero h2 {
    font-size: 32px;
}

.button {
    background: #087f8c;
    color: white;
    border: none;
    padding: 11px 16px;
    border-radius: 5px;
    cursor: pointer;
    margin: 4px;
}

.button:hover {
    background: #065f67;
}

.secondary {
    background: #17345c;
}

.danger {
    background: #b42318;
}

input, select, textarea {
    width: 100%;
    padding: 11px;
    margin: 7px 0 14px;
    border: 1px solid #ccd5e0;
    border-radius: 5px;
    font-size: 15px;
}

label {
    font-weight: bold;
}

.products {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 18px;
}

.card {
    background: white;
    border-radius: 10px;
    padding: 18px;
    box-shadow: 0 3px 12px #00000010;
}

.card h3 {
    color: #17345c;
}

.price {
    font-size: 20px;
    font-weight: bold;
    color: #087f8c;
}

.badge {
    display: inline-block;
    padding: 5px 9px;
    border-radius: 12px;
    background: #e2f4ed;
    color: #146c43;
    font-size: 12px;
}

section {
    margin-bottom: 28px;
}

.panel {
    background: white;
    padding: 20px;
    border-radius: 10px;
    margin: 15px 0;
}

.order {
    border-left: 5px solid #087f8c;
    background: white;
    padding: 15px;
    margin: 12px 0;
    border-radius: 5px;
}

.hidden {
    display: none;
}

.notice {
    background: #fff4cc;
    padding: 12px;
    border-radius: 5px;
}

footer {
    background: #101d35;
    color: white;
    padding: 25px;
    text-align: center;
    margin-top: 35px;
}

footer a {
    color: #ffca28;
}

@media(max-width: 600px) {
    header h1 {
        font-size: 23px;
    }

    .hero h2 {
        font-size: 25px;
    }

    .container {
        padding: 12px;
    }
}
</style>
</head>

<body>

<header>
    <h1>⚡ LIVINGSTON POWER SOLUTIONS</h1>
    <p>Your Trusted Solar & Electrical Partner</p>
    <p>Powering Homes, Businesses and Industries</p>
</header>

<nav>
    <button onclick="showPage('home')">Home</button>
    <button onclick="showPage('shop')">Our Products</button>
    <button onclick="showPage('cart')">Cart (<span id="cartCount">0</span>)</button>
    <button onclick="showPage('account')">My Account</button>
    <button onclick="showPage('orders')">My Orders</button>
    <button onclick="showPage('admin')">Admin</button>
</nav>

<main class="container">

<!-- HOME PAGE -->
<section id="home">
    <div class="hero">
        <h2>Welcome to Livingston Power Solutions</h2>
        <p>Your one-stop shop for solar systems and electrical materials.</p>
        <p>Quality products. Reliable power. Professional service.</p>
        <button class="button" onclick="showPage('shop')">
            Explore Our Products
        </button>
    </div>

    <div class="panel">
        <h2>Our Services</h2>
        <p>☀️ Solar power system supply and installation</p>
        <p>🔋 Solar batteries and inverters</p>
        <p>⚡ Electrical wiring materials and accessories</p>
        <p>🏠 Domestic and commercial electrical installations</p>
        <p>🔧 Electrical maintenance and troubleshooting</p>
    </div>
</section>

<!-- SHOP PAGE -->
<section id="shop" class="hidden">
    <h2>Our Products and Systems</h2>

    <label for="category">Choose a category</label>

    <select id="category" onchange="renderProducts()">
        <option value="All">All Products</option>
        <option value="Solar">Solar Systems</option>
        <option value="Umeme">Umeme / Electrical Systems</option>
    </select>

    <div id="productList" class="products"></div>
</section>

<!-- CART PAGE -->
<section id="cart" class="hidden">
    <h2>🛒 Shopping Cart</h2>
    <div id="cartList"></div>
    <h3 id="cartTotal">Total: UGX 0</h3>

    <button class="button" onclick="showPage('shop')">
        Continue Shopping
    </button>

    <button class="button" onclick="showPage('checkout')">
        Proceed to Order
    </button>
</section>

<!-- CHECKOUT PAGE -->
<section id="checkout" class="hidden">
    <h2>Place Your Order</h2>

    <div class="notice">
        This starter version records a demonstration order in this browser.
        It does not process payments or transmit orders to the business owner.
    </div>

    <form id="checkoutForm">
        <label>Full Name</label>
        <input id="customerName" required>

        <label>Phone Number</label>
        <input id="customerPhone" type="tel" required>

        <label>Delivery Location</label>
        <input id="customerAddress" required>

        <label>Additional Instructions</label>
        <textarea id="customerNotes"></textarea>

        <button class="button" type="submit">
            Submit Order
        </button>
    </form>
</section>

<!-- ACCOUNT PAGE -->
<section id="account" class="hidden">
    <h2>👤 Customer Profile</h2>

    <div class="notice">
        This is a local demonstration profile, not a secure online account.
    </div>

    <form id="accountForm">
        <label>Your Name</label>
        <input id="profileName" required>

        <label>Your Phone Number</label>
        <input id="profilePhone" type="tel" required>

        <button class="button" type="submit">
            Save Profile
        </button>
    </form>

    <div id="profileDisplay" class="panel"></div>
</section>

<!-- CUSTOMER ORDERS -->
<section id="orders" class="hidden">
    <h2>📦 My Orders</h2>
    <div id="myOrders"></div>
</section>

<!-- ADMIN DASHBOARD -->
<section id="admin" class="hidden">
    <h2>📊 Business Order Dashboard</h2>

    <div class="notice">
        Demonstration only: the dashboard is not protected by secure
        administrator authentication. Do not use it for real customer data.
    </div>

    <button class="button" onclick="renderAdmin()">
        Refresh Dashboard
    </button>

    <div class="panel">
        <h3>Order Summary</h3>
        <div id="orderSummary"></div>
    </div>

    <label>Filter Orders</label>

    <select id="statusFilter" onchange="renderAdmin()">
        <option value="All">All Orders</option>
        <option value="Ongoing">Ongoing</option>
        <option value="Successful">Successful</option>
        <option value="Unsuccessful">Unsuccessful</option>
    </select>

    <div id="adminOrders"></div>
</section>

<!-- RATING PAGE -->
<section id="rating" class="hidden">
    <h2>⭐ Rate a Product</h2>

    <form id="ratingForm">
        <label>Select Product</label>
        <select id="ratingProduct"></select>

        <label>Your Rating</label>
        <select id="ratingStars">
            <option value="5">★★★★★ - Excellent</option>
            <option value="4">★★★★ - Very Good</option>
            <option value="3">★★★ - Good</option>
            <option value="2">★★ - Fair</option>
            <option value="1">★ - Poor</option>
        </select>

        <label>Your Review</label>
        <textarea id="ratingComment"
                  placeholder="Share your experience"></textarea>

        <button class="button" type="submit">
            Submit Rating
        </button>
    </form>
</section>

</main>

<footer>
    <h3>Livingston Power Solutions</h3>
    <p>Solar Systems | Electrical Systems | Installation</p>
    <p>For inquiries, contact our business by phone.</p>
    <p>&copy; 2026 Livingston Power Solutions</p>
</footer>

<script>
const products = [
    {
        id: 1,
        name: "Solar Panel",
        category: "Solar",
        price: 250000,
        description: "Solar panel for generating electricity."
    },
    {
        id: 2,
        name: "Solar Inverter",
        category: "Solar",
        price: 450000,
        description: "Inverter for a solar power system."
    },
    {
        id: 3,
        name: "Solar Battery",
        category: "Solar",
        price: 650000,
        description: "Battery for storing solar energy."
    },
    {
        id: 4,
        name: "Solar Charge Controller",
        category: "Solar",
        price: 120000,
        description: "Controller for managing battery charging."
    },
    {
        id: 5,
        name: "Electrical Cable",
        category: "Umeme",
        price: 80000,
        description: "Electrical cable. Confirm size and roll length."
    },
    {
        id: 6,
        name: "Circuit Breaker",
        category: "Umeme",
        price: 35000,
        description: "Circuit protection device. Confirm rating."
    },
    {
        id: 7,
        name: "Electrical Switch",
        category: "Umeme",
        price: 10000,
        description: "Wall switch for electrical installations."
    },
    {
        id: 8,
        name: "Double Socket",
        category: "Umeme",
        price: 18000,
        description: "Double electrical socket outlet."
    }
];

function load(key, fallback) {
    try {
        const value = localStorage.getItem(key);
        return value ? JSON.parse(value) : fallback;
    } catch (error) {
        return fallback;
    }
}

function save(key, value) {
    localStorage.setItem(key, JSON.stringify(value));
}

let cart = load("lpsCart", []);
let orders = load("lpsOrders", []);
let ratings = load("lpsRatings", []);
let profile = load("lpsProfile", {
    name: "",
    phone: ""
});

function money(amount) {
    return "UGX " + Number(amount).toLocaleString("en-UG");
}

function showPage(page) {
    document.querySelectorAll("main > section")
        .forEach(section => section.classList.add("hidden"));

    document.getElementById(page).classList.remove("hidden");

    if (page === "shop") renderProducts();
    if (page === "cart") renderCart();
    if (page === "account") renderProfile();
    if (page === "orders") renderMyOrders();
    if (page === "admin") renderAdmin();
    if (page === "rating") populateRatingProducts();

    window.scrollTo(0, 0);
}

function renderProducts() {
    const category = document.getElementById("category").value;

    const filtered = category === "All"
        ? products
        : products.filter(p => p.category === category);

    document.getElementById("productList").innerHTML =
        filtered.map(p => {
            const reviews = ratings.filter(r => r.productId === p.id);

            const average = reviews.length
                ? (reviews.reduce((sum, r) => sum + r.stars, 0)
                    / reviews.length).toFixed(1)
                : "No ratings";

            return `
                <div class="card">
                    <span class="badge">${p.category}</span>
                    <h3>${p.name}</h3>
                    <p>${p.description}</p>
                    <p class="price">${money(p.price)}</p>
                    <p>⭐ ${average} (${reviews.length} reviews)</p>

                    <button class="button"
                        onclick="addToCart(${p.id})">
                        Add to Cart
                    </button>

                    <button class="button secondary"
                        onclick="openRating(${p.id})">
                        Rate Product
                    </button>
                </div>
            `;
        }).join("");
}

function addToCart(id) {
    const product = products.find(p => p.id === id);
    const existing = cart.find(item => item.id === id);

    if (existing) {
        existing.quantity++;
    } else {
        cart.push({
            id: product.id,
            quantity: 1
        });
    }

    save("lpsCart", cart);
    updateCartCount();

    alert(product.name + " added to your cart.");
}

function updateCartCount() {
    document.getElementById("cartCount").textContent =
        cart.reduce((sum, item) => sum + item.quantity, 0);
}

function renderCart() {
    const list = document.getElementById("cartList");

    if (!cart.length) {
        list.innerHTML = "<p>Your cart is empty.</p>";
        document.getElementById("cartTotal").textContent =
            "Total: UGX 0";
        return;
    }

    list.innerHTML = cart.map(item => {
        const product = products.find(p => p.id === item.id);

        return `
            <div class="card">
                <h3>${product.name}</h3>
                <p>Price: ${money(product.price)}</p>
                <label>Quantity</label>

                <input type="number" min="1"
                    value="${item.quantity}"
                    onchange="changeQuantity(${item.id}, this.value)">

                <p>Subtotal:
                    ${money(product.price * item.quantity)}
                </p>

                <button class="button danger"
                    onclick="removeItem(${item.id})">
                    Remove
                </button>
            </div>
        `;
    }).join("");

    const total = cart.reduce((sum, item) => {
        return sum + products.find(p => p.id === item.id).price
            * item.quantity;
    }, 0);

    document.getElementById("cartTotal").textContent =
        "Total: " + money(total);
}

function changeQuantity(id, quantity) {
    const amount = Math.floor(Number(quantity));

    if (!Number.isFinite(amount) || amount < 1) {
        alert("Enter a quantity of at least 1.");
        renderCart();
        return;
    }

    cart.find(item => item.id === id).quantity = amount;
    save("lpsCart", cart);
    updateCartCount();
    renderCart();
}

function removeItem(id) {
    cart = cart.filter(item => item.id !== id);
    save("lpsCart", cart);
    updateCartCount();
    renderCart();
}

document.getElementById("checkoutForm").addEventListener(
    "submit", function(event) {
        event.preventDefault();

        if (!cart.length) {
            alert("Your cart is empty.");
            showPage("shop");
            return;
        }

        const name = document.getElementById("customerName").value.trim();
        const phone = document.getElementById("customerPhone").value.trim();
        const address = document.getElementById("customerAddress").value.trim();
        const notes = document.getElementById("customerNotes").value.trim();

        if (!name || !phone || !address) {
            alert("Please complete all required fields.");
            return;
        }

        const items = cart.map(item => {
            const p = products.find(product => product.id === item.id);

            return {
                id: p.id,
                name: p.name,
                price: p.price,
                quantity: item.quantity
            };
        });

        const total = items.reduce(
            (sum, item) => sum + item.price * item.quantity, 0
        );

        const order = {
            id: "LPS-" + Date.now(),
            name,
            phone,
            address,
            notes,
            items,
            total,
            status: "Ongoing",
            date: new Date().toLocaleString()
        };

        orders.push(order);
        save("lpsOrders", orders);

        profile = { name, phone };
        save("lpsProfile", profile);

        cart = [];
        save("lpsCart", cart);
        updateCartCount();

        alert("Demonstration order created: " + order.id);

        showPage("orders");
    }
);

function renderMyOrders() {
    const mine = orders.filter(order =>
        order.phone === profile.phone && profile.phone
    );

    if (!mine.length) {
        document.getElementById("myOrders").innerHTML =
            "<p>No orders found for your saved profile in this browser.</p>";
        return;
    }

    document.getElementById("myOrders").innerHTML = mine.map(order => `
        <div class="order">
            <h3>Order ${order.id}</h3>
            <p>Date: ${order.date}</p>
            <p>Status: <strong>${order.status}</strong></p>
            <p>Total: ${money(order.total)}</p>
            <p>Delivery: ${order.address}</p>
            <p>Products: ${order.items.map(item =>
                item.name + " x " + item.quantity
            ).join(", ")}</p>
        </div>
    `).join("");
}

function renderAdmin() {
    const statuses = ["Ongoing", "Successful", "Unsuccessful"];

    document.getElementById("orderSummary").innerHTML =
        statuses.map(status => `
            <p>${status}: ${
                orders.filter(o => o.status === status).length
            } orders</p>
        `).join("") + `
            <p>Total orders: ${orders.length}</p>
        `;

    const filter = document.getElementById("statusFilter").value;

    const filtered = filter === "All"
        ? orders
        : orders.filter(order => order.status === filter);

    if (!filtered.length) {
        document.getElementById("adminOrders").innerHTML =
            "<p>No orders found.</p>";
        return;
    }

    document.getElementById("adminOrders").innerHTML =
        filtered.map(order => `
            <div class="order">
                <h3>Order ${order.id}</h3>
                <p>Customer: ${escapeHTML(order.name)}</p>
                <p>Phone: ${escapeHTML(order.phone)}</p>
                <p>Address: ${escapeHTML(order.address)}</p>
                <p>Date: ${escapeHTML(order.date)}</p>
                <p>Total: ${money(order.total)}</p>
                <p>Status: <strong>${order.status}</strong></p>
                <p>Products: ${order.items.map(item =>
                    escapeHTML(item.name) + " x " + item.quantity
                ).join(", ")}</p>

                <label>Update Order Status</label>

                <select id="status-${order.id}">
                    <option ${order.status === "Ongoing" ? "selected" : ""}>
                        Ongoing
                    </option>
                    <option ${order.status === "Successful" ? "selected" : ""}>
                        Successful
                    </option>
                    <option ${order.status === "Unsuccessful" ? "selected" : ""}>
                        Unsuccessful
                    </option>
                </select>

                <button class="button"
                    onclick="updateStatus('${order.id}')">
                    Save Status
                </button>
            </div>
        `).join("");
}

function updateStatus(id) {
    const order = orders.find(o => o.id === id);
    const selected = document.getElementById("status-" + id).value;

    if (!["Ongoing", "Successful", "Unsuccessful"].includes(selected)) {
        alert("Invalid order status.");
        return;
    }

    order.status = selected;
    save("lpsOrders", orders);

    alert("Order status updated.");
    renderAdmin();
}

function renderProfile() {
    document.getElementById("profileName").value = profile.name;
    document.getElementById("profilePhone").value = profile.phone;

    document.getElementById("profileDisplay").innerHTML =
        `<p>Name: ${escapeHTML(profile.name)}</p>
         <p>Phone: ${escapeHTML(profile.phone)}</p>`;
}

document.getElementById("accountForm").addEventListener(
    "submit", function(event) {
        event.preventDefault();

        profile = {
            name: document.getElementById("profileName").value.trim(),
            phone: document.getElementById("profilePhone").value.trim()
        };

        save("lpsProfile", profile);
        renderProfile();

        alert("Profile saved in this browser.");
    }
);

function populateRatingProducts() {
    document.getElementById("ratingProduct").innerHTML =
        products.map(p =>
            <option value="${p.id}">${p.name}</option>
        ).join("");
}

function openRating(id) {
    showPage("rating");
    document.getElementById("ratingProduct").value = id;
}

document.getElementById("ratingForm").addEventListener(
    "submit", function(event) {
        event.preventDefault();

        const productId = Number(
            document.getElementById("ratingProduct").value
        );

        const stars = Number(
            document.getElementById("ratingStars").value
        );

        const comment = document.getElementById("ratingComment").value.trim();

        ratings.push({
            productId,
            stars,
            comment,
            date: new Date().toLocaleDateString()
        });

        save("lpsRatings", ratings);

        document.getElementById("ratingComment").value = "";

        alert("Thank you for rating our product!");
        showPage("shop");
    }
);

function escapeHTML(value) {
    return String(value ?? "").replace(/[&<>"']/g, char => ({
        "&": "&amp;",
        "<": "&lt;",
        ">": "&gt;",
        '"': "&quot;",
        "'": "&#39;"
    })[char]);
}

renderProducts();
renderProfile();
updateCartCount();
populateRatingProducts();
</script>

</body>
</html>
