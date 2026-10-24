<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>C-MOS CCTV Price List & Inventory System</title>

  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- Lucide Icons -->
  <script src="https://unpkg.com/lucide@latest"></script>

  <!-- Google Fonts: Inter & Noto Sans Sinhala -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Noto+Sans+Sinhala:wght@400;500;600;700&display=swap" rel="stylesheet">

  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          colors: {
            brand: {
              50: '#eef2ff',
              100: '#e0e7ff',
              500: '#6366f1',
              600: '#4f46e5',
              700: '#4338ca',
              900: '#312e81'
            }
          },
          fontFamily: {
            sans: ['Inter', 'Noto Sans Sinhala', 'sans-serif'],
          }
        }
      }
    }
  </script>

  <style>
    body {
      font-family: 'Inter', 'Noto Sans Sinhala', sans-serif;
      background-color: #0f172a;
      color: #f8fafc;
    }
    
    select option {
      background-color: #0f172a !important;
      color: #f8fafc !important;
      padding: 10px !important;
    }

    .custom-scrollbar::-webkit-scrollbar {
      width: 6px;
      height: 6px;
    }
    .custom-scrollbar::-webkit-scrollbar-track {
      background: #1e293b;
    }
    .custom-scrollbar::-webkit-scrollbar-thumb {
      background: #475569;
      border-radius: 3px;
    }

    @media print {
      .no-print {
        display: none !important;
      }
      body {
        background-color: #ffffff !important;
        color: #000000 !important;
      }
      .print-table {
        width: 100% !important;
        border-collapse: collapse !important;
      }
      .print-table th, .print-table td {
        border: 1px solid #cbd5e1 !important;
        padding: 8px !important;
        color: #000000 !important;
      }
    }
  </style>
