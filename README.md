<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BEBI & LEDI - Stitching Business Manager</title>
  <!-- FontAwesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  
  <style>
    :root {
      --primary-red: #8b0000;
      --secondary-blue: #004080;
      --success-green: #2e7d32;
      --bg-color: #f4f6f9;
      --card-bg: #ffffff;
      --text-color: #333333;
      --border-color: #e0e0e0;
    }

    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 0;
      background-color: var(--bg-color);
      color: var(--text-color);
    }

    /* Navigation Header */
    nav {
      background-color: var(--primary-red);
      padding: 12px 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: sticky;
      top: 0;
      z-index: 1000;
      box-shadow: 0 2px 8px rgba(0,0,0,0.2);
    }

    .nav-brand {
      color: white;
      font-size: 1.2rem;
      font-weight: bold;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .nav-links {
      display: flex;
      gap: 8px;
    }

    .nav-links button {
      background: rgba(255, 255, 255, 0.1);
      border: none;
      color: white;
      font-size: 0.95rem;
      cursor: pointer;
      padding: 8px 14px;
      border-radius: 6px;
      transition: all 0.3s ease;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .nav-links button.active, .nav-links button:hover {
      background-color: var(--secondary-blue);
    }

    /* Layout & Pages */
    .container {
      padding: 25px;
      max-width: 1250px;
      margin: 0 auto;
    }

    .page {
      display: none;
    }

    .page.active {
      display: block;
    }

    .section-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
      border-bottom: 2px solid var(--border-color);
      padding-bottom: 10px;
    }

    .section-header h2 {
      margin: 0;
      color: var(--secondary-blue);
      font-size: 1.5rem;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    /* Dashboard Metric Cards */
    .dashboard-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 18px;
      margin-bottom: 30px;
    }

    .card {
      background-color: var(--card-bg);
      padding: 18px;
      border-radius: 10px;
      box-shadow: 0 3px 6px rgba(0,0,0,0.06);
      display: flex;
      align-items: center;
      gap: 15px;
      border-left: 5px solid var(--secondary-blue);
    }

    .card.success { border-left-color: var(--success-green); }
    .card.danger { border-left-color: var(--primary-red); }

    .card i {
      font-size: 2.2rem;
      color: var(--secondary-blue);
    }
    .card.success i { color: var(--success-green); }
    .card.danger i { color: var(--primary-red); }

    .card-info h3 {
      margin: 0;
      font-size: 0.85rem;
      color: #666;
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }

    .card-info p {
      margin: 4px 0 0 0;
      font-size: 1.4rem;
      font-weight: bold;
    }

    /* Platform Badges */
    .badge-bebi {
      background-color: var(--primary-red);
      color: white;
      padding: 3px 8px;
      border-radius: 4px;
      font-size: 0.75rem;
      font-weight: bold;
    }

    .badge-ledi {
      background-color: var(--secondary-blue);
      color: white;
      padding: 3px 8px;
      border-radius: 4px;
      font-size: 0.75rem;
      font-weight: bold;
    }

    /* Forms */
    .form-container {
      background: white;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.05);
      margin-bottom: 25px;
    }

    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 15px;
    }

    .form-group {
      margin-bottom: 12px;
    }

    .form-group label {
      display: block;
      margin-bottom: 5px;
      font-weight: 600;
      font-size: 0.9rem;
    }

    .form-group input, .form-group select {
      width: 100%;
      padding: 9px 12px;
      border: 1px solid #ccc;
      border-radius: 5px;
      box-sizing: border-box;
      font-size: 0.95rem;
    }

    .btn {
      background-color: var(--secondary-blue);
      color: white;
      border: none;
      padding: 9px 16px;
      border-radius: 5px;
      cursor: pointer;
      font-size: 0.9rem;
      font-weight: 600;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      transition: background 0.2s;
    }

    .btn:hover { opacity: 0.9; }
    .btn-success { background-color: var(--success-green); }
    .btn-danger { background-color: var(--primary-red); }
    .btn-sm { padding: 5px 10px; font-size: 0.8rem; }

    /* Tables */
    .table-responsive {
      overflow-x: auto;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      background-color: var(--card-bg);
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 2px 6px rgba(0,0,0,0.05);
    }

    th, td {
      padding: 12px 14px;
      text-align: left;
      border-bottom: 1px solid var(--border-color);
      font-size: 0.9rem;
    }

    th {
      background-color: var(--secondary-blue);
      color: white;
      font-weight: 600;
    }

    .action-btns {
      display: flex;
      gap: 6px;
    }

    .hint {
      font-size: 0.8rem;
      color: #d9534f;
      margin-top: 4px;
    }

    /* Employee Card Grid Layout */
    .emp-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 20px;
      margin-top: 20px;
    }

    .emp-card {
      background: white;
      border-radius: 8px;
      padding: 18px;
      box-shadow: 0 3px 6px rgba(0,0,0,0.08);
      border-top: 4px solid var(--secondary-blue);
    }

    .emp-card-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 12px;
    }

    .emp-card-header h3 {
      margin: 0;
      font-size: 1.1rem;
      color: var(--text-color);
    }

    .emp-stat {
      display: flex;
      justify-content: space-between;
      padding: 6px 0;
      border-bottom: 1px dashed #eee;
      font-size: 0.9rem;
    }

    /* Modal */
    .modal {
      display: none;
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(0,0,0,0.5);
      justify-content: center;
      align-items: center;
      z-index: 2000;
    }

    .modal-content {
      background: white;
      padding: 22px;
      border-radius: 8px;
      width: 90%;
      max-width: 550px;
      max-height: 85vh;
      overflow-y: auto;
    }
  </style>
