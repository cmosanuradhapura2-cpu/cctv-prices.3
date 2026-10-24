function renderTable(items, tbody) {
      tbody.innerHTML = items.map(p => {
        const profit = p.retail - p.wholesale;
        const marginPct = Math.round((profit / p.retail) * 100);
        const is4G = p.category === '4G SIM';

        return `
          <tr class="hover:bg-slate-700/50 transition-colors bg-slate-800 text-slate-100 border-b border-slate-700">
            <td class="py-3.5 px-4 whitespace-nowrap">
              <div class="flex flex-col">
                <span class="font-bold text-white flex items-center gap-1.5">
                  ${p.brand}
                  ${is4G ? '<span class="px-1.5 py-0.5 rounded text-[10px] bg-amber-500/20 text-amber-300 border border-amber-500/30">4G SIM</span>' : ''}
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
