<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UniTrip - Book Flights, Trains & Buses</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <style>
        body { font-family: 'Inter', system-ui, sans-serif; }
        .hero-bg {
            background: linear-gradient(rgba(0,0,0,0.7), rgba(0,0,0,0.8)), 
                        url('https://picsum.photos/id/1015/2000/1200') center/cover no-repeat;
        }
        .tab-active {
            border-bottom: 4px solid #2563eb;
            color: #2563eb;
            font-weight: 600;
        }
    </style>
</head>
<body class="bg-zinc-50">

    <!-- Navbar -->
    <nav class="bg-white shadow sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 bg-blue-600 text-white rounded-2xl flex items-center justify-center text-3xl font-bold">U</div>
                <h1 class="text-3xl font-bold">UniTrip</h1>
            </div>
            <div class="flex gap-8 font-medium">
                <a href="#" class="hover:text-blue-600">Flights</a>
                <a href="#" class="hover:text-blue-600">Trains</a>
                <a href="#" class="hover:text-blue-600">Buses</a>
            </div>
            <div>👤</div>
        </div>
    </nav>

    <!-- Hero -->
    <header class="hero-bg text-white py-24">
        <div class="max-w-5xl mx-auto px-6 text-center">
            <h1 class="text-5xl font-bold mb-3">One Website for All Transport</h1>
            <p class="text-xl mb-10">Flights • Trains • Buses • Book Easily</p>

            <!-- Tabs -->
            <div class="inline-flex bg-white/10 backdrop-blur rounded-3xl p-1 mb-8">
                <button onclick="switchTab(0)" id="tab0" class="tab-active px-8 py-3 rounded-3xl flex items-center gap-2">✈️ Flights</button>
                <button onclick="switchTab(1)" id="tab1" class="px-8 py-3 rounded-3xl flex items-center gap-2">🚄 Trains</button>
                <button onclick="switchTab(2)" id="tab2" class="px-8 py-3 rounded-3xl flex items-center gap-2">🚌 Buses</button>
            </div>

            <!-- Search Form -->
            <div class="bg-white text-zinc-900 rounded-3xl p-8 shadow-2xl max-w-4xl mx-auto">
                <div class="grid grid-cols-1 md:grid-cols-5 gap-4">
                    <div>
                        <label class="text-xs font-medium text-zinc-500">FROM</label>
                        <select id="from" class="w-full mt-1 bg-zinc-100 rounded-2xl px-5 py-4 focus:outline-none">
                            <option>Delhi (DEL)</option>
                            <option>Mumbai (BOM)</option>
                            <option>Bangalore (BLR)</option>
                        </select>
                    </div>
                    <div>
                        <label class="text-xs font-medium text-zinc-500">TO</label>
                        <select id="to" class="w-full mt-1 bg-zinc-100 rounded-2xl px-5 py-4 focus:outline-none">
                            <option>Mumbai (BOM)</option>
                            <option>Delhi (DEL)</option>
                            <option>Bangalore (BLR)</option>
                        </select>
                    </div>
                    <div>
                        <label class="text-xs font-medium text-zinc-500">DATE</label>
                        <input type="date" id="date" value="2026-07-10" class="w-full mt-1 bg-zinc-100 rounded-2xl px-5 py-4">
                    </div>
                    <div>
                        <label class="text-xs font-medium text-zinc-500">PASSENGERS</label>
                        <select id="passengers" class="w-full mt-1 bg-zinc-100 rounded-2xl px-5 py-4">
                            <option>1</option>
                            <option selected>2</option>
                            <option>3</option>
                        </select>
                    </div>
                    <div class="flex items-end">
                        <button onclick="searchTransport()" 
                                class="w-full bg-blue-600 hover:bg-blue-700 text-white font-semibold py-4 rounded-2xl">
                            SEARCH
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <!-- Results -->
    <div id="results" class="max-w-7xl mx-auto px-6 py-12 hidden">
        <button onclick="backToHome()" class="mb-6 text-blue-600 font-medium">← New Search</button>
        <h2 class="text-3xl font-semibold mb-8" id="resultTitle"></h2>
        <div id="resultsContainer" class="space-y-6"></div>
    </div>

    <!-- Booking Modal -->
    <div id="bookingModal" class="hidden fixed inset-0 bg-black/70 flex items-center justify-center z-50">
        <div class="bg-white rounded-3xl max-w-md w-full mx-4 p-8">
            <h3 class="text-2xl font-bold mb-6" id="modalTitle"></h3>
            <div id="modalDetails" class="space-y-4 mb-8"></div>
            <div class="flex gap-4">
                <button onclick="closeModal()" class="flex-1 py-4 border rounded-2xl">Cancel</button>
                <button onclick="confirmBooking()" class="flex-1 py-4 bg-green-600 text-white rounded-2xl">Pay Now</button>
            </div>
        </div>
    </div>

    <script>
        let currentTab = 0;

        function switchTab(n) {
            currentTab = n;
            document.querySelectorAll('#tab0,#tab1,#tab2').forEach((el,i) => {
                el.classList.toggle('tab-active', i === n);
            });
        }

        function searchTransport() {
            const from = document.getElementById('from').value;
            const to = document.getElementById('to').value;

            document.getElementById('results').classList.remove('hidden');
            document.querySelector('header').style.display = 'none';

            document.getElementById('resultTitle').innerHTML = 
                `${['Flights','Trains','Buses'][currentTab]} from <b>${from}</b> to <b>${to}</b>`;

            renderResults(from, to);
        }

        function renderResults(from, to) {
            const container = document.getElementById('resultsContainer');
            container.innerHTML = '';

            const mockData = currentTab === 0 ? [
                {name:"IndiGo", dep:"07:45", arr:"09:55", dur:"2h 10m", price:4299},
                {name:"Air India", dep:"11:00", arr:"13:20", dur:"2h 20m", price:5299}
            ] : currentTab === 1 ? [
                {name:"Rajdhani Express", dep:"16:55", arr:"22:10", dur:"5h 15m", price:1250}
            ] : [
                {name:"VRL Travels", dep:"21:00", arr:"05:30", dur:"8h 30m", price:899}
            ];

            mockData.forEach(item => {
                const div = document.createElement('div');
                div.className = "bg-white border rounded-3xl p-8 flex flex-col md:flex-row justify-between items-center gap-8 hover:shadow-xl transition";
                div.innerHTML = `
                    <div class="flex items-center gap-6">
                        <span class="text-5xl">${currentTab===0?'✈️':currentTab===1?'🚄':'🚌'}</span>
                        <div>
                            <p class="font-bold text-xl">${item.name}</p>
                            <p class="text-zinc-500">${item.dep} → ${item.arr}</p>
                        </div>
                    </div>
                    <div class="text-center">
                        <p class="text-sm text-zinc-500">${item.dur}</p>
                    </div>
                    <div class="text-right">
                        <p class="text-3xl font-bold text-emerald-600">₹${item.price}</p>
                        <button onclick="bookNow('${item.name}', ${item.price})" 
                                class="mt-4 px-10 py-3 bg-blue-600 text-white rounded-2xl hover:bg-blue-700">
                            Book Now
                        </button>
                    </div>
                `;
                container.appendChild(div);
            });
        }

        function bookNow(name, price) {
            document.getElementById('modalTitle').textContent = `Book ${name}`;
            document.getElementById('modalDetails').innerHTML = `
                <p><strong>Date:</strong> 10 July 2026</p>
                <p><strong>Passengers:</strong> 2</p>
                <p class="text-2xl font-bold mt-4">Total: ₹${price * 2}</p>
            `;
            document.getElementById('bookingModal').classList.remove('hidden');
        }

        function closeModal() {
            document.getElementById('bookingModal').classList.add('hidden');
        }

        function confirmBooking() {
            closeModal();
            alert("🎉 Booking Successful!\n\nTicket sent to your email.");
        }

        function backToHome() {
            document.getElementById('results').classList.add('hidden');
            document.querySelector('header').style.display = 'block';
        }

        // Initialize
        switchTab(0);
    </script>
</body>
</html>
