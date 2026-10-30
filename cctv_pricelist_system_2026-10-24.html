<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CMOS Computers Anuradhapura - Inventory & Price Catalog</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <!-- Firebase SDKs -->
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>
    <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-database-compat.js"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: { sans: ['Plus Jakarta Sans', 'sans-serif'] },
                    colors: {
                        cyber: {
                            50: '#f0f9ff',
                            500: '#06b6d4',
                            600: '#0891b2',
                            700: '#0e7490',
                            dark: '#030712',
                            card: '#0f172a'
                        }
                    }
                }
            }
        }
    </script>
    <style>
        .glow-effect { box-shadow: 0 0 25px -5px rgba(14, 165, 233, 0.25); }
        .glass-card { background: rgba(15, 23, 42, 0.75); backdrop-filter: blur(12px); border: 1px solid rgba(255, 255, 255, 0.08); }
        .glass-card:hover { border-color: rgba(56, 189, 248, 0.4); transform: translateY(-3px); }
        .no-scrollbar::-webkit-scrollbar { display: none; }
        .no-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }
    </style>
</head>
<body class="bg-slate-950 text-slate-100 font-sans antialiased min-h-screen flex flex-col selection:bg-cyan-500 selection:text-slate-950">

    <!-- Glowing Top Info Bar -->
    <div class="bg-gradient-to-r from-slate-900 via-cyan-950 to-slate-900 border-b border-slate-800/80 text-xs py-2 px-4 sticky top-0 z-40">
        <div class="max-w-7xl mx-auto flex flex-col sm:flex-row justify-between items-center gap-2">
            <div class="flex items-center gap-2 text-cyan-400 font-medium">
                <i class="fa-solid fa-location-dot animate-bounce"></i>
                <span class="text-slate-200">New Bus Stand, Anuradhapura</span>
                <span class="hidden md:inline text-slate-600">|</span>
                <span class="hidden md:inline text-slate-400">CCTV & Computer Specialists</span>
            </div>
            <div class="flex items-center gap-4 text-slate-300">
                <a href="tel:0703182015" class="hover:text-cyan-400 transition flex items-center gap-1.5"><i class="fa-solid fa-phone text-emerald-400"></i> 070 318 2015</a>
                <a href="tel:0252228715" class="hover:text-cyan-400 transition flex items-center gap-1.5"><i class="fa-solid fa-phone text-emerald-400"></i> 025 222 8715</a>
                <div class="flex items-center gap-1.5 bg-slate-900/80 px-2.5 py-0.5 rounded-full border border-slate-700/60">
                    <span id="syncStatus" class="w-2 h-2 rounded-full bg-emerald-400 animate-ping"></span>
                    <span id="syncText" class="text-[11px] font-semibold text-emerald-400">Connecting...</span>
                </div>
            </div>
        </div>
    </div>

    <!-- Main Navigation Bar -->
    <header class="bg-slate-900/90 backdrop-blur-md border-b border-slate-800/80 sticky top-[33px] z-30">
        <div class="max-w-7xl mx-auto px-4 py-3.5 flex flex-wrap justify-between items-center gap-4">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-cyan-500 to-blue-600 flex items-center justify-center text-slate-950 font-black text-xl shadow-lg shadow-cyan-500/20">
                    <i class="fa-solid fa-bolt"></i>
                </div>
                <div>
                    <h1 class="text-xl font-extrabold text-white tracking-tight">CMOS <span class="text-cyan-400 font-light">COMPUTERS</span></h1>
                    <p class="text-[10px] text-slate-400 tracking-wider uppercase font-semibold">Anuradhapura • Tech & Security Solutions</p>
                </div>
            </div>

            <div class="flex items-center gap-3">
                <button id="modeToggleBtn" onclick="toggleAdminMode()" class="px-3.5 py-2 rounded-xl text-xs font-bold transition flex items-center gap-2 bg-slate-800/80 hover:bg-slate-800 text-slate-300 border border-slate-700">
                    <i id="modeIcon" class="fa-solid fa-shield-halved text-cyan-400"></i>
                    <span id="modeText">Customer View</span>
                </button>
                <button id="addProductBtn" onclick="openModal()" class="hidden px-4 py-2 rounded-xl text-xs font-bold bg-gradient-to-r from-cyan-500 to-blue-600 hover:from-cyan-400 hover:to-blue-500 text-slate-950 transition shadow-lg shadow-cyan-500/20 flex items-center gap-2">
                    <i class="fa-solid fa-plus-circle"></i> Add Item
                </button>
            </div>
        </div>
    </header>

    <!-- Search & Dynamic Filter Section -->
    <section class="bg-slate-900/40 border-b border-slate-800/60 py-5">
        <div class="max-w-7xl mx-auto px-4 space-y-4">
            <div class="relative">
                <i class="fa-solid fa-magnifying-glass absolute left-4 top-3.5 text-slate-500"></i>
                <input type="text" id="searchInput" oninput="filterProducts()" placeholder="Search Dahua, Hikvision, Ezviz, Laptops, SSDs, Monitors..." class="w-full pl-11 pr-4 py-3 bg-slate-900/90 border border-slate-800 rounded-2xl focus:outline-none focus:border-cyan-500/80 text-sm text-slate-200 placeholder-slate-500 transition shadow-inner">
            </div>

            <!-- Scrollable Category Badges -->
            <div class="flex items-center gap-2 overflow-x-auto pb-1 no-scrollbar" id="categoryChips">
                <button onclick="filterCategory('All')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-cyan-500 text-slate-950 transition shadow-md shadow-cyan-500/20">All Categories</button>
                <button onclick="filterCategory('Dahua')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition">Dahua</button>
                <button onclick="filterCategory('Hikvision')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition">Hikvision</button>
                <button onclick="filterCategory('Ezviz')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition">Ezviz</button>
                <button onclick="filterCategory('Tiandy')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition">Tiandy</button>
                <button onclick="filterCategory('Imou')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition">Imou</button>
                <button onclick="filterCategory('Chinese Cam')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition">Chinese Cam</button>
                <button onclick="filterCategory('Laptops & PCs')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition">Laptops & PCs</button>
                <button onclick="filterCategory('Monitors')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition">Monitors</button>
                <button onclick="filterCategory('Storage & SSD')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition">Storage & SSD</button>
                <button onclick="filterCategory('Networking')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition">Networking / 4G</button>
                <button onclick="filterCategory('Power & UPS')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition">Power & UPS</button>
                <button onclick="filterCategory('Accessories')" class="cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition">Accessories</button>
            </div>
        </div>
    </section>

    <!-- Product Grid Content -->
    <main class="max-w-7xl mx-auto px-4 py-8 flex-grow w-full">
        <div id="productGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
            <!-- Dynamic Items Injection -->
        </div>
        <div id="noProducts" class="hidden text-center py-20 text-slate-500">
            <i class="fa-solid fa-box-open text-5xl mb-3 text-slate-700"></i>
            <p class="font-medium text-slate-400">No inventory matches found.</p>
        </div>
    </main>

    <!-- Quick View Spec Modal -->
    <div id="quickViewModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-md z-50 hidden flex items-center justify-center p-4">
        <div class="bg-slate-900 border border-slate-800 rounded-3xl max-w-md w-full p-6 shadow-2xl relative">
            <button onclick="closeQuickView()" class="absolute top-4 right-4 text-slate-400 hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
            <div id="quickViewContent"></div>
        </div>
    </div>

    <!-- Admin Add/Edit Item Modal -->
    <div id="productModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-md z-50 hidden flex items-center justify-center p-4">
        <div class="bg-slate-900 border border-slate-800 rounded-3xl max-w-lg w-full p-6 shadow-2xl relative">
            <h2 id="modalTitle" class="text-lg font-extrabold text-white mb-4">Add Inventory Item</h2>
            <form id="productForm" onsubmit="saveProduct(event)" class="space-y-4">
                <input type="hidden" id="productId">
                <div>
                    <label class="block text-xs font-bold text-slate-400 mb-1">Product Title & Details</label>
                    <input type="text" id="formName" required placeholder="e.g., Dahua 2MP ColorVu Bullet Camera" class="w-full px-3.5 py-2.5 bg-slate-950 border border-slate-800 rounded-xl text-sm text-slate-200 focus:outline-none focus:border-cyan-500">
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-bold text-slate-400 mb-1">Category / Brand</label>
                        <select id="formCategory" class="w-full px-3.5 py-2.5 bg-slate-950 border border-slate-800 rounded-xl text-sm text-slate-200 focus:outline-none focus:border-cyan-500">
                            <option value="Dahua">Dahua</option>
                            <option value="Hikvision">Hikvision</option>
                            <option value="Ezviz">Ezviz</option>
                            <option value="Tiandy">Tiandy</option>
                            <option value="Imou">Imou</option>
                            <option value="Chinese Cam">Chinese Cam</option>
                            <option value="Laptops & PCs">Laptops & PCs</option>
                            <option value="Monitors">Monitors</option>
                            <option value="Storage & SSD">Storage & SSD</option>
                            <option value="Networking">Networking</option>
                            <option value="Power & UPS">Power & UPS</option>
                            <option value="Accessories">Accessories</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-xs font-bold text-slate-400 mb-1">Warranty Period</label>
                        <input type="text" id="formWarranty" required placeholder="e.g. 2 Years" class="w-full px-3.5 py-2.5 bg-slate-950 border border-slate-800 rounded-xl text-sm text-slate-200">
                    </div>
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-bold text-slate-400 mb-1">Retail Price (LKR)</label>
                        <input type="number" id="formRetail" required placeholder="5800" class="w-full px-3.5 py-2.5 bg-slate-950 border border-slate-800 rounded-xl text-sm text-slate-200">
                    </div>
                    <div>
                        <label class="block text-xs font-bold text-slate-400 mb-1">Wholesale Cost (LKR)</label>
                        <input type="number" id="formWholesale" required placeholder="4900" class="w-full px-3.5 py-2.5 bg-slate-950 border border-slate-800 rounded-xl text-sm text-slate-200">
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-bold text-slate-400 mb-1">Stock Availability</label>
                    <select id="formStock" class="w-full px-3.5 py-2.5 bg-slate-950 border border-slate-800 rounded-xl text-sm text-slate-200">
                        <option value="In Stock">In Stock</option>
                        <option value="Low Stock">Low Stock</option>
                        <option value="Out of Stock">Out of Stock</option>
                    </select>
                </div>
                <div class="flex justify-end gap-3 pt-3">
                    <button type="button" onclick="closeModal()" class="px-4 py-2 rounded-xl text-xs font-bold bg-slate-800 text-slate-300 hover:bg-slate-700">Cancel</button>
                    <button type="submit" class="px-5 py-2 rounded-xl text-xs font-bold bg-cyan-500 text-slate-950 hover:bg-cyan-400 shadow-md">Save Item</button>
                </div>
            </form>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-slate-900/60 border-t border-slate-800/80 py-8 text-center text-xs text-slate-500 mt-auto">
        <div class="max-w-7xl mx-auto px-4 space-y-2">
            <p class="font-semibold text-slate-400">CMOS Computers Anuradhapura</p>
            <p>New Bus Stand, Anuradhapura • Hotline: 070 318 2015 / 025 222 8715 / 071 318 2015</p>
            <p class="text-[10px] text-slate-600">© 2026 CMOS Computers. All Rights Reserved.</p>
        </div>
    </footer>

    <!-- Firebase Realtime Logic -->
    <script>
        // Configured Firebase project credentials
        const firebaseConfig = {
            apiKey: "AIzaSyAEb_VuIwhq16T9qC3ZV03rURQdQ3F-NV0",
            authDomain: "new-c-mos.firebaseapp.com",
            databaseURL: "https://new-c-mos-default-rtdb.asia-southeast1.firebasedatabase.app",
            projectId: "new-c-mos",
            storageBucket: "new-c-mos.firebasestorage.app",
            messagingSenderId: "949309834832",
            appId: "1:949309834832:web:d024cb37ce6fda7571b355",
            measurementId: "G-SZ3JR6MZ3F"
        };

        let dbRef = null;
        let isCloudActive = false;

        const defaultProducts = [
            { id: '1', name: 'Dahua 2MP Full-Color Bullet Camera', category: 'Dahua', retailPrice: 5800, wholesalePrice: 4900, warranty: '2 Years', stockStatus: 'In Stock' },
            { id: '2', name: 'Hikvision 2MP Audio Dome Camera', category: 'Hikvision', retailPrice: 5500, wholesalePrice: 4700, warranty: '2 Years', stockStatus: 'In Stock' },
            { id: '3', name: 'Ezviz C6N 1080p Wi-Fi PT Camera', category: 'Ezviz', retailPrice: 9500, wholesalePrice: 8200, warranty: '1 Year', stockStatus: 'In Stock' },
            { id: '4', name: 'Imou Ranger 2 1080p Smart Camera', category: 'Imou', retailPrice: 9200, wholesalePrice: 7900, warranty: '1 Year', stockStatus: 'In Stock' },
            { id: '5', name: 'Tiandy 2MP Starlight IP Camera', category: 'Tiandy', retailPrice: 6200, wholesalePrice: 5300, warranty: '2 Years', stockStatus: 'In Stock' },
            { id: '6', name: 'Standard 1080p Indoor Camera (Chinese)', category: 'Chinese Cam', retailPrice: 3800, wholesalePrice: 3100, warranty: '6 Months', stockStatus: 'In Stock' },
            { id: '7', name: 'DDR4 8GB 3200MHz Desktop RAM', category: 'Accessories', retailPrice: 7500, wholesalePrice: 6500, warranty: '3 Years', stockStatus: 'In Stock' },
            { id: '8', name: 'Hikvision 240GB SATA SSD', category: 'Storage & SSD', retailPrice: 6800, wholesalePrice: 5900, warranty: '3 Years', stockStatus: 'In Stock' }
        ];

        let products = [];
        let currentCategory = 'All';
        let isAdminMode = false;

        function initFirebase() {
            try {
                firebase.initializeApp(firebaseConfig);
                dbRef = firebase.database().ref('products');

                dbRef.on('value', (snapshot) => {
                    const data = snapshot.val();
                    if (data) {
                        products = Object.keys(data).map(key => ({ id: key, ...data[key] }));
                    } else {
                        defaultProducts.forEach(p => {
                            firebase.database().ref('products/' + p.id).set(p);
                        });
                        products = defaultProducts;
                    }
                    localStorage.setItem('cmos_products_v2', JSON.stringify(products));
                    isCloudActive = true;
                    updateSyncBadge(true, "Cloud Synced");
                    renderProducts();
                }, (error) => {
                    console.warn("Fallback to local memory:", error);
                    loadLocalStorage();
                });
            } catch (e) {
                console.warn("Firebase failed to load:", e);
                loadLocalStorage();
            }
        }

        function loadLocalStorage() {
            isCloudActive = false;
            updateSyncBadge(false, "Local Memory");
            products = JSON.parse(localStorage.getItem('cmos_products_v2')) || defaultProducts;
            renderProducts();
        }

        function updateSyncBadge(active, message) {
            const badge = document.getElementById('syncStatus');
            const text = document.getElementById('syncText');
            if (active) {
                badge.className = "w-2 h-2 rounded-full bg-emerald-400 animate-pulse";
                text.className = "text-[11px] font-semibold text-emerald-400";
            } else {
                badge.className = "w-2 h-2 rounded-full bg-amber-400";
                text.className = "text-[11px] font-semibold text-amber-400";
            }
            text.innerText = message;
        }

        function renderProducts() {
            const grid = document.getElementById('productGrid');
            const noProducts = document.getElementById('noProducts');
            const searchVal = document.getElementById('searchInput').value.toLowerCase();

            grid.innerHTML = '';

            const filtered = products.filter(item => {
                const matchesCat = currentCategory === 'All' || item.category === currentCategory;
                const matchesSearch = item.name.toLowerCase().includes(searchVal) || item.category.toLowerCase().includes(searchVal);
                return matchesCat && matchesSearch;
            });

            if (filtered.length === 0) {
                noProducts.classList.remove('hidden');
                return;
            } else {
                noProducts.classList.add('hidden');
            }

            filtered.forEach(item => {
                const stockColor = item.stockStatus === 'In Stock' 
                    ? 'bg-emerald-500/10 text-emerald-400 border-emerald-500/20' 
                    : item.stockStatus === 'Low Stock' 
                    ? 'bg-amber-500/10 text-amber-400 border-amber-500/20' 
                    : 'bg-rose-500/10 text-rose-400 border-rose-500/20';

                let adminHtml = '';
                if (isAdminMode) {
                    const margin = Number(item.retailPrice) - Number(item.wholesalePrice);
                    adminHtml = `
                        <div class="mt-3 pt-3 border-t border-slate-800 bg-slate-950/60 p-2.5 rounded-xl space-y-1">
                            <div class="flex justify-between items-center text-xs">
                                <span class="text-slate-400">Wholesale:</span>
                                <span class="font-bold text-slate-200">Rs. ${Number(item.wholesalePrice).toLocaleString()} LKR</span>
                            </div>
                            <div class="flex justify-between items-center text-[11px]">
                                <span class="text-slate-500">Margin:</span>
                                <span class="font-bold text-emerald-400">+Rs. ${Number(margin).toLocaleString()} LKR</span>
                            </div>
                            <div class="flex gap-2 pt-2">
                                <button onclick="editProduct('${item.id}')" class="flex-1 text-cyan-400 text-xs py-1.5 rounded-lg bg-cyan-950/50 hover:bg-cyan-950 font-bold border border-cyan-800/50 flex items-center justify-center gap-1">
                                    <i class="fa-solid fa-pen text-[10px]"></i> Edit
                                </button>
                                <button onclick="deleteProduct('${item.id}')" class="text-rose-400 text-xs px-3 py-1.5 rounded-lg bg-rose-950/50 hover:bg-rose-950 font-bold border border-rose-800/50">
                                    <i class="fa-solid fa-trash-can text-[10px]"></i>
                                </button>
                            </div>
                        </div>
                    `;
                }

                const card = document.createElement('div');
                card.className = "glass-card rounded-2xl p-5 transition-all flex flex-col justify-between";
                card.innerHTML = `
                    <div>
                        <div class="flex justify-between items-center gap-2 mb-3">
                            <span class="px-2.5 py-1 rounded-lg text-[10px] font-extrabold uppercase tracking-wider bg-cyan-500/10 text-cyan-400 border border-cyan-500/20">${item.category}</span>
                            <span class="px-2.5 py-0.5 rounded-full text-[10px] font-bold border ${stockColor}">${item.stockStatus}</span>
                        </div>
                        <h3 onclick="openQuickView('${item.id}')" class="font-bold text-white text-base mb-2 line-clamp-2 hover:text-cyan-400 cursor-pointer transition">${item.name}</h3>
                        <div class="text-xs text-slate-400 mb-4 flex items-center gap-1.5">
                            <i class="fa-solid fa-shield-check text-cyan-400"></i> Warranty: <span class="font-semibold text-slate-200">${item.warranty}</span>
                        </div>
                    </div>
                    <div>
                        <div class="bg-slate-950/80 p-3 rounded-xl border border-slate-800/80 mb-3">
                            <div class="text-[10px] uppercase tracking-wider text-slate-500 font-bold">Retail Price</div>
                            <div class="text-lg font-black text-cyan-400">Rs. ${Number(item.retailPrice).toLocaleString()} <span class="text-xs font-normal text-slate-500">LKR</span></div>
                        </div>
                        ${adminHtml}
                        <button onclick="shareWhatsApp('${item.name}', '${item.retailPrice}', '${item.warranty}')" class="w-full mt-2 bg-gradient-to-r from-emerald-500 to-teal-600 hover:from-emerald-400 hover:to-teal-500 text-slate-950 font-bold py-2.5 px-3 rounded-xl text-xs transition flex items-center justify-center gap-2 shadow-lg shadow-emerald-500/10">
                            <i class="fa-brands fa-whatsapp text-sm"></i> Share Quote
                        </button>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        function openQuickView(id) {
            const item = products.find(p => p.id === id);
            if (!item) return;
            const content = document.getElementById('quickViewContent');
            content.innerHTML = `
                <div class="space-y-4">
                    <span class="px-2.5 py-1 rounded-lg text-[10px] font-extrabold uppercase bg-cyan-500/10 text-cyan-400 border border-cyan-500/20">${item.category}</span>
                    <h3 class="text-xl font-bold text-white">${item.name}</h3>
                    <div class="bg-slate-950 p-4 rounded-2xl border border-slate-800 space-y-2 text-xs">
                        <div class="flex justify-between text-slate-400"><span>Retail Price:</span><span class="font-bold text-cyan-400 text-base">Rs. ${Number(item.retailPrice).toLocaleString()} LKR</span></div>
                        <div class="flex justify-between text-slate-400"><span>Warranty:</span><span class="font-semibold text-slate-200">${item.warranty}</span></div>
                        <div class="flex justify-between text-slate-400"><span>Availability:</span><span class="font-semibold text-emerald-400">${item.stockStatus}</span></div>
                    </div>
                    <button onclick="shareWhatsApp('${item.name}', '${item.retailPrice}', '${item.warranty}')" class="w-full bg-emerald-500 text-slate-950 font-bold py-3 rounded-xl text-xs flex items-center justify-center gap-2">
                        <i class="fa-brands fa-whatsapp text-base"></i> Send Quote via WhatsApp
                    </button>
                </div>
            `;
            document.getElementById('quickViewModal').classList.remove('hidden');
        }

        function closeQuickView() {
            document.getElementById('quickViewModal').classList.add('hidden');
        }

        function filterCategory(cat) {
            currentCategory = cat;
            document.querySelectorAll('.cat-chip').forEach(btn => {
                if (btn.innerText.includes(cat) || (cat === 'All' && btn.innerText === 'All Categories')) {
                    btn.className = "cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-cyan-500 text-slate-950 transition shadow-md shadow-cyan-500/20";
                } else {
                    btn.className = "cat-chip px-4 py-1.5 rounded-xl text-xs font-bold whitespace-nowrap bg-slate-900/80 text-slate-400 hover:bg-slate-800 hover:text-slate-200 border border-slate-800 transition";
                }
            });
            renderProducts();
        }

        function filterProducts() {
            renderProducts();
        }

        function toggleAdminMode() {
            isAdminMode = !isAdminMode;
            const btnText = document.getElementById('modeText');
            const btnIcon = document.getElementById('modeIcon');
            const addBtn = document.getElementById('addProductBtn');

            if (isAdminMode) {
                btnText.innerText = "Admin View";
                btnIcon.className = "fa-solid fa-lock-open text-emerald-400";
                addBtn.classList.remove('hidden');
            } else {
                btnText.innerText = "Customer View";
                btnIcon.className = "fa-solid fa-shield-halved text-cyan-400";
                addBtn.classList.add('hidden');
            }
            renderProducts();
        }

        function openModal(isEdit = false) {
            document.getElementById('productModal').classList.remove('hidden');
            if (!isEdit) {
                document.getElementById('modalTitle').innerText = "Add Inventory Item";
                document.getElementById('productForm').reset();
                document.getElementById('productId').value = '';
            }
        }

        function closeModal() {
            document.getElementById('productModal').classList.add('hidden');
        }

        async function saveProduct(e) {
            e.preventDefault();
            const id = document.getElementById('productId').value || Date.now().toString();
            const newItem = {
                id: id,
                name: document.getElementById('formName').value,
                category: document.getElementById('formCategory').value,
                warranty: document.getElementById('formWarranty').value,
                retailPrice: Number(document.getElementById('formRetail').value),
                wholesalePrice: Number(document.getElementById('formWholesale').value),
                stockStatus: document.getElementById('formStock').value
            };

            if (isCloudActive && dbRef) {
                try {
                    await firebase.database().ref('products/' + id).set(newItem);
                } catch (err) {
                    console.error("Save error:", err);
                }
            } else {
                const idx = products.findIndex(p => p.id === id);
                if (idx >= 0) {
                    products[idx] = newItem;
                } else {
                    products.push(newItem);
                }
                localStorage.setItem('cmos_products_v2', JSON.stringify(products));
                renderProducts();
            }

            closeModal();
        }

        function editProduct(id) {
            const item = products.find(p => p.id === id);
            if (!item) return;
            document.getElementById('modalTitle').innerText = "Edit Product Details";
            document.getElementById('productId').value = item.id;
            document.getElementById('formName').value = item.name;
            document.getElementById('formCategory').value = item.category;
            document.getElementById('formWarranty').value = item.warranty;
            document.getElementById('formRetail').value = item.retailPrice;
            document.getElementById('formWholesale').value = item.wholesalePrice;
            document.getElementById('formStock').value = item.stockStatus;
            document.getElementById('productModal').classList.remove('hidden');
        }

        async function deleteProduct(id) {
            if (confirm("Delete this inventory item?")) {
                if (isCloudActive && dbRef) {
                    try {
                        await firebase.database().ref('products/' + id).remove();
                    } catch (err) {
                        console.error("Delete error:", err);
                    }
                } else {
                    products = products.filter(p => p.id !== id);
                    localStorage.setItem('cmos_products_v2', JSON.stringify(products));
                    renderProducts();
                }
            }
        }

        function shareWhatsApp(name, retail, warranty) {
            const text = `*CMOS Computers Anuradhapura*\n📍 New Bus Stand, Anuradhapura\n\n📦 *Item:* ${name}\n🛡️ *Warranty:* ${warranty}\n💵 *Price:* Rs. ${Number(retail).toLocaleString()} LKR\n\n📞 Contact: 070 318 2015 / 025 222 8715 / 071 318 2015`;
            const encoded = encodeURIComponent(text);
            window.open(`https://wa.me/?text=${encoded}`, '_blank');
        }

        window.onload = initFirebase;
    </script>
</body>
</html>