</head>
<body>

  <!-- Navigation Header -->
  <nav>
    <div class="nav-brand">
      <i class="fa-solid fa-scissors"></i> BEBI & LEDI Tailoring Manager
    </div>
    <div class="nav-links">
      <button onclick="showPage('dashboard')" class="active"><i class="fa-solid fa-gauge"></i> Dashboard</button>
      <button onclick="showPage('new-order')"><i class="fa-solid fa-plus-circle"></i> New Order</button>
      <button onclick="showPage('employees')"><i class="fa-solid fa-users"></i> Employees</button>
      <button onclick="showPage('completed')"><i class="fa-solid fa-circle-check"></i> Customers</button>
      <button onclick="showPage('analytics')"><i class="fa-solid fa-chart-bar"></i> Analytics</button>
    </div>
  </nav>

  <div class="container">

    <!-- 1. DASHBOARD PAGE -->
    <div id="dashboard" class="page active">
      <div class="section-header">
        <h2><i class="fa-solid fa-gauge"></i> Dashboard Overview</h2>
      </div>

      <div class="dashboard-grid">
        <div class="card">
          <i class="fa-solid fa-indian-rupee-sign"></i>
          <div class="card-info">
            <h3>Total Revenue</h3>
            <p id="dash-revenue">₹0</p>
          </div>
        </div>
        <div class="card success">
          <i class="fa-solid fa-store"></i>
          <div class="card-info">
            <h3>BEBI Revenue</h3>
            <p id="dash-bebi-rev">₹0</p>
          </div>
        </div>
        <div class="card">
          <i class="fa-solid fa-shop"></i>
          <div class="card-info">
            <h3>LEDI Revenue</h3>
            <p id="dash-ledi-rev">₹0</p>
          </div>
        </div>
        <div class="card success">
          <i class="fa-solid fa-chart-line"></i>
          <div class="card-info">
            <h3>Total Profit</h3>
            <p id="dash-profit">₹0</p>
          </div>
        </div>
        <div class="card danger">
          <i class="fa-solid fa-user-shield"></i>
          <div class="card-info">
            <h3>Owner Amount</h3>
            <p id="dash-owner">₹0</p>
          </div>
        </div>
        <div class="card">
          <i class="fa-solid fa-scissors"></i>
          <div class="card-info">
            <h3>Total Stitch Charges</h3>
            <p id="dash-stitch">₹0</p>
          </div>
        </div>
        <div class="card success">
          <i class="fa-solid fa-calendar-check"></i>
          <div class="card-info">
            <h3>Current Month Orders</h3>
            <p id="dash-month-orders">0</p>
          </div>
        </div>
      </div>

      <!-- Next Delivery Alert -->
      <div style="margin-bottom:25px;">
        <h3 style="margin-bottom:10px; font-size:1.1rem; color:var(--secondary-blue);"><i class="fa-solid fa-truck"></i> Next Upcoming Delivery</h3>
        <div id="next-delivery-card" class="card danger">
          <i class="fa-solid fa-clock"></i>
          <div class="card-info">
            <h3 id="next-cust-name" style="font-size:1.1rem; color:#333;">No pending deliveries</h3>
            <p id="next-cust-date" style="font-size:0.95rem; color:#666; font-weight:normal;"></p>
          </div>
        </div>
      </div>

      <!-- Active Orders Table -->
      <div class="section-header">
        <h2><i class="fa-solid fa-list-check"></i> Active Pending Orders</h2>
      </div>
      <div class="table-responsive">
        <table>
          <thead>
            <tr>
              <th>Platform</th>
              <th>Customer Name</th>
              <th>Phone</th>
              <th>Delivery Date</th>
              <th>Assigned To</th>
              <th>Price</th>
              <th>Advance</th>
              <th>Status Action</th>
              <th>Manage</th>
            </tr>
          </thead>
          <tbody id="active-orders-list"></tbody>
        </table>
      </div>
    </div>

    <!-- 2. NEW ORDER / EDIT ORDER PAGE -->
    <div id="new-order" class="page">
      <div class="section-header">
        <h2 id="order-form-title"><i class="fa-solid fa-cart-plus"></i> Register New Customer Order</h2>
      </div>

      <div class="form-container">
        <form id="order-form">
          <input type="hidden" id="edit-order-id">
          <div class="form-grid">
            <div class="form-group">
              <label><i class="fa-solid fa-building"></i> Business Platform</label>
              <select id="order-platform" required>
                <option value="BEBI">BEBI</option>
                <option value="LEDI">LEDI</option>
              </select>
            </div>
            <div class="form-group">
              <label><i class="fa-solid fa-user"></i> Customer Name</label>
              <input type="text" id="cust-name" placeholder="Enter customer name" required>
            </div>
            <div class="form-group">
              <label><i class="fa-brands fa-whatsapp"></i> WhatsApp Number</label>
              <input type="text" id="cust-phone" placeholder="e.g. 919876543210" required>
            </div>
            <div class="form-group">
              <label><i class="fa-solid fa-tag"></i> Order Price (₹)</label>
              <input type="number" id="order-price" oninput="calculateDetails()" placeholder="0" required>
            </div>
            <div class="form-group">
              <label><i class="fa-solid fa-wallet"></i> Advance Paid (₹)</label>
              <input type="number" id="order-advance" placeholder="Auto 50% or custom" required>
            </div>
            <div class="form-group">
              <label><i class="fa-solid fa-coins"></i> Total Additional Expenses (₹)</label>
              <input type="number" id="order-cost" oninput="calculateDetails()" value="0">
              <div id="adv-hint" class="hint"></div>
            </div>
            <div class="form-group">
              <label><i class="fa-solid fa-calendar"></i> Delivery Target Date</label>
              <input type="date" id="order-date" required>
            </div>
            <div class="form-group">
              <label><i class="fa-solid fa-user-ninja"></i> Assign Employee</label>
              <select id="order-employee" required></select>
            </div>
            <div class="form-group">
              <label><i class="fa-solid fa-scissors"></i> Employee Stitching Charge (₹)</label>
              <input type="number" id="stitch-charge" oninput="calculateDetails()" placeholder="0" required>
            </div>
            <div class="form-group">
              <label><i class="fa-solid fa-chart-line"></i> Calculated Profit (₹)</label>
              <input type="number" id="order-profit" readonly placeholder="Calculated automatically">
            </div>
          </div>

          <div style="margin-top:15px; display:flex; gap:10px;">
            <button type="submit" class="btn btn-success"><i class="fa-solid fa-floppy-disk"></i> Save Order Details</button>
            <button type="button" class="btn btn-danger" onclick="resetOrderForm()" style="display:none;" id="btn-cancel-edit">Cancel Edit</button>
          </div>
        </form>
      </div>
    </div>

    <!-- 3. EMPLOYEES PAGE -->
    <div id="employees" class="page">
      <div class="section-header">
        <h2><i class="fa-solid fa-users"></i> Employee Management</h2>
      </div>

      <div class="form-container">
        <form id="employee-form">
          <input type="hidden" id="edit-emp-id">
          <div class="form-grid">
            <div class="form-group">
              <label><i class="fa-solid fa-user"></i> Employee Name</label>
              <input type="text" id="emp-name" placeholder="Enter employee name" required>
            </div>
            <div class="form-group">
              <label><i class="fa-brands fa-whatsapp"></i> WhatsApp Number</label>
              <input type="text" id="emp-phone" placeholder="e.g. 919876543210" required>
            </div>
          </div>
          <div style="margin-top:10px; display:flex; gap:10px;">
            <button type="submit" class="btn"><i class="fa-solid fa-plus-circle"></i> Save Employee</button>
            <button type="button" class="btn btn-danger" onclick="resetEmployeeForm()" style="display:none;" id="btn-cancel-emp-edit">Cancel</button>
          </div>
        </form>
      </div>

      <h3><i class="fa-solid fa-user-gear"></i> Employee Performance Summaries</h3>
      <div id="employee-card-list" class="emp-grid"></div>
    </div>

    <!-- 4. CUSTOMERS & COMPLETED ORDERS PAGE -->
    <div id="completed" class="page">
      <div class="section-header">
        <h2><i class="fa-solid fa-circle-check"></i> Customer Directory & History</h2>
      </div>

      <div class="table-responsive">
        <table>
          <thead>
            <tr>
              <th>Customer Name</th>
              <th>Phone Number</th>
              <th>Total Orders Placed</th>
              <th>Actions</th>
            </tr>
          </thead>
          <tbody id="completed-customers-list"></tbody>
        </table>
      </div>
    </div>

    <!-- 5. MONTHLY ANALYTICS PAGE -->
    <div id="analytics" class="page">
      <div class="section-header">
        <h2><i class="fa-solid fa-chart-bar"></i> Monthly Business Financial Report</h2>
      </div>

      <div class="form-group" style="max-width: 300px;">
        <label>Select Month & Year</label>
        <input type="month" id="analytics-month" onchange="renderAnalytics()">
      </div>

      <div class="dashboard-grid">
        <div class="card"><div class="card-info"><h3>Total Month Orders</h3><p id="m-orders">0</p></div></div>
        <div class="card success"><div class="card-info"><h3>Total Revenue</h3><p id="m-revenue">₹0</p></div></div>
        <div class="card"><div class="card-info"><h3>Total Profit</h3><p id="m-profit">₹0</p></div></div>
        <div class="card danger"><div class="card-info"><h3>Stitch Charges Paid</h3><p id="m-stitch">₹0</p></div></div>
        <div class="card danger"><div class="card-info"><h3>Owner Fixed Amount</h3><p id="m-owner">₹0</p></div></div>
      </div>
    </div>

  </div>

  <!-- Details Modal -->
  <div id="modal" class="modal">
    <div class="modal-content">
      <h3 id="modal-title" style="margin-top:0; color:var(--secondary-blue);">Customer Order History</h3>
      <div id="modal-body"></div>
      <div style="text-align:right; margin-top:20px;">
        <button class="btn btn-danger" onclick="closeModal()"><i class="fa-solid fa-xmark"></i> Close Window</button>
      </div>
    </div>
  </div>

  <!-- Firebase JavaScript SDKs -->
  <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-firestore.js"></script>

  <script>
    // --- FIREBASE CONFIGURATION ---
    // ഗൂഗിൾ ഫയർബേസ് കൺസോളിൽ നിന്നും ലഭിക്കുന്ന നിങ്ങളുടെ സ്വന്തം API Keys ഇവിടെ നൽകുക:
    const firebaseConfig = {
      apiKey: "YOUR_API_KEY",
      authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
      projectId: "YOUR_PROJECT_ID",
      storageBucket: "YOUR_PROJECT_ID.appspot.com",
      messagingSenderId: "YOUR_SENDER_ID",
      appId: "YOUR_APP_ID"
    };

    firebase.initializeApp(firebaseConfig);
    const db = firebase.firestore();

    // Default Initial Staff Data
    const defaultEmployees = [
      { name: "umma", phone: "918943887325" },
      { name: "ani mol", phone: "919995549582" },
      { name: "meema (v)", phone: "919745081002" },
      { name: "nusrah", phone: "917510702526" }
    ];

    let employees = [];
    let orders = [];

    // --- NAVIGATION ---
    function showPage(pageId) {
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
      document.querySelectorAll('nav button').forEach(b => b.classList.remove('active'));
      
      const targetBtn = Array.from(document.querySelectorAll('nav button')).find(
        btn => btn.getAttribute('onclick').includes(pageId)
      );
      if(targetBtn) targetBtn.classList.add('active');

      document.getElementById(pageId).classList.add('active');
      renderDashboard();
      if (pageId === 'employees') renderEmployeeCards();
    }

    // --- INITIALIZATION ---
    window.onload = function() {
      initEmployees();
      listenToOrders();
    };

    function initEmployees() {
      db.collection("employees").onSnapshot(snapshot => {
        if(snapshot.empty) {
          defaultEmployees.forEach(emp => db.collection("employees").add(emp));
        } else {
          employees = [];
          snapshot.forEach(doc => employees.push({id: doc.id, ...doc.data()}));
          renderEmployeeSelect();
          renderEmployeeCards();
        }
      });
    }

    function listenToOrders() {
      db.collection("orders").onSnapshot(snapshot => {
        orders = [];
        snapshot.forEach(doc => orders.push({id: doc.id, ...doc.data()}));
        renderDashboard();
        renderCompletedCustomers();
        renderEmployeeCards();
      });
    }

    // --- FORM CALCULATIONS ---
    function calculateDetails() {
      const price = parseFloat(document.getElementById('order-price').value) || 0;
      const advanceInput = document.getElementById('order-advance');
      
      if (price > 0 && !advanceInput.dataset.touched) {
        advanceInput.value = price / 2;
      }

      const advance = parseFloat(advanceInput.value) || 0;
      const cost = parseFloat(document.getElementById('order-cost').value) || 0;
      const stitch = parseFloat(document.getElementById('stitch-charge').value) || 0;
      const ownerAmount = 300;

      // Profit Calculation Formula
      const profit = price - (cost + stitch + ownerAmount);
      document.getElementById('order-profit').value = profit;

      const remainingAdv = advance - cost;
      const hint = document.getElementById('adv-hint');
      if (cost > 0) {
        hint.innerText = `Remaining Advance Balance: ₹${remainingAdv >= 0 ? remainingAdv : 0}`;
      } else {
        hint.innerText = '';
      }
    }

    document.getElementById('order-advance').addEventListener('focus', function() {
      this.dataset.touched = "true";
    });

    // --- WHATSAPP MESSAGING INTEGRATION ---
    function sendWhatsApp(phone, message) {
      let cleanPhone = phone.replace(/[^0-9]/g, '');
      if (cleanPhone.length === 10) {
        cleanPhone = '91' + cleanPhone;
      }
      const whatsappUrl = `https://api.whatsapp.com/send?phone=${cleanPhone}&text=${encodeURIComponent(message)}`;
      window.open(whatsappUrl, '_blank');
    }

    // --- ORDER WORKFLOW & ACTIONS ---
    document.getElementById('order-form').addEventListener('submit', function(e) {
      e.preventDefault();
      
      const editId = document.getElementById('edit-order-id').value;

      const orderData = {
        platform: document.getElementById('order-platform').value,
        customerName: document.getElementById('cust-name').value,
        phone: document.getElementById('cust-phone').value,
        price: parseFloat(document.getElementById('order-price').value) || 0,
        advance: parseFloat(document.getElementById('order-advance').value) || 0,
        cost: parseFloat(document.getElementById('order-cost').value) || 0,
        date: document.getElementById('order-date').value,
        employee: document.getElementById('order-employee').value,
        stitchCharge: parseFloat(document.getElementById('stitch-charge').value) || 0,
        profit: parseFloat(document.getElementById('order-profit').value) || 0,
        ownerAmount: 300,
        updatedAt: new Date().toISOString()
      };

      if (editId) {
        db.collection("orders").doc(editId).update(orderData).then(() => {
          alert("Order details updated successfully!");
          resetOrderForm();
          showPage('dashboard');
        });
      } else {
        orderData.status = 'ADVANCE_PENDING';
        orderData.createdAt = new Date().toISOString();

        db.collection("orders").add(orderData).then(() => {
          alert("New order saved successfully!");
          resetOrderForm();
          showPage('dashboard');
        });
      }
    });

    function editOrder(orderId) {
      const o = orders.find(item => item.id === orderId);
      if (!o) return;

      document.getElementById('edit-order-id').value = o.id;
      document.getElementById('order-platform').value = o.platform || 'BEBI';
      document.getElementById('cust-name').value = o.customerName;
      document.getElementById('cust-phone').value = o.phone;
      document.getElementById('order-price').value = o.price;
      document.getElementById('order-advance').value = o.advance;
      document.getElementById('order-cost').value = o.cost;
      document.getElementById('order-date').value = o.date;
      document.getElementById('order-employee').value = o.employee;
      document.getElementById('stitch-charge').value = o.stitchCharge;
      document.getElementById('order-profit').value = o.profit;

      document.getElementById('order-form-title').innerHTML = '<i class="fa-solid fa-pen-to-square"></i> Edit Order Details';
      document.getElementById('btn-cancel-edit').style.display = 'inline-flex';
      showPage('new-order');
    }

    function deleteOrder(orderId) {
      if (confirm("Are you sure you want to permanently delete this order?")) {
        db.collection("orders").doc(orderId).delete().then(() => {
          alert("Order deleted successfully.");
        });
      }
    }

    function resetOrderForm() {
      document.getElementById('edit-order-id').value = '';
      document.getElementById('order-form').reset();
      document.getElementById('order-advance').dataset.touched = "";
      document.getElementById('order-form-title').innerHTML = '<i class="fa-solid fa-cart-plus"></i> Register New Customer Order';
      document.getElementById('btn-cancel-edit').style.display = 'none';
      document.getElementById('adv-hint').innerText = '';
    }

    function processOrderStep(orderId) {
      const order = orders.find(o => o.id === orderId);
      const emp = employees.find(e => e.name === order.employee);

      if (order.status === 'ADVANCE_PENDING') {
        db.collection("orders").doc(orderId).update({ status: 'FULL_PAID' }).then(() => {
          sendWhatsApp(order.phone, `Dear ${order.customerName}, your advance payment of ₹${order.advance} for order [${order.platform}] has been received. Thank you!`);
        });
      
      } else if (order.status === 'FULL_PAID') {
        db.collection("orders").doc(orderId).update({ status: 'STITCH_PENDING' }).then(() => {
          sendWhatsApp(order.phone, `Dear ${order.customerName}, your order from [${order.platform}] is fully paid and delivered! Thank you for choosing us.`);
        });
      
      } else if (order.status === 'STITCH_PENDING') {
        db.collection("orders").doc(orderId).update({ status: 'FINISHED' }).then(() => {
          if (emp) {
            sendWhatsApp(emp.phone, `Hello ${emp.name}, your stitching charge payment of ₹${order.stitchCharge} for customer ${order.customerName} (${order.platform}) has been processed.`);
          }
        });
      }
    }

    // --- DASHBOARD RENDER ---
    function renderDashboard() {
      let totalRev = 0, bebiRev = 0, lediRev = 0, totalProfit = 0, totalOwner = 0, totalStitch = 0;
      const currentMonth = new Date().toISOString().substring(0, 7);
      let currentMonthOrdersCount = 0;

      const activeOrdersList = document.getElementById('active-orders-list');
      activeOrdersList.innerHTML = '';

      let activeOrders = orders.filter(o => o.status !== 'FINISHED');
      activeOrders.sort((a,b) => new Date(a.date) - new Date(b.date));

      if (activeOrders.length > 0) {
        document.getElementById('next-cust-name').innerText = `${activeOrders[0].customerName} (${activeOrders[0].platform || 'BEBI'})`;
        document.getElementById('next-cust-date').innerText = `Target Delivery: ${activeOrders[0].date} | Assigned: ${activeOrders[0].employee}`;
      } else {
        document.getElementById('next-cust-name').innerText = "No upcoming pending deliveries";
        document.getElementById('next-cust-date').innerText = "";
      }

      orders.forEach(o => {
        totalRev += o.price;
        if (o.platform === 'LEDI') lediRev += o.price;
        else bebiRev += o.price;

        totalProfit += o.profit;
        totalOwner += o.ownerAmount;
        totalStitch += o.stitchCharge;

        if (o.date.startsWith(currentMonth)) {
          currentMonthOrdersCount++;
        }
      });

      document.getElementById('dash-revenue').innerText = `₹${totalRev}`;
      document.getElementById('dash-bebi-rev').innerText = `₹${bebiRev}`;
      document.getElementById('dash-ledi-rev').innerText = `₹${lediRev}`;
      document.getElementById('dash-profit').innerText = `₹${totalProfit}`;
      document.getElementById('dash-owner').innerText = `₹${totalOwner}`;
      document.getElementById('dash-stitch').innerText = `₹${totalStitch}`;
      document.getElementById('dash-month-orders').innerText = currentMonthOrdersCount;

      activeOrders.forEach(o => {
        let btnText = "", btnClass = "";
        if (o.status === 'ADVANCE_PENDING') {
          btnText = '<i class="fa-solid fa-wallet"></i> Pay Advance'; btnClass = "btn btn-sm";
        } else if (o.status === 'FULL_PAID') {
          btnText = '<i class="fa-solid fa-money-check-dollar"></i> Mark Delivered'; btnClass = "btn btn-sm btn-success";
        } else if (o.status === 'STITCH_PENDING') {
          btnText = '<i class="fa-solid fa-scissors"></i> Stitch Charge Paid'; btnClass = "btn btn-sm btn-danger";
        }

        const badgeClass = o.platform === 'LEDI' ? 'badge-ledi' : 'badge-bebi';

        activeOrdersList.innerHTML += `
          <tr>
            <td><span class="${badgeClass}">${o.platform || 'BEBI'}</span></td>
            <td><b>${o.customerName}</b></td>
            <td>${o.phone}</td>
            <td>${o.date}</td>
            <td>${o.employee}</td>
            <td>₹${o.price}</td>
            <td>₹${o.advance}</td>
            <td><button class="${btnClass}" onclick="processOrderStep('${o.id}')">${btnText}</button></td>
            <td>
              <div class="action-btns">
                <button class="btn btn-sm" onclick="editOrder('${o.id}')" title="Edit"><i class="fa-solid fa-pen"></i></button>
                <button class="btn btn-sm btn-danger" onclick="deleteOrder('${o.id}')" title="Delete"><i class="fa-solid fa-trash"></i></button>
              </div>
            </td>
          </tr>
        `;
      });
    }

    // --- EMPLOYEE MANAGEMENT & CARDS RENDER ---
    function renderEmployeeSelect() {
      const select = document.getElementById('order-employee');
      select.innerHTML = '';
      employees.forEach(e => {
        select.innerHTML += `<option value="${e.name}">${e.name}</option>`;
      });
    }

    function renderEmployeeCards() {
      const list = document.getElementById('employee-card-list');
      if (!list) return;
      list.innerHTML = '';

      employees.forEach(e => {
        const empOrders = orders.filter(o => o.employee === e.name);
        const totalEmpOrdersCount = empOrders.length;
        const pendingCount = empOrders.filter(o => o.status !== 'FINISHED').length;

        // Total Stitch Charge Paid to Employee
        const paidStitchSum = empOrders
          .filter(o => o.status === 'FINISHED')
          .reduce((sum, o) => sum + (o.stitchCharge || 0), 0);

        list.innerHTML += `
          <div class="emp-card">
            <div class="emp-card-header">
              <h3><i class="fa-solid fa-user-gear"></i> ${e.name}</h3>
              <div class="action-btns">
                <button class="btn btn-sm" onclick="editEmployee('${e.id}')"><i class="fa-solid fa-pen"></i></button>
                <button class="btn btn-sm btn-danger" onclick="deleteEmployee('${e.id}')"><i class="fa-solid fa-trash"></i></button>
              </div>
            </div>
            <div class="emp-stat">
              <span>WhatsApp:</span>
              <strong>${e.phone}</strong>
            </div>
            <div class="emp-stat">
              <span>Lifetime Orders:</span>
              <strong>${totalEmpOrdersCount} Orders</strong>
            </div>
            <div class="emp-stat">
              <span>Pending Works:</span>
              <strong style="color:var(--primary-red);">${pendingCount} Active</strong>
            </div>
            <div class="emp-stat">
              <span>Total Paid Amount:</span>
              <strong style="color:var(--success-green); font-size:1.05rem;">₹${paidStitchSum}</strong>
            </div>
          </div>
        `;
      });
    }

    document.getElementById('employee-form').addEventListener('submit', function(e) {
      e.preventDefault();
      const editId = document.getElementById('edit-emp-id').value;
      const name = document.getElementById('emp-name').value;
      const phone = document.getElementById('emp-phone').value;

      if (editId) {
        db.collection("employees").doc(editId).update({ name, phone }).then(() => {
          alert("Employee details updated!");
          resetEmployeeForm();
        });
      } else {
        db.collection("employees").add({ name, phone }).then(() => {
          sendWhatsApp(phone, `Hello ${name}, welcome! You have been added as an employee in our Tailoring Management App.`);
          resetEmployeeForm();
        });
      }
    });

    function editEmployee(id) {
      const emp = employees.find(e => e.id === id);
      if (!emp) return;
      document.getElementById('edit-emp-id').value = emp.id;
      document.getElementById('emp-name').value = emp.name;
      document.getElementById('emp-phone').value = emp.phone;
      document.getElementById('btn-cancel-emp-edit').style.display = 'inline-flex';
    }

    function deleteEmployee(id) {
      if (confirm("Are you sure you want to remove this employee?")) {
        db.collection("employees").doc(id).delete().then(() => {
          alert("Employee deleted!");
        });
      }
    }

    function resetEmployeeForm() {
      document.getElementById('edit-emp-id').value = '';
      document.getElementById('employee-form').reset();
      document.getElementById('btn-cancel-emp-edit').style.display = 'none';
    }

    // --- COMPLETED CUSTOMERS PAGE ---
    function renderCompletedCustomers() {
      const list = document.getElementById('completed-customers-list');
      list.innerHTML = '';

      const customerMap = {};
      orders.forEach(o => {
        if (!customerMap[o.customerName]) {
          customerMap[o.customerName] = { phone: o.phone, orders: [] };
        }
        customerMap[o.customerName].orders.push(o);
      });

      for (let custName in customerMap) {
        const custData = customerMap[custName];
        list.innerHTML += `
          <tr>
            <td><b>${custName}</b></td>
            <td>${custData.phone}</td>
            <td>${custData.orders.length} Order(s)</td>
            <td>
              <button class="btn btn-sm" onclick="viewCustomerDetails('${custName}')">
                <i class="fa-solid fa-eye"></i> View History
              </button>
            </td>
          </tr>
        `;
      }
    }

    function viewCustomerDetails(custName) {
      const custOrders = orders.filter(o => o.customerName === custName);
      let html = `<div style="max-height:400px; overflow-y:auto;">`;
      
      custOrders.forEach((o, index) => {
        html += `
          <div style="background:#f9f9f9; padding:12px; border-radius:6px; margin-bottom:10px; border-left:4px solid var(--secondary-blue);">
            <strong>Order #${index + 1} [${o.platform || 'BEBI'}]</strong> - ${o.date}<br>
            Price: ₹${o.price} | Advance: ₹${o.advance} | Stitching Charge: ₹${o.stitchCharge}<br>
            Assigned Employee: <b>${o.employee}</b> | Status: <b>${o.status}</b><br>
            <div style="margin-top:8px;">
              <button class="btn btn-sm" onclick="closeModal(); editOrder('${o.id}');"><i class="fa-solid fa-pen"></i> Edit Order</button>
              <button class="btn btn-sm btn-danger" onclick="closeModal(); deleteOrder('${o.id}');"><i class="fa-solid fa-trash"></i> Delete</button>
            </div>
          </div>
        `;
      });
      html += `</div>`;
      
      document.getElementById('modal-title').innerText = `Order History: ${custName}`;
      document.getElementById('modal-body').innerHTML = html;
      document.getElementById('modal').style.display = 'flex';
    }

    function closeModal() {
      document.getElementById('modal').style.display = 'none';
    }

    // --- MONTHLY ANALYTICS ---
    function renderAnalytics() {
      const selectedMonth = document.getElementById('analytics-month').value;
      if (!selectedMonth) return;

      const filtered = orders.filter(o => o.date.startsWith(selectedMonth));

      let rev = 0, profit = 0, stitch = 0, owner = 0;
      filtered.forEach(o => {
        rev += o.price;
        profit += o.profit;
        stitch += o.stitchCharge;
        owner += o.ownerAmount;
      });

      document.getElementById('m-orders').innerText = filtered.length;
      document.getElementById('m-revenue').innerText = `₹${rev}`;
      document.getElementById('m-profit').innerText = `₹${profit}`;
      document.getElementById('m-stitch').innerText = `₹${stitch}`;
      document.getElementById('m-owner').innerText = `₹${owner}`;
    }
  </script>
</body>
</html>