</head>
<body class="min-h-screen flex flex-col justify-between custom-scrollbar bg-slate-900 text-slate-100">

  <!-- HEADER / NAVBAR -->
  <header class="sticky top-0 z-30 bg-slate-800/90 backdrop-blur-md border-b border-slate-700 shadow-lg no-print">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-3.5 flex flex-col md:flex-row items-center justify-between gap-4">
      
      <!-- Brand & Title -->
      <div class="flex items-center justify-between w-full md:w-auto">
        <div class="flex items-center space-x-3">
          <div class="p-2.5 bg-gradient-to-tr from-indigo-600 to-violet-500 rounded-xl shadow-md text-white">
            <i data-lucide="video" class="w-6 h-6"></i>
          </div>
          <div>
            <h1 class="text-xl font-bold tracking-tight text-white flex items-center gap-2">
              C-MOS COMPUTERS
              <span class="text-xs font-semibold px-2.5 py-0.5 rounded-full bg-indigo-500/20 text-indigo-300 border border-indigo-500/30">CCTV Manager</span>
            </h1>
            <p class="text-xs text-slate-400">මිල ගණන් සහ තොග කළමනාකරණ පද්ධතිය</p>
          </div>
        </div>

        <div class="flex md:hidden items-center gap-2">
          <button onclick="openModal('addModal')" class="bg-indigo-600 hover:bg-indigo-500 text-white p-2 rounded-lg flex items-center justify-center">
            <i data-lucide="plus" class="w-5 h-5"></i>
          </button>
        </div>
      </div>

      <!-- Action Buttons -->
      <div class="flex flex-wrap items-center justify-end gap-2.5 w-full md:w-auto">
        
        <!-- Live Storage Indicator -->
        <div class="hidden lg:flex items-center gap-2 px-3 py-1.5 rounded-lg bg-emerald-500/10 border border-emerald-500/20 text-emerald-400 text-xs">
          <span class="w-2 h-2 rounded-full bg-emerald-400 animate-pulse"></span>
          <span>Auto-Saved in Browser</span>
        </div>

        <!-- Add New Product Button -->
        <button onclick="openModal('addModal')" class="bg-gradient-to-r from-indigo-600 to-indigo-500 hover:from-indigo-500 hover:to-indigo-400 text-white font-medium text-sm px-3.5 py-2 rounded-xl shadow-lg shadow-indigo-600/20 transition-all flex items-center gap-2">
          <i data-lucide="plus-circle" class="w-4 h-4"></i>
          <span>Add Product</span>
        </button>

        <!-- WhatsApp Share Button -->
        <button onclick="openWhatsAppModal()" class="bg-emerald-600 hover:bg-emerald-500 text-white font-medium text-sm px-3.5 py-2 rounded-xl shadow-lg shadow-emerald-600/20 transition-all flex items-center gap-2">
          <i data-lucide="message-square" class="w-4 h-4"></i>
          <span>WhatsApp List</span>
        </button>

        <!-- Print Button -->
        <button onclick="window.print()" class="bg-slate-700 hover:bg-slate-600 text-slate-200 font-medium text-sm px-3 py-2 rounded-xl transition-all flex items-center gap-1.5">
          <i data-lucide="printer" class="w-4 h-4"></i>
          <span class="hidden sm:inline">Print</span>
        </button>

        <!-- Export Backup -->
        <button onclick="exportJSON()" class="bg-slate-700 hover:bg-slate-600 text-slate-200 font-medium text-sm px-3 py-2 rounded-xl transition-all flex items-center gap-1.5" title="Download backup file">
          <i data-lucide="download" class="w-4 h-4"></i>
          <span class="hidden sm:inline">Export</span>
        </button>

        <!-- Restore Backup -->
        <label class="bg-slate-700 hover:bg-slate-600 text-slate-200 font-medium text-sm px-3 py-2 rounded-xl transition-all flex items-center gap-1.5 cursor-pointer" title="Restore from backup file">
          <i data-lucide="upload" class="w-4 h-4"></i>
          <span class="hidden sm:inline">Restore</span>
          <input type="file" id="importFileInput" accept=".json" class="hidden" onchange="importJSON(event)">
        </label>

        <!-- Reset Button -->
        <button onclick="confirmReset()" class="bg-rose-500/10 hover:bg-rose-500/20 text-rose-400 border border-rose-500/20 p-2 rounded-xl transition-all" title="Reset to default items">
          <i data-lucide="rotate-ccw" class="w-4 h-4"></i>
        </button>
      </div>

    </div>
  </header>

  <!-- MAIN CONTAINER -->
  <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6 flex-1 w-full space-y-6">

    <!-- SEARCH & FILTER BAR -->
    <div class="bg-slate-800 border border-slate-700 rounded-2xl p-4 shadow-xl no-print backdrop-blur-md">
      <div class="grid grid-cols-1 md:grid-cols-12 gap-3">
        
        <!-- Live Search Box -->
        <div class="md:col-span-5 relative">
          <div class="absolute inset-y-0 left-0 pl-3.5 flex items-center pointer-events-none text-slate-400">
            <i data-lucide="search" class="w-5 h-5"></i>
          </div>
          <input 
            type="text" 
            id="searchInput" 
            placeholder="Search CCTV model, brand, WiFi, 4G..." 
            oninput="renderProducts()"
            class="w-full pl-10 pr-4 py-2.5 bg-slate-900 border border-slate-700 text-white rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 placeholder-slate-500"
          >
        </div>

        <!-- Brand Filter Dropdown -->
        <div class="md:col-span-3">
          <select id="brandFilter" onchange="renderProducts()" class="w-full py-2.5 px-3 bg-slate-900 border border-slate-700 text-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500">
            <option value="ALL">All Brands (සියලුම සන්නාම)</option>
            <option value="Hikvision">Hikvision</option>
            <option value="Dahua">Dahua</option>
            <option value="Imou">Imou</option>
            <option value="Ezviz">Ezviz</option>
            <option value="Tiandy">Tiandy</option>
            <option value="Baseus">Baseus</option>
            <option value="Other">Other</option>
          </select>
        </div>

        <!-- Category Filter Dropdown -->
        <div class="md:col-span-3">
          <select id="categoryFilter" onchange="renderProducts()" class="w-full py-2.5 px-3 bg-slate-900 border border-slate-700 text-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500">
            <option value="ALL">All Categories (සියලු කාණ්ඩ)</option>
            <option value="WiFi Camera">WiFi Cameras</option>
            <option value="4G SIM">4G / SIM Cameras & Routers</option>
            <option value="IP Camera">IP Cameras</option>
            <option value="Analog Camera">Analog Cameras</option>
            <option value="DVR / NVR">DVR & NVR Recorders</option>
            <option value="Accessories">Accessories & Power</option>
            <option value="Storage">Hard Drives & SD Cards</option>
          </select>
        </div>

        <!-- View Toggle Buttons -->
        <div class="md:col-span-1 flex items-center justify-end gap-1 bg-slate-900 border border-slate-700 p-1 rounded-xl">
          <button id="viewTableBtn" onclick="setViewMode('table')" class="flex-1 py-1.5 flex justify-center items-center rounded-lg bg-indigo-600 text-white transition-all">
            <i data-lucide="list" class="w-4 h-4"></i>
          </button>
          <button id="viewGridBtn" onclick="setViewMode('grid')" class="flex-1 py-1.5 flex justify-center items-center rounded-lg text-slate-400 hover:text-white transition-all">
            <i data-lucide="layout-grid" class="w-4 h-4"></i>
          </button>
        </div>

      </div>

      <!-- Quick Brand Chips -->
      <div class="flex items-center gap-2 mt-3 pt-3 border-t border-slate-700 overflow-x-auto custom-scrollbar text-xs">
        <span class="text-slate-400 whitespace-nowrap font-medium">Quick Filter:</span>
        <button onclick="quickFilterBrand('ALL')" class="px-2.5 py-1 rounded-lg bg-slate-700 hover:bg-indigo-600 text-slate-300 hover:text-white transition-all whitespace-nowrap">All</button>
        <button onclick="quickFilterBrand('WiFi Camera')" class="px-2.5 py-1 rounded-lg bg-cyan-500/20 text-cyan-300 border border-cyan-500/30 hover:bg-cyan-500 hover:text-white transition-all whitespace-nowrap font-medium">📶 WiFi Cameras</button>
        <button onclick="quickFilterBrand('4G SIM')" class="px-2.5 py-1 rounded-lg bg-amber-500/20 text-amber-300 border border-amber-500/30 hover:bg-amber-500 hover:text-white transition-all whitespace-nowrap font-medium">📡 4G SIM Cameras</button>
        <button onclick="quickFilterBrand('Hikvision')" class="px-2.5 py-1 rounded-lg bg-slate-700 hover:bg-red-600 text-slate-300 hover:text-white transition-all whitespace-nowrap">Hikvision</button>
        <button onclick="quickFilterBrand('Dahua')" class="px-2.5 py-1 rounded-lg bg-slate-700 hover:bg-red-500 text-slate-300 hover:text-white transition-all whitespace-nowrap">Dahua</button>
        <button onclick="quickFilterBrand('Imou')" class="px-2.5 py-1 rounded-lg bg-slate-700 hover:bg-amber-600 text-slate-300 hover:text-white transition-all whitespace-nowrap">Imou</button>
        <button onclick="quickFilterBrand('Ezviz')" class="px-2.5 py-1 rounded-lg bg-slate-700 hover:bg-cyan-600 text-slate-300 hover:text-white transition-all whitespace-nowrap">Ezviz</button>
      </div>
    </div>

    <!-- STATS COUNTER BAR -->
    <div class="grid grid-cols-2 md:grid-cols-4 gap-3 no-print">
      <div class="bg-slate-800 border border-slate-700 rounded-xl p-3 flex items-center justify-between">
        <div>
          <p class="text-xs text-slate-400">Total Products</p>
          <p id="statTotalItems" class="text-lg font-bold text-white">0</p>
        </div>
        <i data-lucide="box" class="w-5 h-5 text-indigo-400"></i>
      </div>
      <div class="bg-slate-800 border border-slate-700 rounded-xl p-3 flex items-center justify-between">
        <div>
          <p class="text-xs text-slate-400">WiFi & 4G Devices</p>
          <p id="statWirelessItems" class="text-lg font-bold text-cyan-400">0</p>
        </div>
        <i data-lucide="wifi" class="w-5 h-5 text-cyan-400"></i>
      </div>
      <div class="bg-slate-800 border border-slate-700 rounded-xl p-3 flex items-center justify-between">
        <div>
          <p class="text-xs text-slate-400">Avg Wholesale Margin</p>
          <p id="statAvgMargin" class="text-lg font-bold text-emerald-400">0%</p>
        </div>
        <i data-lucide="trending-up" class="w-5 h-5 text-emerald-400"></i>
      </div>
      <div class="bg-slate-800 border border-slate-700 rounded-xl p-3 flex items-center justify-between">
        <div>
          <p class="text-xs text-slate-400">Status</p>
          <p class="text-xs font-semibold text-emerald-400 flex items-center gap-1">
            <span class="w-2 h-2 rounded-full bg-emerald-400 animate-ping"></span> Live & Saved
          </p>
        </div>
        <i data-lucide="shield-check" class="w-5 h-5 text-emerald-400"></i>
      </div>
    </div>

    <!-- PRODUCT LIST CONTAINER -->
    <div id="tableContainer" class="bg-slate-800 border border-slate-700 rounded-2xl shadow-xl overflow-hidden backdrop-blur-md">
      
      <!-- Table View -->
      <div class="overflow-x-auto">
        <table class="w-full text-left border-collapse print-table">
          <thead>
            <tr class="bg-slate-900 text-slate-300 text-xs font-semibold uppercase tracking-wider border-b border-slate-700">
              <th class="py-3.5 px-4">Brand / Category</th>
              <th class="py-3.5 px-4">Product Name & Specifications</th>
              <th class="py-3.5 px-4 text-right">Wholesale Price (තොග)</th>
              <th class="py-3.5 px-4 text-right">Retail Price (සිල්ලර)</th>
              <th class="py-3.5 px-4 text-center">Profit Margin</th>
              <th class="py-3.5 px-4 text-center no-print">Actions</th>
            </tr>
          </thead>
          <tbody id="productTableBody" class="divide-y divide-slate-700 text-sm bg-slate-800">
            <!-- Dynamic Insertion -->
          </tbody>
        </table>
      </div>

    </div>

    <!-- Grid View Container -->
    <div id="gridContainer" class="hidden grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
      <!-- Dynamic Grid Cards -->
    </div>

    <!-- Empty State -->
    <div id="emptyState" class="hidden bg-slate-800 border border-dashed border-slate-700 rounded-2xl p-12 text-center">
      <div class="w-16 h-16 bg-slate-700 text-slate-400 rounded-full flex items-center justify-center mx-auto mb-4">
        <i data-lucide="search-x" class="w-8 h-8"></i>
      </div>
      <h3 class="text-lg font-semibold text-white">No products found</h3>
      <p class="text-sm text-slate-400 mt-1">Try adjusting your search terms or filters above.</p>
      <button onclick="resetFilters()" class="mt-4 px-4 py-2 bg-indigo-600 hover:bg-indigo-500 text-white text-xs font-medium rounded-xl transition-all">
        Reset Search Filters
      </button>
    </div>

  </main>

  <!-- FOOTER -->
  <footer class="bg-slate-900 border-t border-slate-800 py-4 text-center text-xs text-slate-500 no-print">
    <div class="max-w-7xl mx-auto px-4 flex flex-col sm:flex-row items-center justify-between gap-2">
      <p>© 2026 C-MOS Computers & Technologies — Anuradhapura. All Rights Reserved.</p>
      <p class="text-slate-400">CCTV & Security Solutions | Hikvision • Dahua • Imou • Ezviz • Tiandy</p>
    </div>
  </footer>

  <!-- MODAL: ADD / EDIT PRODUCT -->
  <div id="productModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
    <div class="bg-slate-800 border border-slate-700 rounded-2xl w-full max-w-lg shadow-2xl overflow-hidden transform transition-all">
      
      <div class="px-6 py-4 bg-slate-900 border-b border-slate-700 flex items-center justify-between">
        <h3 id="modalTitle" class="text-lg font-bold text-white flex items-center gap-2">
          <i data-lucide="plus-circle" class="w-5 h-5 text-indigo-400"></i>
          <span>Add New Product</span>
        </h3>
        <button onclick="closeModal('productModal')" class="text-slate-400 hover:text-white p-1 rounded-lg">
          <i data-lucide="x" class="w-5 h-5"></i>
        </button>
      </div>

      <form id="productForm" onsubmit="handleFormSubmit(event)" class="p-6 space-y-4">
        <input type="hidden" id="productId">

        <!-- Product Name -->
        <div>
          <label class="block text-xs font-medium text-slate-300 mb-1">Product Name / Model Number *</label>
          <input 
            type="text" 
            id="productName" 
            required
            placeholder="e.g. Imou Ranger 2 WiFi 3MP Camera"
            class="w-full px-3.5 py-2.5 bg-slate-900 border border-slate-700 text-white rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500"
          >
        </div>

        <!-- Brand & Category -->
        <div class="grid grid-cols-2 gap-3">
          <div>
            <label class="block text-xs font-medium text-slate-300 mb-1">Brand *</label>
            <select id="productBrand" required class="w-full px-3 py-2.5 bg-slate-900 border border-slate-700 text-white rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500">
              <option value="Hikvision">Hikvision</option>
              <option value="Dahua">Dahua</option>
              <option value="Imou">Imou</option>
              <option value="Ezviz">Ezviz</option>
              <option value="Tiandy">Tiandy</option>
              <option value="Baseus">Baseus</option>
              <option value="Other">Other</option>
            </select>
          </div>

          <div>
            <label class="block text-xs font-medium text-slate-300 mb-1">Category *</label>
            <select id="productCategory" required class="w-full px-3 py-2.5 bg-slate-900 border border-slate-700 text-white rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500">
              <option value="WiFi Camera">WiFi Camera</option>
              <option value="4G SIM">4G SIM / Solar Camera</option>
              <option value="IP Camera">IP Camera</option>
              <option value="Analog Camera">Analog Camera</option>
              <option value="DVR / NVR">DVR / NVR</option>
              <option value="Accessories">Accessories</option>
              <option value="Storage">Hard Drive / SD Card</option>
            </select>
          </div>
        </div>

        <!-- Wholesale & Retail Price -->
        <div class="grid grid-cols-2 gap-3">
          <div>
            <label class="block text-xs font-medium text-slate-300 mb-1">Wholesale Price (LKR) *</label>
            <input 
              type="number" 
              id="productWholesale" 
              required
              min="0"
              placeholder="e.g. 6500"
              class="w-full px-3.5 py-2.5 bg-slate-900 border border-slate-700 text-white rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500"
            >
          </div>

          <div>
            <label class="block text-xs font-medium text-slate-300 mb-1">Retail Price (LKR) *</label>
            <input 
              type="number" 
              id="productRetail" 
              required
              min="0"
              placeholder="e.g. 8500"
              class="w-full px-3.5 py-2.5 bg-slate-900 border border-slate-700 text-white rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500"
            >
          </div>
        </div>

        <!-- Description / Specs -->
        <div>
          <label class="block text-xs font-medium text-slate-300 mb-1">Specifications / Notes</label>
          <textarea 
            id="productSpecs" 
            rows="2"
            placeholder="e.g. 3MP, Smart Tracking, Two-way Talk, Cloud Storage"
            class="w-full px-3.5 py-2 bg-slate-900 border border-slate-700 text-white rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500"
          ></textarea>
        </div>

        <!-- Buttons -->
        <div class="pt-2 flex items-center justify-end gap-2 border-t border-slate-700">
          <button type="button" onclick="closeModal('productModal')" class="px-4 py-2 bg-slate-700 hover:bg-slate-600 text-slate-300 rounded-xl text-xs font-medium transition-all">
            Cancel
          </button>
          <button type="submit" class="px-5 py-2 bg-indigo-600 hover:bg-indigo-500 text-white rounded-xl text-xs font-semibold shadow-lg shadow-indigo-600/30 transition-all flex items-center gap-1.5">
            <i data-lucide="check" class="w-4 h-4"></i>
            <span>Save Product</span>
          </button>
        </div>
      </form>

    </div>
  </div>

  <!-- MODAL: WHATSAPP SHARE GENERATOR -->
  <div id="whatsAppModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
    <div class="bg-slate-800 border border-slate-700 rounded-2xl w-full max-w-lg shadow-2xl overflow-hidden">
      
      <div class="px-6 py-4 bg-slate-900 border-b border-slate-700 flex items-center justify-between">
        <h3 class="text-lg font-bold text-white flex items-center gap-2">
          <i data-lucide="message-square" class="w-5 h-5 text-emerald-400"></i>
          <span>Share via WhatsApp</span>
        </h3>
        <button onclick="closeModal('whatsAppModal')" class="text-slate-400 hover:text-white p-1 rounded-lg">
          <i data-lucide="x" class="w-5 h-5"></i>
        </button>
      </div>

      <div class="p-6 space-y-4">
        <div>
          <label class="block text-xs font-medium text-slate-300 mb-1">Select Prices to Include:</label>
          <div class="grid grid-cols-3 gap-2">
            <button onclick="generateWhatsAppText('both')" class="py-2 px-3 rounded-xl bg-slate-700 hover:bg-emerald-600 text-white text-xs font-medium transition-all">Both Prices</button>
            <button onclick="generateWhatsAppText('wholesale')" class="py-2 px-3 rounded-xl bg-slate-700 hover:bg-emerald-600 text-white text-xs font-medium transition-all">Wholesale Only</button>
            <button onclick="generateWhatsAppText('retail')" class="py-2 px-3 rounded-xl bg-slate-700 hover:bg-emerald-600 text-white text-xs font-medium transition-all">Retail Only</button>
          </div>
        </div>

        <div>
          <label class="block text-xs font-medium text-slate-300 mb-1">Formatted Message Preview:</label>
          <textarea id="whatsappPreview" rows="8" readonly class="w-full p-3 bg-slate-900 border border-slate-700 text-emerald-400 text-xs font-mono rounded-xl focus:outline-none custom-scrollbar"></textarea>
        </div>

        <div class="flex items-center gap-2 pt-2 border-t border-slate-700">
          <button onclick="copyWhatsAppText()" class="flex-1 py-2.5 bg-slate-700 hover:bg-slate-600 text-white rounded-xl text-xs font-semibold transition-all flex items-center justify-center gap-2">
            <i data-lucide="copy" class="w-4 h-4"></i>
            <span>Copy Text</span>
          </button>
          <button onclick="sendWhatsAppDirect()" class="flex-1 py-2.5 bg-emerald-600 hover:bg-emerald-500 text-white rounded-xl text-xs font-semibold shadow-lg shadow-emerald-600/30 transition-all flex items-center justify-center gap-2">
            <i data-lucide="send" class="w-4 h-4"></i>
            <span>Open WhatsApp</span>
          </button>
        </div>
      </div>

    </div>
  </div>

  <!-- TOAST NOTIFICATION -->
  <div id="toast" class="fixed bottom-5 right-5 z-50 transform translate-y-20 opacity-0 transition-all duration-300 pointer-events-none">
    <div class="bg-emerald-500 text-white px-4 py-3 rounded-xl shadow-2xl flex items-center gap-3 border border-emerald-400">
      <i data-lucide="check-circle-2" class="w-5 h-5"></i>
      <span id="toastMsg" class="text-sm font-medium">Product saved successfully!</span>
    </div>
  </div>

  <!-- APPLICATION JAVASCRIPT -->
  <script>
    const STORAGE_KEY = 'cmos_cctv_inventory_v4';

    const INITIAL_PRODUCTS = [
      { id: '1', name: 'Imou Ranger 2 WiFi 3MP Indoor PT Camera', brand: 'Imou', category: 'WiFi Camera', wholesale: 6500, retail: 8500, specs: '3MP, Human Detection, Smart Tracking, Two-Way Talk, Privacy Mode' },
      { id: '2', name: 'Ezviz H6c Pro WiFi 2K Pan & Tilt Camera', brand: 'Ezviz', category: 'WiFi Camera', wholesale: 7200, retail: 9500, specs: '2K Resolution, Touch Call Button, Night Vision, Motion Tracking' },
      { id: '3', name: 'Hikvision 2MP WiFi Fixed Bullet Network Camera', brand: 'Hikvision', category: 'WiFi Camera', wholesale: 9800, retail: 12500, specs: '2MP, Built-in Mic & Speaker, IP67 Weatherproof, Wi-Fi Connection' },
      { id: '4', name: 'Dahua 4G Solar Powered Outdoor PTZ Security Camera', brand: 'Dahua', category: '4G SIM', wholesale: 24500, retail: 29500, specs: '4MP, Solar Panel + 4G LTE SIM Card Slot, Full Color Night Vision' },
      { id: '5', name: 'Hikvision 4G LTE Speed Dome PTZ Outdoor Camera', brand: 'Hikvision', category: '4G SIM', wholesale: 32000, retail: 38500, specs: '4MP, 4G SIM Direct Connect, 30m IR + White Light' },
      { id: '6', name: 'Imou Cruiser Dual 4G SIM 10MP Dual Lens Camera', brand: 'Imou', category: '4G SIM', wholesale: 18500, retail: 22500, specs: 'Dual 5MP + 5MP Lenses, 4G SIM, Smart Color Night Vision' },
      { id: '7', name: 'Hikvision 2MP Audio Fixed Mini Bullet IP Camera', brand: 'Hikvision', category: 'IP Camera', wholesale: 7200, retail: 9200, specs: '2MP, Built-in Audio Mic, PoE, IP67 Weatherproof' },
      { id: '8', name: 'Dahua 4 Channel Cooper XVR / DVR Recorder', brand: 'Dahua', category: 'DVR / NVR', wholesale: 11500, retail: 14500, specs: '4 CH 1080P Mini 1U Digital Video Recorder, H.265+' },
      { id: '9', name: 'Western Digital Purple 2TB Surveillance Hard Drive', brand: 'Other', category: 'Storage', wholesale: 18500, retail: 22000, specs: '24/7 Continuous DVR/NVR Recording, AllFrame Technology' }
    ];

    let products = [];
    let currentViewMode = 'table';

    document.addEventListener('DOMContentLoaded', () => {
      loadProductsFromStorage();
      renderProducts();
      lucide.createIcons();
    });

    function loadProductsFromStorage() {
      const savedData = localStorage.getItem(STORAGE_KEY);
      if (savedData) {
        try {
          products = JSON.parse(savedData);
        } catch (e) {
          products = [...INITIAL_PRODUCTS];
          saveProductsToStorage();
        }
      } else {
        products = [...INITIAL_PRODUCTS];
        saveProductsToStorage();
      }
    }

    function saveProductsToStorage() {
      localStorage.setItem(STORAGE_KEY, JSON.stringify(products));
    }

    function renderProducts() {
      const searchQuery = document.getElementById('searchInput').value.toLowerCase().trim();
      const selectedBrand = document.getElementById('brandFilter').value;
      const selectedCategory = document.getElementById('categoryFilter').value;

      const filtered = products.filter(p => {
        const matchesSearch = p.name.toLowerCase().includes(searchQuery) || 
                              p.brand.toLowerCase().includes(searchQuery) ||
                              p.category.toLowerCase().includes(searchQuery) ||
                              (p.specs && p.specs.toLowerCase().includes(searchQuery));

        const matchesBrand = selectedBrand === 'ALL' || p.brand === selectedBrand;
        const matchesCategory = selectedCategory === 'ALL' || p.category === selectedCategory;

        return matchesSearch && matchesBrand && matchesCategory;
      });

      document.getElementById('statTotalItems').innerText = products.length;
      document.getElementById('statWirelessItems').innerText = products.filter(p => p.category === '4G SIM' || p.category === 'WiFi Camera').length;

      if (products.length > 0) {
        const totalMarginPct = products.reduce((acc, p) => {
          const margin = ((p.retail - p.wholesale) / p.retail) * 100;
          return acc + margin;
        }, 0);
        document.getElementById('statAvgMargin').innerText = Math.round(totalMarginPct / products.length) + '%';
      } else {
        document.getElementById('statAvgMargin').innerText = '0%';
      }

      const tableBody = document.getElementById('productTableBody');
      const gridContainer = document.getElementById('gridContainer');
      const emptyState = document.getElementById('emptyState');

      if (filtered.length === 0) {
        document.getElementById('tableContainer').classList.add('hidden');
        gridContainer.classList.add('hidden');
        emptyState.classList.remove('hidden');
        return;
      }

      emptyState.classList.add('hidden');

      if (currentViewMode === 'table') {
        document.getElementById('tableContainer').classList.remove('hidden');
        gridContainer.classList.add('hidden');
        renderTable(filtered, tableBody);
      } else {
        document.getElementById('tableContainer').classList.add('hidden');
        gridContainer.classList.remove('hidden');
        renderGrid(filtered, gridContainer);
      }

      lucide.createIcons();
    }

    function renderTable(items, tbody) {
      tbody.innerHTML = items.map(p => {
        const profit = p.retail - p.wholesale;
        const marginPct = Math.round((profit / p.retail) * 100);
        const is4G = p.category === '4G SIM';
        const isWiFi = p.category === 'WiFi Camera';

        let badgeHtml = `<span class="px-1.5 py-0.5 rounded text-[10px] bg-indigo-500/20 text-indigo-300 border border-indigo-500/30">${p.category}</span>`;
        if (is4G) badgeHtml = '<span class="px-1.5 py-0.5 rounded text-[10px] bg-amber-500/20 text-amber-300 border border-amber-500/30">4G SIM</span>';
        if (isWiFi) badgeHtml = '<span class="px-1.5 py-0.5 rounded text-[10px] bg-cyan-500/20 text-cyan-300 border border-cyan-500/30">WiFi Camera</span>';

        return `
          <tr class="hover:bg-slate-700/50 transition-colors bg-slate-800 text-slate-100 border-b border-slate-700">
            <td class="py-3.5 px-4 whitespace-nowrap">
              <div class="flex flex-col">
                <span class="font-bold text-white flex items-center gap-1.5">
                  ${p.brand}
                  ${badgeHtml}
                </span>
                <span class="text-xs text-slate-300 font-medium">${p.category}</span>
              </div>
            </td>
            <td class="py-3.5 px-4">
              <div class="font-semibold text-white text-base">${p.name}</div>
              ${p.specs ? `<div class="text-xs text-slate-300 mt-0.5">${p.specs}</div>` : ''}
            </td>
            <td class="py-3.5 px-4 text-right whitespace-nowrap font-semibold text-slate-200">
              Rs. ${p.wholesale.toLocaleString()}
            </td>
            <td class="py-3.5 px-4 text-right whitespace-nowrap font-bold text-emerald-400">
              Rs. ${p.retail.toLocaleString()}
            </td>
            <td class="py-3.5 px-4 text-center whitespace-nowrap">
              <span class="inline-flex items-center gap-1 px-2.5 py-1 rounded-full text-xs font-semibold bg-indigo-500/20 text-indigo-200 border border-indigo-500/30">
                +Rs. ${profit.toLocaleString()} (${marginPct}%)
              </span>
            </td>
            <td class="py-3.5 px-4 text-center whitespace-nowrap no-print">
              <div class="flex items-center justify-center gap-1.5">
                <button onclick="editProduct('${p.id}')" class="p-1.5 bg-slate-700 hover:bg-indigo-600 text-slate-200 hover:text-white rounded-lg transition-all" title="Edit">
                  <i data-lucide="edit-3" class="w-4 h-4"></i>
                </button>
                <button onclick="deleteProduct('${p.id}')" class="p-1.5 bg-slate-700 hover:bg-rose-600 text-slate-200 hover:text-white rounded-lg transition-all" title="Delete">
                  <i data-lucide="trash-2" class="w-4 h-4"></i>
                </button>
              </div>
            </td>
          </tr>
        `;
      }).join('');
    }

    function renderGrid(items, container) {
      container.innerHTML = items.map(p => {
        const profit = p.retail - p.wholesale;
        const marginPct = Math.round((profit / p.retail) * 100);
        const is4G = p.category === '4G SIM';
        const isWiFi = p.category === 'WiFi Camera';

        let badgeClass = 'bg-indigo-500/20 text-indigo-300 border-indigo-500/30';
        if (is4G) badgeClass = 'bg-amber-500/20 text-amber-300 border-amber-500/30';
        if (isWiFi) badgeClass = 'bg-cyan-500/20 text-cyan-300 border-cyan-500/30';

        return `
          <div class="bg-slate-800 border border-slate-700 rounded-2xl p-4 flex flex-col justify-between space-y-3 shadow-lg text-slate-100">
            <div>
              <div class="flex items-center justify-between mb-1.5">
                <span class="text-xs font-bold px-2.5 py-0.5 rounded-full border ${badgeClass}">
                  ${p.brand} • ${p.category}
                </span>
                <div class="flex items-center gap-1 no-print">
                  <button onclick="editProduct('${p.id}')" class="text-slate-400 hover:text-white p-1">
                    <i data-lucide="edit-3" class="w-4 h-4"></i>
                  </button>
                  <button onclick="deleteProduct('${p.id}')" class="text-slate-400 hover:text-rose-400 p-1">
                    <i data-lucide="trash-2" class="w-4 h-4"></i>
                  </button>
                </div>
              </div>
              <h4 class="font-bold text-white text-base leading-snug">${p.name}</h4>
              ${p.specs ? `<p class="text-xs text-slate-300 mt-1 line-clamp-2">${p.specs}</p>` : ''}
            </div>

            <div class="pt-3 border-t border-slate-700 space-y-2">
              <div class="flex items-center justify-between text-xs">
                <span class="text-slate-400">Wholesale (තොග):</span>
                <span class="font-semibold text-slate-200">Rs. ${p.wholesale.toLocaleString()}</span>
              </div>
              <div class="flex items-center justify-between text-sm">
                <span class="text-slate-300 font-medium">Retail (සිල්ලර):</span>
                <span class="font-bold text-emerald-400 text-base">Rs. ${p.retail.toLocaleString()}</span>
              </div>
              <div class="text-center pt-1">
                <span class="text-[11px] font-semibold px-2 py-0.5 rounded bg-indigo-500/20 text-indigo-200 border border-indigo-500/30">
                  Profit: Rs. ${profit.toLocaleString()} (${marginPct}%)
                </span>
              </div>
            </div>
          </div>
        `;
      }).join('');
    }

    function handleFormSubmit(e) {
      e.preventDefault();

      const id = document.getElementById('productId').value;
      const name = document.getElementById('productName').value.trim();
      const brand = document.getElementById('productBrand').value;
      const category = document.getElementById('productCategory').value;
      const wholesale = parseFloat(document.getElementById('productWholesale').value) || 0;
      const retail = parseFloat(document.getElementById('productRetail').value) || 0;
      const specs = document.getElementById('productSpecs').value.trim();

      if (id) {
        const index = products.findIndex(p => p.id === id);
        if (index !== -1) {
          products[index] = { id, name, brand, category, wholesale, retail, specs };
          showToast('Product updated successfully!');
        }
      } else {
        const newProd = {
          id: Date.now().toString(),
          name, brand, category, wholesale, retail, specs
        };
        products.unshift(newProd);
        showToast('New product added and saved!');
      }

      saveProductsToStorage();
      renderProducts();
      closeModal('productModal');
    }

    function editProduct(id) {
      const prod = products.find(p => p.id === id);
      if (!prod) return;

      document.getElementById('productId').value = prod.id;
      document.getElementById('productName').value = prod.name;
      document.getElementById('productBrand').value = prod.brand;
      document.getElementById('productCategory').value = prod.category;
      document.getElementById('productWholesale').value = prod.wholesale;
      document.getElementById('productRetail').value = prod.retail;
      document.getElementById('productSpecs').value = prod.specs || '';

      document.getElementById('modalTitle').innerHTML = `
        <i data-lucide="edit-3" class="w-5 h-5 text-indigo-400"></i>
        <span>Edit Product</span>
      `;

      openModal('productModal');
      lucide.createIcons();
    }

    function deleteProduct(id) {
      if (confirm('Are you sure you want to delete this CCTV product?')) {
        products = products.filter(p => p.id !== id);
        saveProductsToStorage();
        renderProducts();
        showToast('Product deleted successfully');
      }
    }

    function setViewMode(mode) {
      currentViewMode = mode;
      const btnTable = document.getElementById('viewTableBtn');
      const btnGrid = document.getElementById('viewGridBtn');

      if (mode === 'table') {
        btnTable.className = 'flex-1 py-1.5 flex justify-center items-center rounded-lg bg-indigo-600 text-white transition-all';
        btnGrid.className = 'flex-1 py-1.5 flex justify-center items-center rounded-lg text-slate-400 hover:text-white transition-all';
      } else {
        btnGrid.className = 'flex-1 py-1.5 flex justify-center items-center rounded-lg bg-indigo-600 text-white transition-all';
        btnTable.className = 'flex-1 py-1.5 flex justify-center items-center rounded-lg text-slate-400 hover:text-white transition-all';
      }

      renderProducts();
    }

    function quickFilterBrand(filterVal) {
      document.getElementById('searchInput').value = '';
      if (filterVal === 'WiFi Camera' || filterVal === '4G SIM') {
        document.getElementById('categoryFilter').value = filterVal;
        document.getElementById('brandFilter').value = 'ALL';
      } else {
        document.getElementById('brandFilter').value = filterVal;
        document.getElementById('categoryFilter').value = 'ALL';
      }
      renderProducts();
    }

    function resetFilters() {
      document.getElementById('searchInput').value = '';
      document.getElementById('brandFilter').value = 'ALL';
      document.getElementById('categoryFilter').value = 'ALL';
      renderProducts();
    }

    function confirmReset() {
      if (confirm('Reset catalog to default items? Any custom products added will be restored.')) {
        products = [...INITIAL_PRODUCTS];
        saveProductsToStorage();
        renderProducts();
        showToast('Restored default CCTV inventory!');
      }
    }

    function exportJSON() {
      const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(products, null, 2));
      const downloadAnchor = document.createElement('a');
      downloadAnchor.setAttribute("href", dataStr);
      downloadAnchor.setAttribute("download", `CMOS_CCTV_Prices_${new Date().toISOString().slice(0,10)}.json`);
      document.body.appendChild(downloadAnchor);
      downloadAnchor.click();
      downloadAnchor.remove();
      showToast('Backup downloaded successfully!');
    }

    function importJSON(event) {
      const file = event.target.files[0];
      if (!file) return;

      const reader = new FileReader();
      reader.onload = function(e) {
        try {
          const importedData = JSON.parse(e.target.result);
          if (Array.isArray(importedData)) {
            products = importedData;
            saveProductsToStorage();
            renderProducts();
            showToast('Backup restored successfully!');
          } else {
            alert('Invalid backup file format.');
          }
        } catch (err) {
          alert('Error reading backup file.');
        }
      };
      reader.readAsText(file);
    }

    function openWhatsAppModal() {
      generateWhatsAppText('both');
      openModal('whatsAppModal');
    }

    function generateWhatsAppText(type) {
      let text = `📹 *C-MOS COMPUTERS - CCTV PRICE LIST*\n`;
      text += `📍 Anuradhapura | 📞 Contact for Orders\n`;
      text += `----------------------------------------\n\n`;

      products.forEach((p, idx) => {
        text += `${idx + 1}. *${p.brand}* - ${p.name}\n`;
        if (type === 'both' || type === 'wholesale') {
          text += `   • Wholesale: Rs. ${p.wholesale.toLocaleString()}\n`;
        }
        if (type === 'both' || type === 'retail') {
          text += `   • Retail: Rs. ${p.retail.toLocaleString()}\n`;
        }
        text += `\n`;
      });

      text += `----------------------------------------\n`;
      text += `*All items subject to availability.*`;

      document.getElementById('whatsappPreview').value = text;
    }

    function copyWhatsAppText() {
      const txt = document.getElementById('whatsappPreview');
      txt.select();
      document.execCommand('copy');
      showToast('Price list copied to clipboard!');
    }

    function sendWhatsAppDirect() {
      const txt = encodeURIComponent(document.getElementById('whatsappPreview').value);
      window.open(`https://api.whatsapp.com/send?text=${txt}`, '_blank');
    }

    function openModal(id) {
      if (id === 'addModal') {
        document.getElementById('productId').value = '';
        document.getElementById('productForm').reset();
        document.getElementById('modalTitle').innerHTML = `
          <i data-lucide="plus-circle" class="w-5 h-5 text-indigo-400"></i>
          <span>Add New Product</span>
        `;
        id = 'productModal';
      }
      document.getElementById(id).classList.remove('hidden');
      lucide.createIcons();
    }

    function closeModal(id) {
      document.getElementById(id).classList.add('hidden');
    }

    function showToast(msg) {
      const toast = document.getElementById('toast');
      document.getElementById('toastMsg').innerText = msg;
      toast.classList.remove('translate-y-20', 'opacity-0');
      
      setTimeout(() => {
        toast.classList.add('translate-y-20', 'opacity-0');
      }, 3000);
    }
  </script>
</body>
</html>
