<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Food Bridge - Connecting Surplus to Hunger</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-slate-50 font-sans text-slate-800">

  <!-- Header / Navigation -->
  <header class="bg-emerald-600 text-white shadow-md sticky top-0 z-50">
    <div class="max-w-6xl mx-auto px-4 py-4 flex justify-between items-center">
      <div class="flex items-center space-x-2">
        <svg class="w-8 h-8 fill-current text-emerald-200" viewBox="0 0 24 24">
          <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
        </svg>
        <span class="text-2xl font-bold tracking-tight">Food Bridge</span>
      </div>
      <nav class="space-x-2">
        <button onclick="switchTab('donate')" id="tab-donate" class="px-4 py-2 rounded-lg bg-emerald-700 font-medium hover:bg-emerald-800 transition">Donate Food</button>
        <button onclick="switchTab('browse')" id="tab-browse" class="px-4 py-2 rounded-lg bg-emerald-600 font-medium hover:bg-emerald-700 transition">Available Food (NGO)</button>
      </nav>
    </div>
  </header>

  <main class="max-w-6xl mx-auto px-4 py-8">
    
    <!-- Hero Banner -->
    <section class="bg-emerald-100 border border-emerald-200 rounded-2xl p-6 mb-8 text-center sm:text-left sm:flex items-center justify-between">
      <div>
        <h1 class="text-2xl sm:text-3xl font-extrabold text-emerald-900 mb-2">Bridge the Gap Between Waste and Want</h1>
        <p class="text-emerald-700">List surplus food from events or restaurants, or claim available meals for shelters.</p>
      </div>
    </section>

    <!-- SECTION 1: Donate Food Form -->
    <section id="view-donate" class="bg-white rounded-xl shadow-sm border border-slate-200 p-6 max-w-2xl mx-auto">
      <h2 class="text-xl font-bold mb-4 text-slate-800 flex items-center gap-2">
        <span>🍲</span> Post a Food Donation
      </h2>
      <form id="donationForm" onsubmit="handleFormSubmit(event)" class="space-y-4">
        <div>
          <label class="block text-sm font-semibold text-slate-700 mb-1">Food Item Description *</label>
          <input type="text" id="foodTitle" required placeholder="e.g., 50 Packed Lunch Boxes (Rice & Curry)" class="w-full px-3 py-2 border rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none">
        </div>
        
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
          <div>
            <label class="block text-sm font-semibold text-slate-700 mb-1">Servings / Quantity *</label>
            <input type="text" id="quantity" required placeholder="e.g., 30 people / 10 kg" class="w-full px-3 py-2 border rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none">
          </div>
          <div>
            <label class="block text-sm font-semibold text-slate-700 mb-1">Food Type *</label>
            <select id="foodType" class="w-full px-3 py-2 border rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none">
              <option value="Cooked Meals">Cooked Meals</option>
              <option value="Packaged Foods">Packaged Foods</option>
              <option value="Raw Produce / Grocery">Raw Produce / Grocery</option>
              <option value="Bakery Goods">Bakery Goods</option>
            </select>
          </div>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
          <div>
            <label class="block text-sm font-semibold text-slate-700 mb-1">Pickup Location / Address *</label>
            <input type="text" id="location" required placeholder="e.g., Downtown Plaza, Gate 3" class="w-full px-3 py-2 border rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none">
          </div>
          <div>
            <label class="block text-sm font-semibold text-slate-700 mb-1">Expiry / Best Before *</label>
            <input type="text" id="expiry" required placeholder="e.g., Best before 9 PM today" class="w-full px-3 py-2 border rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none">
          </div>
        </div>

        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
          <div>
            <label class="block text-sm font-semibold text-slate-700 mb-1">Donor Name / Organization *</label>
            <input type="text" id="donorName" required placeholder="e.g., Green Catering Co." class="w-full px-3 py-2 border rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none">
          </div>
          <div>
            <label class="block text-sm font-semibold text-slate-700 mb-1">Contact Phone *</label>
            <input type="tel" id="contact" required placeholder="e.g., +1 555-0199" class="w-full px-3 py-2 border rounded-lg focus:ring-2 focus:ring-emerald-500 outline-none">
          </div>
        </div>

        <button type="submit" class="w-full bg-emerald-600 text-white font-bold py-3 rounded-lg hover:bg-emerald-700 transition shadow">
          Publish Donation Listing
        </button>
      </form>
    </section>

    <!-- SECTION 2: Browse Donations (NGO View) -->
    <section id="view-browse" class="hidden space-y-4">
      <div class="flex justify-between items-center mb-4">
        <h2 class="text-xl font-bold text-slate-800">Available Food Listings</h2>
        <button onclick="fetchDonations()" class="text-sm bg-slate-200 hover:bg-slate-300 px-3 py-1.5 rounded-md transition">↻ Refresh Listings</button>
      </div>

      <div id="listingsContainer" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
        <!-- Dynamic Cards Inserted Here via JS -->
      </div>
    </section>

  </main>

  <script>
    const API_URL = 'http://localhost:3000/api/donations';

    function switchTab(tab) {
      const donateView = document.getElementById('view-donate');
      const browseView = document.getElementById('view-browse');
      const tabDonate = document.getElementById('tab-donate');
      const tabBrowse = document.getElementById('tab-browse');

      if (tab === 'donate') {
        donateView.classList.remove('hidden');
        browseView.classList.add('hidden');
        tabDonate.classList.replace('bg-emerald-600', 'bg-emerald-700');
        tabBrowse.classList.replace('bg-emerald-700', 'bg-emerald-600');
      } else {
        donateView.classList.add('hidden');
        browseView.classList.remove('hidden');
        tabBrowse.classList.replace('bg-emerald-600', 'bg-emerald-700');
        tabDonate.classList.replace('bg-emerald-700', 'bg-emerald-600');
        fetchDonations();
      }
    }

    async function handleFormSubmit(event) {
      event.preventDefault();
      
      const payload = {
        title: document.getElementById('foodTitle').value,
        quantity: document.getElementById('quantity').value,
        type: document.getElementById('foodType').value,
        location: document.getElementById('location').value,
        expiry: document.getElementById('expiry').value,
        donorName: document.getElementById('donorName').value,
        contact: document.getElementById('contact').value
      };

      try {
        const res = await fetch(API_URL, {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(payload)
        });

        if (res.ok) {
          alert('Donation posted successfully!');
          document.getElementById('donationForm').reset();
          switchTab('browse');
        } else {
          alert('Failed to submit donation.');
        }
      } catch (err) {
        console.error(err);
        alert('Server connection error. Make sure server.js is running.');
      }
    }

    async function fetchDonations() {
      const container = document.getElementById('listingsContainer');
      container.innerHTML = '<p class="text-slate-500">Loading food listings...</p>';

      try {
        const res = await fetch(API_URL);
        const donations = await res.json();

        if (donations.length === 0) {
          container.innerHTML = '<p class="text-slate-500 col-span-full">No active food listings available right now.</p>';
          return;
        }

        container.innerHTML = donations.map(item => `
          <div class="bg-white border border-slate-200 rounded-xl p-5 shadow-sm hover:shadow-md transition flex flex-col justify-between">
            <div>
              <div class="flex justify-between items-start mb-2">
                <span class="text-xs font-bold uppercase tracking-wider bg-emerald-100 text-emerald-800 px-2.5 py-1 rounded-full">${item.type}</span>
                <span class="text-xs text-slate-400">${item.status === 'claimed' ? '🔒 Claimed' : '🟢 Available'}</span>
              </div>
              <h3 class="font-bold text-lg text-slate-800 mb-1">${item.title}</h3>
              <p class="text-sm text-slate-600 mb-3">📍 <strong>Location:</strong> ${item.location}</p>
              
              <div class="text-xs space-y-1 bg-slate-50 p-3 rounded-lg mb-4 text-slate-600">
                <p>📦 <strong>Quantity:</strong> ${item.quantity}</p>
                <p>⏳ <strong>Expiry:</strong> ${item.expiry}</p>
                <p>👤 <strong>Donor:</strong> ${item.donorName}</p>
              </div>
            </div>

            ${item.status === 'available' ? `
              <button onclick="claimDonation(${item.id})" class="w-full bg-slate-800 hover:bg-slate-900 text-white font-medium py-2 rounded-lg text-sm transition">
                Claim Food (${item.contact})
              </button>
            ` : `
              <button disabled class="w-full bg-slate-200 text-slate-500 font-medium py-2 rounded-lg text-sm cursor-not-allowed">
                Already Claimed
              </button>
            `}
          </div>
        `).join('');
      } catch (err) {
        console.error(err);
        container.innerHTML = '<p class="text-red-500">Failed to load listings. Please start the backend server.</p>';
      }
    }

    async function claimDonation(id) {
      try {
        const res = await fetch(`${API_URL}/${id}/claim`, { method: 'PATCH' });
        if (res.ok) {
          alert('Item claimed! Contact details are attached to the card.');
          fetchDonations();
        }
      } catch (err) {
        alert('Could not claim item.');
      }
    }
  </script>
</body>
</html>
