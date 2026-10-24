<!DOCTYPE html>
<html lang="si" class="h-full bg-slate-950 text-slate-100"><head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CCTV Pro - Inventory &amp; Price List System</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- QR Code JS Library -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&amp;family=Noto+Sans+Sinhala:wght@400;500;600;700&amp;display=swap" rel="stylesheet">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'Noto Sans Sinhala', 'sans-serif'],
                    }
                }
            }
        }
    </script>

    <style>
        /* Print Styles */
        @media print {
            .no-print { display: none !important; }
            .print-only { display: block !important; }
            body { background: white !important; color: black !important; font-size: 10pt; }
            .print-container { width: 100% !important; margin: 0 !important; padding: 0 !important; box-shadow: none !important; border: none !important; }
            table { width: 100% !important; border-collapse: collapse !important; }
            th, td { border: 1px solid #cbd5e1 !important; padding: 6px 8px !important; color: black !important; }
            .badge-price { border: none !important; background: transparent !important; color: black !important; font-weight: bold; }
        }

        /* Custom Scrollbars */
        ::-webkit-scrollbar { width: 6px; height: 6px; }
        ::-webkit-scrollbar-track { background: #0f172a; }
        ::-webkit-scrollbar-thumb { background: #334155; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #475569; }

        /* Animation for toast */
        @keyframes slideIn {
            from { transform: translateY(-100%); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        .toast-animate {
            animation: slideIn 0.3s ease-out forwards;
        }
    </style>
<style>*, ::before, ::after{--tw-border-spacing-x:0;--tw-border-spacing-y:0;--tw-translate-x:0;--tw-translate-y:0;--tw-rotate:0;--tw-skew-x:0;--tw-skew-y:0;--tw-scale-x:1;--tw-scale-y:1;--tw-pan-x: ;--tw-pan-y: ;--tw-pinch-zoom: ;--tw-scroll-snap-strictness:proximity;--tw-gradient-from-position: ;--tw-gradient-via-position: ;--tw-gradient-to-position: ;--tw-ordinal: ;--tw-slashed-zero: ;--tw-numeric-figure: ;--tw-numeric-spacing: ;--tw-numeric-fraction: ;--tw-ring-inset: ;--tw-ring-offset-width:0px;--tw-ring-offset-color:#fff;--tw-ring-color:rgb(59 130 246 / 0.5);--tw-ring-offset-shadow:0 0 #0000;--tw-ring-shadow:0 0 #0000;--tw-shadow:0 0 #0000;--tw-shadow-colored:0 0 #0000;--tw-blur: ;--tw-brightness: ;--tw-contrast: ;--tw-grayscale: ;--tw-hue-rotate: ;--tw-invert: ;--tw-saturate: ;--tw-sepia: ;--tw-drop-shadow: ;--tw-backdrop-blur: ;--tw-backdrop-brightness: ;--tw-backdrop-contrast: ;--tw-backdrop-grayscale: ;--tw-backdrop-hue-rotate: ;--tw-backdrop-invert: ;--tw-backdrop-opacity: ;--tw-backdrop-saturate: ;--tw-backdrop-sepia: ;--tw-contain-size: ;--tw-contain-layout: ;--tw-contain-paint: ;--tw-contain-style: }::backdrop{--tw-border-spacing-x:0;--tw-border-spacing-y:0;--tw-translate-x:0;--tw-translate-y:0;--tw-rotate:0;--tw-skew-x:0;--tw-skew-y:0;--tw-scale-x:1;--tw-scale-y:1;--tw-pan-x: ;--tw-pan-y: ;--tw-pinch-zoom: ;--tw-scroll-snap-strictness:proximity;--tw-gradient-from-position: ;--tw-gradient-via-position: ;--tw-gradient-to-position: ;--tw-ordinal: ;--tw-slashed-zero: ;--tw-numeric-figure: ;--tw-numeric-spacing: ;--tw-numeric-fraction: ;--tw-ring-inset: ;--tw-ring-offset-width:0px;--tw-ring-offset-color:#fff;--tw-ring-color:rgb(59 130 246 / 0.5);--tw-ring-offset-shadow:0 0 #0000;--tw-ring-shadow:0 0 #0000;--tw-shadow:0 0 #0000;--tw-shadow-colored:0 0 #0000;--tw-blur: ;--tw-brightness: ;--tw-contrast: ;--tw-grayscale: ;--tw-hue-rotate: ;--tw-invert: ;--tw-saturate: ;--tw-sepia: ;--tw-drop-shadow: ;--tw-backdrop-blur: ;--tw-backdrop-brightness: ;--tw-backdrop-contrast: ;--tw-backdrop-grayscale: ;--tw-backdrop-hue-rotate: ;--tw-backdrop-invert: ;--tw-backdrop-opacity: ;--tw-backdrop-saturate: ;--tw-backdrop-sepia: ;--tw-contain-size: ;--tw-contain-layout: ;--tw-contain-paint: ;--tw-contain-style: }/* ! tailwindcss v3.4.17 | MIT License | https://tailwindcss.com */*,::after,::before{box-sizing:border-box;border-width:0;border-style:solid;border-color:#e5e7eb}::after,::before{--tw-content:''}:host,html{line-height:1.5;-webkit-text-size-adjust:100%;-moz-tab-size:4;tab-size:4;font-family:Inter, Noto Sans Sinhala, sans-serif;font-feature-settings:normal;font-variation-settings:normal;-webkit-tap-highlight-color:transparent}body{margin:0;line-height:inherit}hr{height:0;color:inherit;border-top-width:1px}abbr:where([title]){-webkit-text-decoration:underline dotted;text-decoration:underline dotted}h1,h2,h3,h4,h5,h6{font-size:inherit;font-weight:inherit}a{color:inherit;text-decoration:inherit}b,strong{font-weight:bolder}code,kbd,pre,samp{font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;font-feature-settings:normal;font-variation-settings:normal;font-size:1em}small{font-size:80%}sub,sup{font-size:75%;line-height:0;position:relative;vertical-align:baseline}sub{bottom:-.25em}sup{top:-.5em}table{text-indent:0;border-color:inherit;border-collapse:collapse}button,input,optgroup,select,textarea{font-family:inherit;font-feature-settings:inherit;font-variation-settings:inherit;font-size:100%;font-weight:inherit;line-height:inherit;letter-spacing:inherit;color:inherit;margin:0;padding:0}button,select{text-transform:none}button,input:where([type=button]),input:where([type=reset]),input:where([type=submit]){-webkit-appearance:button;background-color:transparent;background-image:none}:-moz-focusring{outline:auto}:-moz-ui-invalid{box-shadow:none}progress{vertical-align:baseline}::-webkit-inner-spin-button,::-webkit-outer-spin-button{height:auto}[type=search]{-webkit-appearance:textfield;outline-offset:-2px}::-webkit-search-decoration{-webkit-appearance:none}::-webkit-file-upload-button{-webkit-appearance:button;font:inherit}summary{display:list-item}blockquote,dd,dl,figure,h1,h2,h3,h4,h5,h6,hr,p,pre{margin:0}fieldset{margin:0;padding:0}legend{padding:0}menu,ol,ul{list-style:none;margin:0;padding:0}dialog{padding:0}textarea{resize:vertical}input::placeholder,textarea::placeholder{opacity:1;color:#9ca3af}[role=button],button{cursor:pointer}:disabled{cursor:default}audio,canvas,embed,iframe,img,object,svg,video{display:block;vertical-align:middle}img,video{max-width:100%;height:auto}[hidden]:where(:not([hidden=until-found])){display:none}.pointer-events-none{pointer-events:none}.fixed{position:fixed}.absolute{position:absolute}.relative{position:relative}.sticky{position:sticky}.inset-0{inset:0px}.inset-y-0{top:0px;bottom:0px}.left-0{left:0px}.right-0{right:0px}.right-4{right:1rem}.top-0{top:0px}.top-4{top:1rem}.z-30{z-index:30}.z-50{z-index:50}.mx-auto{margin-left:auto;margin-right:auto}.mb-1{margin-bottom:0.25rem}.mb-2{margin-bottom:0.5rem}.mb-3{margin-bottom:0.75rem}.mb-4{margin-bottom:1rem}.mb-6{margin-bottom:1.5rem}.ml-1{margin-left:0.25rem}.mr-1{margin-right:0.25rem}.mt-1{margin-top:0.25rem}.block{display:block}.inline-block{display:inline-block}.flex{display:flex}.inline-flex{display:inline-flex}.grid{display:grid}.hidden{display:none}.h-16{height:4rem}.h-full{height:100%}.min-h-\[120px\]{min-height:120px}.min-h-screen{min-height:100vh}.w-16{width:4rem}.w-full{width:100%}.min-w-\[120px\]{min-width:120px}.max-w-7xl{max-width:80rem}.max-w-xl{max-width:36rem}.shrink-0{flex-shrink:0}.flex-grow{flex-grow:1}.border-collapse{border-collapse:collapse}.transform{transform:translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}.cursor-pointer{cursor:pointer}.select-all{-webkit-user-select:all;user-select:all}.grid-cols-1{grid-template-columns:repeat(1, minmax(0, 1fr))}.grid-cols-2{grid-template-columns:repeat(2, minmax(0, 1fr))}.flex-col{flex-direction:column}.flex-wrap{flex-wrap:wrap}.items-center{align-items:center}.justify-end{justify-content:flex-end}.justify-center{justify-content:center}.justify-between{justify-content:space-between}.gap-1{gap:0.25rem}.gap-1\.5{gap:0.375rem}.gap-2{gap:0.5rem}.gap-3{gap:0.75rem}.gap-3\.5{gap:0.875rem}.gap-4{gap:1rem}.space-x-3 > :not([hidden]) ~ :not([hidden]){--tw-space-x-reverse:0;margin-right:calc(0.75rem * var(--tw-space-x-reverse));margin-left:calc(0.75rem * calc(1 - var(--tw-space-x-reverse)))}.space-y-2 > :not([hidden]) ~ :not([hidden]){--tw-space-y-reverse:0;margin-top:calc(0.5rem * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(0.5rem * var(--tw-space-y-reverse))}.space-y-3 > :not([hidden]) ~ :not([hidden]){--tw-space-y-reverse:0;margin-top:calc(0.75rem * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(0.75rem * var(--tw-space-y-reverse))}.space-y-4 > :not([hidden]) ~ :not([hidden]){--tw-space-y-reverse:0;margin-top:calc(1rem * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(1rem * var(--tw-space-y-reverse))}.space-y-6 > :not([hidden]) ~ :not([hidden]){--tw-space-y-reverse:0;margin-top:calc(1.5rem * calc(1 - var(--tw-space-y-reverse)));margin-bottom:calc(1.5rem * var(--tw-space-y-reverse))}.divide-y > :not([hidden]) ~ :not([hidden]){--tw-divide-y-reverse:0;border-top-width:calc(1px * calc(1 - var(--tw-divide-y-reverse)));border-bottom-width:calc(1px * var(--tw-divide-y-reverse))}.divide-slate-800\/60 > :not([hidden]) ~ :not([hidden]){border-color:rgb(30 41 59 / 0.6)}.overflow-hidden{overflow:hidden}.overflow-x-auto{overflow-x:auto}.rounded{border-radius:0.25rem}.rounded-2xl{border-radius:1rem}.rounded-full{border-radius:9999px}.rounded-lg{border-radius:0.5rem}.rounded-xl{border-radius:0.75rem}.rounded-md{border-radius:0.375rem}.border{border-width:1px}.border-b{border-bottom-width:1px}.border-t{border-top-width:1px}.border-amber-500\/30{border-color:rgb(245 158 11 / 0.3)}.border-blue-500\/30{border-color:rgb(59 130 246 / 0.3)}.border-blue-500\/40{border-color:rgb(59 130 246 / 0.4)}.border-blue-800\/50{border-color:rgb(30 64 175 / 0.5)}.border-emerald-500\/20{border-color:rgb(16 185 129 / 0.2)}.border-emerald-500\/30{border-color:rgb(16 185 129 / 0.3)}.border-emerald-500\/40{border-color:rgb(16 185 129 / 0.4)}.border-emerald-700\/50{border-color:rgb(4 120 87 / 0.5)}.border-red-500\/30{border-color:rgb(239 68 68 / 0.3)}.border-slate-300{--tw-border-opacity:1;border-color:rgb(203 213 225 / var(--tw-border-opacity, 1))}.border-slate-700{--tw-border-opacity:1;border-color:rgb(51 65 85 / var(--tw-border-opacity, 1))}.border-slate-700\/80{border-color:rgb(51 65 85 / 0.8)}.border-slate-800{--tw-border-opacity:1;border-color:rgb(30 41 59 / var(--tw-border-opacity, 1))}.border-orange-500\/30{border-color:rgb(249 115 22 / 0.3)}.border-slate-700\/60{border-color:rgb(51 65 85 / 0.6)}.border-emerald-400{--tw-border-opacity:1;border-color:rgb(52 211 153 / var(--tw-border-opacity, 1))}.bg-amber-500\/10{background-color:rgb(245 158 11 / 0.1)}.bg-blue-600{--tw-bg-opacity:1;background-color:rgb(37 99 235 / var(--tw-bg-opacity, 1))}.bg-blue-600\/20{background-color:rgb(37 99 235 / 0.2)}.bg-blue-900\/80{background-color:rgb(30 58 138 / 0.8)}.bg-blue-950\/60{background-color:rgb(23 37 84 / 0.6)}.bg-emerald-500{--tw-bg-opacity:1;background-color:rgb(16 185 129 / var(--tw-bg-opacity, 1))}.bg-emerald-500\/10{background-color:rgb(16 185 129 / 0.1)}.bg-emerald-500\/20{background-color:rgb(16 185 129 / 0.2)}.bg-emerald-600{--tw-bg-opacity:1;background-color:rgb(5 150 105 / var(--tw-bg-opacity, 1))}.bg-emerald-600\/20{background-color:rgb(5 150 105 / 0.2)}.bg-emerald-950\/80{background-color:rgb(2 44 34 / 0.8)}.bg-red-500\/10{background-color:rgb(239 68 68 / 0.1)}.bg-slate-800{--tw-bg-opacity:1;background-color:rgb(30 41 59 / var(--tw-bg-opacity, 1))}.bg-slate-900{--tw-bg-opacity:1;background-color:rgb(15 23 42 / var(--tw-bg-opacity, 1))}.bg-slate-900\/95{background-color:rgb(15 23 42 / 0.95)}.bg-slate-950{--tw-bg-opacity:1;background-color:rgb(2 6 23 / var(--tw-bg-opacity, 1))}.bg-slate-950\/80{background-color:rgb(2 6 23 / 0.8)}.bg-slate-950\/90{background-color:rgb(2 6 23 / 0.9)}.bg-white{--tw-bg-opacity:1;background-color:rgb(255 255 255 / var(--tw-bg-opacity, 1))}.bg-blue-500\/10{background-color:rgb(59 130 246 / 0.1)}.bg-orange-500\/20{background-color:rgb(249 115 22 / 0.2)}.bg-gradient-to-r{background-image:linear-gradient(to right, var(--tw-gradient-stops))}.bg-gradient-to-tr{background-image:linear-gradient(to top right, var(--tw-gradient-stops))}.from-blue-600{--tw-gradient-from:#2563eb var(--tw-gradient-from-position);--tw-gradient-to:rgb(37 99 235 / 0) var(--tw-gradient-to-position);--tw-gradient-stops:var(--tw-gradient-from), var(--tw-gradient-to)}.from-emerald-600{--tw-gradient-from:#059669 var(--tw-gradient-from-position);--tw-gradient-to:rgb(5 150 105 / 0) var(--tw-gradient-to-position);--tw-gradient-stops:var(--tw-gradient-from), var(--tw-gradient-to)}.to-indigo-600{--tw-gradient-to:#4f46e5 var(--tw-gradient-to-position)}.to-teal-600{--tw-gradient-to:#0d9488 var(--tw-gradient-to-position)}.p-0\.5{padding:0.125rem}.p-2{padding:0.5rem}.p-2\.5{padding:0.625rem}.p-3{padding:0.75rem}.p-4{padding:1rem}.p-6{padding:1.5rem}.px-1\.5{padding-left:0.375rem;padding-right:0.375rem}.px-2{padding-left:0.5rem;padding-right:0.5rem}.px-2\.5{padding-left:0.625rem;padding-right:0.625rem}.px-3{padding-left:0.75rem;padding-right:0.75rem}.px-3\.5{padding-left:0.875rem;padding-right:0.875rem}.px-4{padding-left:1rem;padding-right:1rem}.px-5{padding-left:1.25rem;padding-right:1.25rem}.px-6{padding-left:1.5rem;padding-right:1.5rem}.py-0\.5{padding-top:0.125rem;padding-bottom:0.125rem}.py-1{padding-top:0.25rem;padding-bottom:0.25rem}.py-1\.5{padding-top:0.375rem;padding-bottom:0.375rem}.py-16{padding-top:4rem;padding-bottom:4rem}.py-2{padding-top:0.5rem;padding-bottom:0.5rem}.py-2\.5{padding-top:0.625rem;padding-bottom:0.625rem}.py-3{padding-top:0.75rem;padding-bottom:0.75rem}.py-3\.5{padding-top:0.875rem;padding-bottom:0.875rem}.py-4{padding-top:1rem;padding-bottom:1rem}.py-6{padding-top:1.5rem;padding-bottom:1.5rem}.pb-4{padding-bottom:1rem}.pl-10{padding-left:2.5rem}.pl-11{padding-left:2.75rem}.pl-3{padding-left:0.75rem}.pl-4{padding-left:1rem}.pr-12{padding-right:3rem}.pr-3{padding-right:0.75rem}.pr-4{padding-right:1rem}.pt-1{padding-top:0.25rem}.pt-2{padding-top:0.5rem}.pt-4{padding-top:1rem}.text-left{text-align:left}.text-center{text-align:center}.font-mono{font-family:ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace}.font-sans{font-family:Inter, Noto Sans Sinhala, sans-serif}.text-2xl{font-size:1.5rem;line-height:2rem}.text-\[10px\]{font-size:10px}.text-\[11px\]{font-size:11px}.text-base{font-size:1rem;line-height:1.5rem}.text-lg{font-size:1.125rem;line-height:1.75rem}.text-sm{font-size:0.875rem;line-height:1.25rem}.text-xl{font-size:1.25rem;line-height:1.75rem}.text-xs{font-size:0.75rem;line-height:1rem}.font-bold{font-weight:700}.font-medium{font-weight:500}.font-semibold{font-weight:600}.uppercase{text-transform:uppercase}.tracking-tight{letter-spacing:-0.025em}.tracking-wider{letter-spacing:0.05em}.text-amber-400{--tw-text-opacity:1;color:rgb(251 191 36 / var(--tw-text-opacity, 1))}.text-blue-200{--tw-text-opacity:1;color:rgb(191 219 254 / var(--tw-text-opacity, 1))}.text-blue-300{--tw-text-opacity:1;color:rgb(147 197 253 / var(--tw-text-opacity, 1))}.text-blue-400{--tw-text-opacity:1;color:rgb(96 165 250 / var(--tw-text-opacity, 1))}.text-blue-500{--tw-text-opacity:1;color:rgb(59 130 246 / var(--tw-text-opacity, 1))}.text-emerald-200{--tw-text-opacity:1;color:rgb(167 243 208 / var(--tw-text-opacity, 1))}.text-emerald-400{--tw-text-opacity:1;color:rgb(52 211 153 / var(--tw-text-opacity, 1))}.text-purple-400{--tw-text-opacity:1;color:rgb(192 132 252 / var(--tw-text-opacity, 1))}.text-red-400{--tw-text-opacity:1;color:rgb(248 113 113 / var(--tw-text-opacity, 1))}.text-slate-100{--tw-text-opacity:1;color:rgb(241 245 249 / var(--tw-text-opacity, 1))}.text-slate-200{--tw-text-opacity:1;color:rgb(226 232 240 / var(--tw-text-opacity, 1))}.text-slate-300{--tw-text-opacity:1;color:rgb(203 213 225 / var(--tw-text-opacity, 1))}.text-slate-400{--tw-text-opacity:1;color:rgb(148 163 184 / var(--tw-text-opacity, 1))}.text-slate-500{--tw-text-opacity:1;color:rgb(100 116 139 / var(--tw-text-opacity, 1))}.text-slate-950{--tw-text-opacity:1;color:rgb(2 6 23 / var(--tw-text-opacity, 1))}.text-white{--tw-text-opacity:1;color:rgb(255 255 255 / var(--tw-text-opacity, 1))}.text-blue-500\/70{color:rgb(59 130 246 / 0.7)}.text-emerald-500\/70{color:rgb(16 185 129 / 0.7)}.text-orange-400{--tw-text-opacity:1;color:rgb(251 146 60 / var(--tw-text-opacity, 1))}.antialiased{-webkit-font-smoothing:antialiased;-moz-osx-font-smoothing:grayscale}.placeholder-slate-500::placeholder{--tw-placeholder-opacity:1;color:rgb(100 116 139 / var(--tw-placeholder-opacity, 1))}.placeholder-slate-600::placeholder{--tw-placeholder-opacity:1;color:rgb(71 85 105 / var(--tw-placeholder-opacity, 1))}.shadow-2xl{--tw-shadow:0 25px 50px -12px rgb(0 0 0 / 0.25);--tw-shadow-colored:0 25px 50px -12px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-inner{--tw-shadow:inset 0 2px 4px 0 rgb(0 0 0 / 0.05);--tw-shadow-colored:inset 0 2px 4px 0 var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-lg{--tw-shadow:0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);--tw-shadow-colored:0 10px 15px -3px var(--tw-shadow-color), 0 4px 6px -4px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-md{--tw-shadow:0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);--tw-shadow-colored:0 4px 6px -1px var(--tw-shadow-color), 0 2px 4px -2px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-sm{--tw-shadow:0 1px 2px 0 rgb(0 0 0 / 0.05);--tw-shadow-colored:0 1px 2px 0 var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-xl{--tw-shadow:0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);--tw-shadow-colored:0 20px 25px -5px var(--tw-shadow-color), 0 8px 10px -6px var(--tw-shadow-color);box-shadow:var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow)}.shadow-blue-500\/20{--tw-shadow-color:rgb(59 130 246 / 0.2);--tw-shadow:var(--tw-shadow-colored)}.shadow-blue-600\/30{--tw-shadow-color:rgb(37 99 235 / 0.3);--tw-shadow:var(--tw-shadow-colored)}.shadow-emerald-600\/30{--tw-shadow-color:rgb(5 150 105 / 0.3);--tw-shadow:var(--tw-shadow-colored)}.backdrop-blur{--tw-backdrop-blur:blur(8px);-webkit-backdrop-filter:var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);backdrop-filter:var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia)}.backdrop-blur-sm{--tw-backdrop-blur:blur(4px);-webkit-backdrop-filter:var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);backdrop-filter:var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia)}.transition{transition-property:color, background-color, border-color, fill, stroke, opacity, box-shadow, transform, filter, -webkit-text-decoration-color, -webkit-backdrop-filter;transition-property:color, background-color, border-color, text-decoration-color, fill, stroke, opacity, box-shadow, transform, filter, backdrop-filter;transition-property:color, background-color, border-color, text-decoration-color, fill, stroke, opacity, box-shadow, transform, filter, backdrop-filter, -webkit-text-decoration-color, -webkit-backdrop-filter;transition-timing-function:cubic-bezier(0.4, 0, 0.2, 1);transition-duration:150ms}.transition-all{transition-property:all;transition-timing-function:cubic-bezier(0.4, 0, 0.2, 1);transition-duration:150ms}.transition-colors{transition-property:color, background-color, border-color, fill, stroke, -webkit-text-decoration-color;transition-property:color, background-color, border-color, text-decoration-color, fill, stroke;transition-property:color, background-color, border-color, text-decoration-color, fill, stroke, -webkit-text-decoration-color;transition-timing-function:cubic-bezier(0.4, 0, 0.2, 1);transition-duration:150ms}.selection\:bg-blue-500 *::selection{--tw-bg-opacity:1;background-color:rgb(59 130 246 / var(--tw-bg-opacity, 1))}.selection\:text-white *::selection{--tw-text-opacity:1;color:rgb(255 255 255 / var(--tw-text-opacity, 1))}.selection\:bg-blue-500::selection{--tw-bg-opacity:1;background-color:rgb(59 130 246 / var(--tw-bg-opacity, 1))}.selection\:text-white::selection{--tw-text-opacity:1;color:rgb(255 255 255 / var(--tw-text-opacity, 1))}.hover\:bg-amber-500\/20:hover{background-color:rgb(245 158 11 / 0.2)}.hover\:bg-blue-500:hover{--tw-bg-opacity:1;background-color:rgb(59 130 246 / var(--tw-bg-opacity, 1))}.hover\:bg-blue-600\/30:hover{background-color:rgb(37 99 235 / 0.3)}.hover\:bg-emerald-400:hover{--tw-bg-opacity:1;background-color:rgb(52 211 153 / var(--tw-bg-opacity, 1))}.hover\:bg-emerald-500:hover{--tw-bg-opacity:1;background-color:rgb(16 185 129 / var(--tw-bg-opacity, 1))}.hover\:bg-emerald-600\/30:hover{background-color:rgb(5 150 105 / 0.3)}.hover\:bg-red-500\/20:hover{background-color:rgb(239 68 68 / 0.2)}.hover\:bg-slate-700:hover{--tw-bg-opacity:1;background-color:rgb(51 65 85 / var(--tw-bg-opacity, 1))}.hover\:bg-slate-800\/40:hover{background-color:rgb(30 41 59 / 0.4)}.hover\:from-emerald-500:hover{--tw-gradient-from:#10b981 var(--tw-gradient-from-position);--tw-gradient-to:rgb(16 185 129 / 0) var(--tw-gradient-to-position);--tw-gradient-stops:var(--tw-gradient-from), var(--tw-gradient-to)}.hover\:to-teal-500:hover{--tw-gradient-to:#14b8a6 var(--tw-gradient-to-position)}.hover\:text-white:hover{--tw-text-opacity:1;color:rgb(255 255 255 / var(--tw-text-opacity, 1))}.hover\:text-blue-400:hover{--tw-text-opacity:1;color:rgb(96 165 250 / var(--tw-text-opacity, 1))}.hover\:text-red-400:hover{--tw-text-opacity:1;color:rgb(248 113 113 / var(--tw-text-opacity, 1))}.focus\:outline-none:focus{outline:2px solid transparent;outline-offset:2px}.focus\:ring-2:focus{--tw-ring-offset-shadow:var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color);--tw-ring-shadow:var(--tw-ring-inset) 0 0 0 calc(2px + var(--tw-ring-offset-width)) var(--tw-ring-color);box-shadow:var(--tw-ring-offset-shadow), var(--tw-ring-shadow), var(--tw-shadow, 0 0 #0000)}.focus\:ring-blue-500:focus{--tw-ring-opacity:1;--tw-ring-color:rgb(59 130 246 / var(--tw-ring-opacity, 1))}.focus\:ring-emerald-500:focus{--tw-ring-opacity:1;--tw-ring-color:rgb(16 185 129 / var(--tw-ring-opacity, 1))}.active\:scale-95:active{--tw-scale-x:.95;--tw-scale-y:.95;transform:translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y))}@media (min-width: 640px){.sm\:inline{display:inline}.sm\:w-auto{width:auto}.sm\:flex-grow-0{flex-grow:0}.sm\:grid-cols-2{grid-template-columns:repeat(2, minmax(0, 1fr))}.sm\:p-5{padding:1.25rem}.sm\:px-6{padding-left:1.5rem;padding-right:1.5rem}.sm\:text-lg{font-size:1.125rem;line-height:1.75rem}.sm\:text-sm{font-size:0.875rem;line-height:1.25rem}.sm\:text-xl{font-size:1.25rem;line-height:1.75rem}}@media (min-width: 768px){.md\:w-auto{width:auto}.md\:grid-cols-4{grid-template-columns:repeat(4, minmax(0, 1fr))}.md\:flex-row{flex-direction:row}.md\:justify-start{justify-content:flex-start}}@media (min-width: 1024px){.lg\:grid-cols-3{grid-template-columns:repeat(3, minmax(0, 1fr))}.lg\:px-8{padding-left:2rem;padding-right:2rem}}</style></head>
<body class="font-sans bg-slate-950 text-slate-100 min-h-screen flex flex-col antialiased selection:bg-blue-500 selection:text-white">

    <!-- FLOATING TOAST NOTIFICATION CONTAINER -->
    <div id="toastContainer" class="fixed top-4 right-4 z-50 flex flex-col gap-2 pointer-events-none no-print"></div>

    <!-- TOP HEADER -->
    <header class="bg-slate-900/95 backdrop-blur border-b border-slate-800 sticky top-0 z-30 no-print">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-3.5 flex flex-col md:flex-row items-center justify-between gap-4">
            
            <!-- Logo & Info -->
            <div class="flex items-center space-x-3 w-full md:w-auto justify-between md:justify-start">
                <div class="flex items-center space-x-3">
                    <div class="bg-gradient-to-tr from-blue-600 to-indigo-600 p-2.5 rounded-xl shadow-lg shadow-blue-500/20 text-white">
                        <i class="fa-solid fa-camera-web text-2xl"></i>
                    </div>
                    <div>
                        <h1 class="text-lg sm:text-xl font-bold tracking-tight text-white flex items-center gap-2">
                            CCTV Pro Inventory
                            <span class="text-[10px] uppercase font-bold px-2 py-0.5 rounded bg-emerald-500/20 text-emerald-400 border border-emerald-500/30 flex items-center gap-1">
                                <i class="fa-solid fa-hard-drive"></i> Local Storage Saved
                            </span>
                        </h1>
                        <p class="text-xs text-slate-400">Wholesale &amp; Retail Price List Management • මිල ගණන් පද්ධතිය</p>
                    </div>
                </div>
            </div>

            <!-- Header Action Controls -->
            <div class="flex flex-wrap items-center gap-2 w-full md:w-auto justify-end">
                
                <!-- Share Center Main Modal Button -->
                <button onclick="openShareModal()" class="bg-gradient-to-r from-emerald-600 to-teal-600 hover:from-emerald-500 hover:to-teal-500 active:scale-95 text-white text-xs sm:text-sm font-semibold px-4 py-2.5 rounded-xl shadow-lg shadow-emerald-600/30 transition flex items-center justify-center gap-2">
                    <i class="fa-solid fa-share-nodes text-base"></i>
                    <span>Share System (බෙදාගන්න)</span>
                </button>

                <!-- Add Product Button -->
                <button onclick="openAddModal()" class="bg-blue-600 hover:bg-blue-500 active:scale-95 text-white text-xs sm:text-sm font-semibold px-4 py-2.5 rounded-xl shadow-lg shadow-blue-600/30 transition flex items-center justify-center gap-2">
                    <i class="fa-solid fa-plus-circle text-base"></i>
                    <span>+ Add Product</span>
                </button>

                <!-- Export Backup Button -->
                <button onclick="exportBackupJSON()" class="bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs sm:text-sm font-medium px-3 py-2.5 rounded-xl border border-slate-700 transition flex items-center gap-1.5" title="Export Backup JSON">
                    <i class="fa-solid fa-download text-blue-400"></i>
                    <span class="hidden sm:inline">Export</span>
                </button>

                <!-- Restore Backup Input Button -->
                <label class="bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs sm:text-sm font-medium px-3 py-2.5 rounded-xl border border-slate-700 transition cursor-pointer flex items-center gap-1.5" title="Restore Data JSON">
                    <i class="fa-solid fa-upload text-amber-400"></i>
                    <span class="hidden sm:inline">Restore</span>
                    <input type="file" id="importFileInput" accept=".json" onchange="importBackupJSON(event)" class="hidden">
                </label>

                <!-- Reset Button -->
                <button onclick="resetToDefaultData()" class="bg-red-500/10 hover:bg-red-500/20 text-red-400 border border-red-500/30 text-xs sm:text-sm font-medium px-3 py-2.5 rounded-xl transition flex items-center gap-1.5" title="Reset Default CCTV Products">
                    <i class="fa-solid fa-rotate-left"></i>
                    <span class="hidden sm:inline">Reset</span>
                </button>

                <!-- Print Button -->
                <button onclick="window.print()" class="bg-slate-800 hover:bg-slate-700 text-slate-200 text-xs sm:text-sm font-medium px-3 py-2.5 rounded-xl border border-slate-700 transition flex items-center gap-1.5">
                    <i class="fa-solid fa-print"></i>
                    <span class="hidden sm:inline">Print</span>
                </button>
            </div>
        </div>
    </header>

    <!-- PERSISTENCE GUARANTEE & LINK DETECTED BANNER -->
    <div id="urlSyncBanner" class="hidden bg-emerald-950/80 border-b border-emerald-700/50 no-print">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-2.5 flex items-center justify-between text-xs text-emerald-200 flex-wrap gap-2">
            <div class="flex items-center gap-2">
                <i class="fa-solid fa-link text-emerald-400 text-sm"></i>
                <span><strong>Shared Catalog Link Detected!</strong> Would you like to import these shared CCTV products into your list?</span>
            </div>
            <div class="flex items-center gap-2">
                <button onclick="acceptSharedUrlData()" class="bg-emerald-500 hover:bg-emerald-400 text-slate-950 font-bold px-3 py-1 rounded-lg transition text-xs">
                    Import Now
                </button>
                <button onclick="dismissUrlBanner()" class="text-slate-400 hover:text-white px-2 py-1 text-xs">
                    Dismiss
                </button>
            </div>
        </div>
    </div>

    <div class="bg-blue-950/60 border-b border-blue-800/50 no-print">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-2 flex items-center justify-between text-xs text-blue-200 flex-wrap gap-2">
            <div class="flex items-center gap-2">
                <i class="fa-solid fa-shield-check text-blue-400 text-sm"></i>
                <span><strong>100% Data Persistence:</strong> Saved inside browser storage (<code class="bg-blue-900/80 px-1.5 py-0.5 rounded text-blue-300 font-mono text-[11px]">localStorage</code>). Closing or refreshing the page will never erase your added products!</span>
            </div>
            <div class="text-slate-400 text-[11px]">
                Last Saved: <span id="lastSavedTimestamp" class="text-blue-300 font-semibold">Just Now</span>
            </div>
        </div>
    </div>

    <!-- MAIN CONTAINER -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6 flex-grow w-full">

        <!-- STATS DASHBOARD BAR -->
        <div class="grid grid-cols-2 md:grid-cols-4 gap-3.5 mb-6 no-print">
            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-4 shadow-sm">
                <div class="flex items-center justify-between text-slate-400 mb-1">
                    <span class="text-xs font-medium">මුළු භාණ්ඩ (Total Items)</span>
                    <i class="fa-solid fa-boxes-stacked text-blue-400 text-sm"></i>
                </div>
                <p id="statTotalItems" class="text-2xl font-bold text-white">1</p>
            </div>

            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-4 shadow-sm">
                <div class="flex items-center justify-between text-slate-400 mb-1">
                    <span class="text-xs font-medium">Active Brands</span>
                    <i class="fa-solid fa-tags text-purple-400 text-sm"></i>
                </div>
                <p id="statTotalBrands" class="text-2xl font-bold text-white">1</p>
            </div>

            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-4 shadow-sm">
                <div class="flex items-center justify-between text-slate-400 mb-1">
                    <span class="text-xs font-medium">Avg Profit Markup</span>
                    <i class="fa-solid fa-chart-line text-emerald-400 text-sm"></i>
                </div>
                <p id="statAvgMargin" class="text-2xl font-bold text-emerald-400">4.4%</p>
            </div>

            <div class="bg-slate-900 border border-slate-800 rounded-2xl p-4 shadow-sm">
                <div class="flex items-center justify-between text-slate-400 mb-1">
                    <span class="text-xs font-medium">Low / Out Stock</span>
                    <i class="fa-solid fa-triangle-exclamation text-amber-400 text-sm"></i>
                </div>
                <p id="statLowStock" class="text-2xl font-bold text-amber-400">0</p>
            </div>
        </div>

        <!-- PRINT HEADER (Only visible when printing) -->
        <div class="hidden print-only mb-6 text-center border-b border-slate-300 pb-4">
            <h1 class="text-2xl font-bold">CCTV Camera Equipment Wholesale &amp; Retail Price Catalog</h1>
            <p class="text-xs text-slate-500 mt-1">Generated Date: <span id="printDate">24/10/2026</span></p>
        </div>

        <!-- SEARCH AND FILTER CONTROLS -->
        <div class="bg-slate-900 border border-slate-800 rounded-2xl p-4 sm:p-5 mb-6 shadow-md no-print space-y-4">
            
            <!-- Live Search Bar -->
            <div class="relative w-full">
                <div class="absolute inset-y-0 left-0 pl-4 flex items-center pointer-events-none text-blue-400">
                    <i class="fa-solid fa-magnifying-glass text-lg"></i>
                </div>
                <input type="text" id="searchInput" onkeyup="filterProducts()" placeholder="Search CCTV model name, camera brand (Hikvision, Dahua, Imou, Ezviz, Tiandy) or category..." class="w-full pl-11 pr-12 py-3 bg-slate-950 border border-slate-700/80 rounded-xl text-slate-100 placeholder-slate-500 text-sm focus:outline-none focus:ring-2 focus:ring-blue-500 transition shadow-inner">
                <button onclick="clearSearch()" id="clearBtn" class="hidden absolute inset-y-0 right-0 pr-4 flex items-center text-slate-400 hover:text-white">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>

            <!-- Brand Filter Tabs & Category Dropdown -->
            <div class="flex flex-wrap items-center justify-between gap-3 pt-2 border-t border-slate-800">
                <!-- Brand Filter Chips -->
                <div class="flex flex-wrap items-center gap-1.5 text-xs sm:text-sm" id="brandTabs"><button onclick="setBrandFilter('ALL')" class="px-3 py-1.5 rounded-lg transition text-xs bg-blue-600 text-white font-bold shadow-md shadow-blue-500/20">සියලුම Brands</button><button onclick="setBrandFilter('Hikvision')" class="px-3 py-1.5 rounded-lg transition text-xs bg-slate-950 text-slate-400 hover:text-white border border-slate-800">Hikvision</button><button onclick="setBrandFilter('Dahua')" class="px-3 py-1.5 rounded-lg transition text-xs bg-slate-950 text-slate-400 hover:text-white border border-slate-800">Dahua</button><button onclick="setBrandFilter('Imou')" class="px-3 py-1.5 rounded-lg transition text-xs bg-slate-950 text-slate-400 hover:text-white border border-slate-800">Imou</button><button onclick="setBrandFilter('Ezviz')" class="px-3 py-1.5 rounded-lg transition text-xs bg-slate-950 text-slate-400 hover:text-white border border-slate-800">Ezviz</button><button onclick="setBrandFilter('Tiandy')" class="px-3 py-1.5 rounded-lg transition text-xs bg-slate-950 text-slate-400 hover:text-white border border-slate-800">Tiandy</button><button onclick="setBrandFilter('Baseus')" class="px-3 py-1.5 rounded-lg transition text-xs bg-slate-950 text-slate-400 hover:text-white border border-slate-800">Baseus</button><button onclick="setBrandFilter('HiLook')" class="px-3 py-1.5 rounded-lg transition text-xs bg-slate-950 text-slate-400 hover:text-white border border-slate-800">HiLook</button><button onclick="setBrandFilter('Other')" class="px-3 py-1.5 rounded-lg transition text-xs bg-slate-950 text-slate-400 hover:text-white border border-slate-800">Other</button></div>

                <div class="flex items-center gap-2 w-full sm:w-auto">
                    <!-- Category Filter -->
                    <select id="categoryFilter" onchange="filterProducts()" class="flex-grow sm:flex-grow-0 bg-slate-950 border border-slate-700 text-slate-300 text-xs sm:text-sm rounded-lg px-3 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500">
                        <option value="ALL">සියලුම Categories</option>
                        <option value="4G / SIM Camera &amp; Routers">4G / SIM Camera &amp; Routers</option>
                        <option value="IP Camera">IP Camera</option>
                        <option value="HD/Analog Camera">HD/Analog Camera</option>
                        <option value="Wi-Fi / Smart Camera">Wi-Fi / Smart Camera</option>
                        <option value="DVR / NVR">DVR / NVR Recorder</option>
                        <option value="Hard Disk / Storage">Hard Disk / Storage</option>
                        <option value="Cables &amp; Accessories">Cables &amp; Accessories</option>
                        <option value="Power Supply &amp; Connectors">Power Supply &amp; Connectors</option>
                    </select>

                    <!-- View Mode Toggles -->
                    <div class="flex bg-slate-950 border border-slate-700 rounded-lg p-0.5">
                        <button id="viewTableBtn" onclick="setView('table')" class="px-2.5 py-1.5 rounded text-xs font-medium bg-slate-800 text-blue-400" title="Table View">
                            <i class="fa-solid fa-table-list"></i>
                        </button>
                        <button id="viewGridBtn" onclick="setView('grid')" class="px-2.5 py-1.5 rounded text-xs font-medium text-slate-400 hover:text-white" title="Grid View">
                            <i class="fa-solid fa-border-all"></i>
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <!-- TABLE VIEW CONTAINER -->
        <div id="tableViewContainer" class="print-container bg-slate-900 border border-slate-800 rounded-2xl shadow-xl overflow-hidden">
            <div class="overflow-x-auto">
                <table class="w-full text-left border-collapse">
                    <thead>
                        <tr class="bg-slate-950/90 border-b border-slate-800 text-xs font-semibold text-slate-400 uppercase tracking-wider">
                            <th class="py-3.5 px-4 cursor-pointer hover:text-white" onclick="sortBy('brand')">
                                Brand <i class="fa-solid fa-sort text-[10px] ml-1"></i>
                            </th>
                            <th class="py-3.5 px-4 cursor-pointer hover:text-white" onclick="sortBy('name')">
                                භාණ්ඩයේ නම (Model / Name) <i class="fa-solid fa-sort text-[10px] ml-1"></i>
                            </th>
                            <th class="py-3.5 px-4">Category</th>
                            <th class="py-3.5 px-4 text-center">Stock</th>
                            <th class="py-3.5 px-4 text-center cursor-pointer hover:text-white" onclick="sortBy('wholesalePrice')">
                                තොග මිල (Wholesale) <i class="fa-solid fa-sort text-[10px] ml-1"></i>
                            </th>
                            <th class="py-3.5 px-4 text-center cursor-pointer hover:text-white" onclick="sortBy('retailPrice')">
                                සිල්ලර මිල (Retail) <i class="fa-solid fa-sort text-[10px] ml-1"></i>
                            </th>
                            <th class="py-3.5 px-4 text-center">Profit &amp; Margin</th>
                            <th class="py-3.5 px-4 text-center no-print">Actions</th>
                        </tr>
                    </thead>
                    <tbody id="productTableBody" class="divide-y divide-slate-800/60 text-sm">
                <tr class="hover:bg-slate-800/40 transition-colors">
                    <td class="py-3.5 px-4">
                        <span class="inline-block px-2.5 py-1 rounded-md text-xs font-bold uppercase bg-orange-500/20 text-orange-400 border border-orange-500/30">
                            Imou
                        </span>
                    </td>
                    <td class="py-3.5 px-4">
                        <div class="font-semibold text-white">Bulb  camera  with  bulb</div>
                        
                    </td>
                    <td class="py-3.5 px-4 text-xs text-slate-300">
                        <span class="bg-slate-800 px-2 py-1 rounded border border-slate-700/60 inline-block">Wi-Fi / Smart Camera</span>
                    </td>
                    <td class="py-3.5 px-4 text-center"><span class="px-2 py-0.5 rounded text-xs bg-emerald-500/10 text-emerald-400 border border-emerald-500/20">In Stock</span></td>
                    <td class="py-3.5 px-4 text-center">
                        <span class="badge-price inline-flex items-center gap-1 bg-emerald-500/10 border border-emerald-500/30 text-emerald-400 font-bold px-3 py-1.5 rounded-lg text-sm">
                            <span class="text-xs text-emerald-500/70">රු.</span>11,350.00
                        </span>
                    </td>
                    <td class="py-3.5 px-4 text-center">
                        <span class="badge-price inline-flex items-center gap-1 bg-blue-500/10 border border-blue-500/30 text-blue-400 font-bold px-3 py-1.5 rounded-lg text-sm">
                            <span class="text-xs text-blue-500/70">රු.</span>11,850.00
                        </span>
                    </td>
                    <td class="py-3.5 px-4 text-center text-xs">
                        <div class="font-semibold text-slate-200">+රු. 500.00</div>
                        <div class="text-[10px] text-emerald-400">4.4% markup</div>
                    </td>
                    <td class="py-3.5 px-4 text-center no-print">
                        <div class="flex items-center justify-center gap-1">
                            <button onclick="editProduct('cctv_1792839738890')" class="p-2 text-slate-400 hover:text-blue-400 rounded-lg transition" title="Edit">
                                <i class="fa-solid fa-pen-to-square"></i>
                            </button>
                            <button onclick="deleteProduct('cctv_1792839738890')" class="p-2 text-slate-400 hover:text-red-400 rounded-lg transition" title="Delete">
                                <i class="fa-solid fa-trash-can"></i>
                            </button>
                        </div>
                    </td>
                </tr>
            </tbody>
                </table>
            </div>
        </div>

        <!-- GRID CARDS VIEW CONTAINER -->
        <div id="gridViewContainer" class="hidden grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
            <!-- JS Injected -->
        </div>

        <!-- EMPTY STATE -->
        <div id="emptyState" class="hidden py-16 text-center bg-slate-900 border border-slate-800 rounded-2xl">
            <div class="w-16 h-16 bg-slate-800 text-slate-500 rounded-full flex items-center justify-center mx-auto mb-4 text-2xl">
                <i class="fa-solid fa-video-slash"></i>
            </div>
            <h3 class="text-base font-semibold text-slate-300">කිසිදු CCTV උපකරණයක් හමුවූයේ නැත</h3>
            <p class="text-xs text-slate-500 mt-1">සෙවුම් පදය වෙනස් කර බලන්න හෝ අලුත් එකක් එකතු කරන්න.</p>
        </div>

    </main>

    <!-- SHARE CENTER MODAL -->
    <div id="shareModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-sm z-50 flex items-center justify-center p-4 no-print">
        <div class="bg-slate-900 border border-slate-800 rounded-2xl shadow-2xl w-full max-w-xl overflow-hidden transform transition-all">
            
            <div class="bg-slate-950 px-6 py-4 border-b border-slate-800 flex items-center justify-between">
                <h3 class="font-bold text-base sm:text-lg text-white flex items-center gap-2">
                    <i class="fa-solid fa-share-nodes text-emerald-400"></i>
                    <span>Share &amp; Multi-Device Sync Center (මිල ලැයිස්තුව යවන්න)</span>
                </h3>
                <button onclick="closeShareModal()" class="text-slate-400 hover:text-white transition">
                    <i class="fa-solid fa-xmark text-xl"></i>
                </button>
            </div>

            <div class="p-6 space-y-6">
                <!-- Method 1: WhatsApp / Direct Hash Link -->
                <div class="bg-slate-950 border border-slate-800 rounded-xl p-4 space-y-3">
                    <div class="flex items-center justify-between">
                        <span class="text-xs font-bold text-emerald-400 uppercase tracking-wider flex items-center gap-2">
                            <i class="fa-brands fa-whatsapp text-lg"></i>
                            Method 1: Instant WhatsApp / Compressed Hash Link
                        </span>
                        <span class="text-[10px] bg-emerald-500/10 text-emerald-400 border border-emerald-500/20 px-2 py-0.5 rounded">No Hosting Needed</span>
                    </div>
                    <p class="text-xs text-slate-400">Generates a special link containing your entire product list embedded inside it. Friends click the link to instantly import all items into their browser!</p>
                    <div class="flex items-center gap-2">
                        <input type="text" id="shareUrlInput" readonly="" class="w-full px-3 py-2 bg-slate-900 border border-slate-700 rounded-lg text-xs text-slate-300 font-mono select-all focus:outline-none">
                        <button onclick="copyShareUrl()" class="px-3.5 py-2 bg-emerald-600 hover:bg-emerald-500 text-slate-950 font-bold text-xs rounded-lg transition shrink-0 flex items-center gap-1">
                            <i class="fa-solid fa-copy"></i> Copy
                        </button>
                    </div>
                    <div class="flex items-center gap-2 pt-1">
                        <button onclick="shareToWhatsApp()" class="w-full py-2 bg-emerald-600/20 hover:bg-emerald-600/30 text-emerald-400 border border-emerald-500/30 text-xs font-semibold rounded-lg transition flex items-center justify-center gap-2">
                            <i class="fa-brands fa-whatsapp text-sm"></i> Share via WhatsApp
                        </button>
                    </div>
                </div>

                <!-- Method 2 & 3: Mobile Native Share & QR Code -->
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <!-- Method 2: Mobile Native Web Share -->
                    <div class="bg-slate-950 border border-slate-800 rounded-xl p-4 flex flex-col justify-between">
                        <div>
                            <span class="text-xs font-bold text-blue-400 uppercase tracking-wider block mb-1">
                                <i class="fa-solid fa-mobile-screen-button mr-1"></i> Method 2: Mobile Share Sheet
                            </span>
                            <p class="text-xs text-slate-400 mb-3">Uses phone native share dialog (WhatsApp, Telegram, Email, Bluetooth).</p>
                        </div>
                        <button onclick="triggerNativeShare()" class="w-full py-2 bg-blue-600/20 hover:bg-blue-600/30 text-blue-400 border border-blue-500/30 text-xs font-semibold rounded-lg transition flex items-center justify-center gap-2">
                            <i class="fa-solid fa-share-nodes"></i> Trigger Phone Share Sheet
                        </button>
                    </div>

                    <!-- Method 3: QR Code Generator -->
                    <div class="bg-slate-950 border border-slate-800 rounded-xl p-4 flex flex-col items-center justify-center text-center">
                        <span class="text-xs font-bold text-purple-400 uppercase tracking-wider block mb-2">
                            <i class="fa-solid fa-qrcode mr-1"></i> Method 3: QR Code
                        </span>
                        <div id="qrcode" class="p-2 bg-white rounded-lg mb-2 flex items-center justify-center min-h-[120px] min-w-[120px]" title="file:///C:/Users/C%20MOS/Downloads/cctv_inventory_price_list_system%20(3).html#data=JTVCJTdCJTIyaWQlMjIlM0ElMjJjY3R2XzE3OTI4Mzk3Mzg4OTAlMjIlMkMlMjJicmFuZCUyMiUzQSUyMkltb3UlMjIlMkMlMjJjYXRlZ29yeSUyMiUzQSUyMldpLUZpJTIwJTJGJTIwU21hcnQlMjBDYW1lcmElMjIlMkMlMjJuYW1lJTIyJTNBJTIyQnVsYiUyMCUyMGNhbWVyYSUyMCUyMHdpdGglMjAlMjBidWxiJTIyJTJDJTIyd2hvbGVzYWxlUHJpY2UlMjIlM0ExMTM1MCUyQyUyMnJldGFpbFByaWNlJTIyJTNBMTE4NTAlMkMlMjJzdG9jayUyMiUzQSUyMkluJTIwU3RvY2slMjIlMkMlMjJ3YXJyYW50eSUyMiUzQSUyMjMlMjBZZWFycyUyMFdhcnJhbnR5JTIyJTJDJTIyZGVzY3JpcHRpb24lMjIlM0ElMjIlMjIlMkMlMjJ1cGRhdGVkQXQlMjIlM0ElMjIyMDI2LTEwLTI0VDExJTNBMDIlM0ExOC44OTBaJTIyJTdEJTVE"><canvas width="128" height="128" style="display: none;"></canvas><img src="data:image/png;base64,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" style="display: block;"></div>
                        <p class="text-[11px] text-slate-500">Scan with phone camera to transfer catalog</p>
                    </div>
                </div>

                <!-- Method 4: Standalone Offline HTML Exporter -->
                <div class="bg-slate-950 border border-slate-800 rounded-xl p-4 space-y-2">
                    <span class="text-xs font-bold text-amber-400 uppercase tracking-wider block">
                        <i class="fa-solid fa-file-code mr-1"></i> Method 4: Download Offline Single HTML File
                    </span>
                    <p class="text-xs text-slate-400">Downloads a complete, self-contained `.html` website file pre-loaded with your current inventory. Send this file directly to friends via WhatsApp or email.</p>
                    <button onclick="exportStandaloneHTML()" class="w-full py-2.5 bg-amber-500/10 hover:bg-amber-500/20 text-amber-400 border border-amber-500/30 text-xs font-semibold rounded-lg transition flex items-center justify-center gap-2">
                        <i class="fa-solid fa-download"></i> Download Standalone HTML App (.html)
                    </button>
                </div>

            </div>
        </div>
    </div>

    <!-- ADD / EDIT PRODUCT MODAL -->
    <div id="productModal" class="fixed inset-0 bg-slate-950/80 backdrop-blur-sm z-50 flex items-center justify-center hidden p-4 no-print">
        <div class="bg-slate-900 border border-slate-800 rounded-2xl shadow-2xl w-full max-w-xl overflow-hidden transform transition-all">
            
            <div class="bg-slate-950 px-6 py-4 border-b border-slate-800 flex items-center justify-between">
                <h3 id="modalTitle" class="font-bold text-base sm:text-lg text-white flex items-center gap-2">
                    <i class="fa-solid fa-video text-blue-500"></i>
                    <span>නව CCTV උපකරණයක් එකතු කරන්න</span>
                </h3>
                <button onclick="closeModal()" class="text-slate-400 hover:text-white transition">
                    <i class="fa-solid fa-xmark text-xl"></i>
                </button>
            </div>

            <form id="productForm" onsubmit="handleProductSubmit(event)" class="p-6 space-y-4">
                <input type="hidden" id="productId">

                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <!-- Brand -->
                    <div>
                        <label class="block text-xs font-semibold text-slate-400 uppercase mb-1">Brand *</label>
                        <select id="productBrand" required="" class="w-full px-3.5 py-2.5 bg-slate-950 border border-slate-700 rounded-xl text-sm text-white focus:ring-2 focus:ring-blue-500 focus:outline-none">
                            <option value="Hikvision">Hikvision</option>
                            <option value="Dahua">Dahua</option>
                            <option value="Imou">Imou</option>
                            <option value="Ezviz">Ezviz</option>
                            <option value="Tiandy">Tiandy</option>
                            <option value="Baseus">Baseus</option>
                            <option value="HiLook">HiLook</option>
                            <option value="Other">Other</option>
                        </select>
                    </div>

                    <!-- Category -->
                    <div>
                        <label class="block text-xs font-semibold text-slate-400 uppercase mb-1">Category *</label>
                        <select id="productCategory" required="" class="w-full px-3.5 py-2.5 bg-slate-950 border border-slate-700 rounded-xl text-sm text-white focus:ring-2 focus:ring-blue-500 focus:outline-none">
                            <option value="4G / SIM Camera &amp; Routers">4G / SIM Camera &amp; Routers</option>
                            <option value="IP Camera">IP Camera</option>
                            <option value="HD/Analog Camera">HD/Analog Camera</option>
                            <option value="Wi-Fi / Smart Camera">Wi-Fi / Smart Camera</option>
                            <option value="DVR / NVR">DVR / NVR Recorder</option>
                            <option value="Hard Disk / Storage">Hard Disk / Storage</option>
                            <option value="Cables &amp; Accessories">Cables &amp; Accessories</option>
                            <option value="Power Supply &amp; Connectors">Power Supply &amp; Connectors</option>
                        </select>
                    </div>
                </div>

                <!-- Item / Camera Name & Model -->
                <div>
                    <label class="block text-xs font-semibold text-slate-400 uppercase mb-1">Product Name / Model Code *</label>
                    <input type="text" id="productName" required="" placeholder="eg. Hikvision 2MP Turbo HD Outdoor Bullet DS-2CE16D0T" class="w-full px-3.5 py-2.5 bg-slate-950 border border-slate-700 rounded-xl text-sm text-white focus:ring-2 focus:ring-blue-500 focus:outline-none placeholder-slate-600">
                </div>

                <!-- Wholesale & Retail Prices -->
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-semibold text-emerald-400 uppercase mb-1">තොග මිල (Wholesale Price - LKR) *</label>
                        <div class="relative">
                            <span class="absolute inset-y-0 left-0 pl-3 flex items-center text-slate-500 text-xs">රු.</span>
                            <input type="number" id="productWholesalePrice" step="0.01" required="" placeholder="0.00" oninput="calculateModalMargin()" class="w-full pl-10 pr-3 py-2.5 bg-slate-950 border border-emerald-500/40 rounded-xl text-sm text-white focus:ring-2 focus:ring-emerald-500 focus:outline-none">
                        </div>
                    </div>

                    <div>
                        <label class="block text-xs font-semibold text-blue-400 uppercase mb-1">සිල්ලර මිල (Retail Price - LKR) *</label>
                        <div class="relative">
                            <span class="absolute inset-y-0 left-0 pl-3 flex items-center text-slate-500 text-xs">රු.</span>
                            <input type="number" id="productRetailPrice" step="0.01" required="" placeholder="0.00" oninput="calculateModalMargin()" class="w-full pl-10 pr-3 py-2.5 bg-slate-950 border border-blue-500/40 rounded-xl text-sm text-white focus:ring-2 focus:ring-blue-500 focus:outline-none">
                        </div>
                    </div>
                </div>

                <!-- Live Margin Calculation Preview Bar -->
                <div id="marginPreview" class="bg-slate-950 border border-slate-800 rounded-xl p-3 text-xs flex justify-between items-center text-slate-400">
                    <span>Estimated Profit: <strong id="previewProfit" class="text-white">රු. 0.00</strong></span>
                    <span>Markup Percentage: <strong id="previewMarkup" class="text-emerald-400">0%</strong></span>
                </div>

                <!-- Stock Quantity & Warranty -->
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-semibold text-slate-400 uppercase mb-1">Stock Status</label>
                        <select id="productStock" class="w-full px-3.5 py-2.5 bg-slate-950 border border-slate-700 rounded-xl text-sm text-white focus:ring-2 focus:ring-blue-500 focus:outline-none">
                            <option value="In Stock">In Stock</option>
                            <option value="Low Stock">Low Stock</option>
                            <option value="Out of Stock">Out of Stock</option>
                        </select>
                    </div>

                    <div>
                        <label class="block text-xs font-semibold text-slate-400 uppercase mb-1">Warranty Info</label>
                        <input type="text" id="productWarranty" placeholder="eg. 2 Years Warranty" class="w-full px-3.5 py-2.5 bg-slate-950 border border-slate-700 rounded-xl text-sm text-white focus:ring-2 focus:ring-blue-500 focus:outline-none placeholder-slate-600">
                    </div>
                </div>

                <!-- Description -->
                <div>
                    <label class="block text-xs font-semibold text-slate-400 uppercase mb-1">Key Specs / Description</label>
                    <textarea id="productDescription" rows="2" placeholder="eg. 20m Smart IR Night Vision, IP67 Weatherproof, 1080P Full HD..." class="w-full px-3.5 py-2.5 bg-slate-950 border border-slate-700 rounded-xl text-sm text-white focus:ring-2 focus:ring-blue-500 focus:outline-none placeholder-slate-600"></textarea>
                </div>

                <!-- Actions -->
                <div class="flex items-center justify-end gap-3 pt-4 border-t border-slate-800">
                    <button type="button" onclick="closeModal()" class="px-4 py-2.5 bg-slate-800 hover:bg-slate-700 text-slate-300 text-sm font-medium rounded-xl transition">
                        Cancel
                    </button>
                    <button type="submit" class="px-5 py-2.5 bg-blue-600 hover:bg-blue-500 active:scale-95 text-white text-sm font-semibold rounded-xl transition shadow-lg shadow-blue-600/30 flex items-center gap-2">
                        <i class="fa-solid fa-floppy-disk"></i>
                        <span>සුරකින්න (Save Product)</span>
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- CORE JAVASCRIPT LOGIC -->
    <script>
        const STORAGE_KEY = 'cctv_inventory_v2';

        const DEFAULT_PRODUCTS = [
            { id: '101', brand: 'Dahua', name: 'Dahua 4G Solar Powered Security Camera DH-IPC-HFW2231T-ZS-4G', category: '4G / SIM Camera & Routers', wholesalePrice: 38500, retailPrice: 46000, stock: 'In Stock', warranty: '2 Years Warranty', description: 'Standalone Solar Panel, Integrated 4G LTE Module, PIR Human Detection, IP67' },
            { id: '102', brand: 'Hikvision', name: 'Hikvision 4G LTE Speed Dome PTZ DS-2DE4225IW-DE(S6)/4G', category: '4G / SIM Camera & Routers', wholesalePrice: 82000, retailPrice: 98000, stock: 'In Stock', warranty: '2 Years Warranty', description: '25x Optical Zoom, Built-in 4G SIM Slot, 100m IR Night Vision' },
            { id: '103', brand: 'Imou', name: 'Imou Cruiser 4G Outdoor Pan & Tilt Camera', category: '4G / SIM Camera & Routers', wholesalePrice: 19500, retailPrice: 24000, stock: 'In Stock', warranty: '2 Years Warranty', description: 'Supports 4G SIM Card, Smart Color Night Vision, Two-Way Talk, IP66' },
            { id: '104', brand: 'Tiandy', name: 'Tiandy 4G 2MP Starlight Outdoor Bullet TC-C32XN-4G', category: '4G / SIM Camera & Routers', wholesalePrice: 14800, retailPrice: 18500, stock: 'Low Stock', warranty: '2 Years Warranty', description: '4G LTE SIM Card Support, Starlight Low-light Performance, Metal Housing' },
            { id: '105', brand: 'Hikvision', name: 'Hikvision 2MP Outdoor Bullet DS-2CE16D0T-IRPF', category: 'HD/Analog Camera', wholesalePrice: 4200, retailPrice: 5800, stock: 'In Stock', warranty: '2 Years Warranty', description: '20m Smart IR, IP67 Weatherproof, 1080P Full HD' },
            { id: '106', brand: 'Hikvision', name: 'Hikvision 4-Channel Turbo HD DVR DS-7204HGHI-K1', category: 'DVR / NVR', wholesalePrice: 11800, retailPrice: 14900, stock: 'In Stock', warranty: '2 Years Warranty', description: 'H.265 Pro+ compression, supports HDTVI/AHD/CVI/CVBS/IP' },
            { id: '107', brand: 'Dahua', name: 'Dahua 2MP Cooper HD Bullet DH-HAC-B1A21P', category: 'HD/Analog Camera', wholesalePrice: 3950, retailPrice: 5400, stock: 'In Stock', warranty: '2 Years Warranty', description: '20m Smart IR, HD and SD output switchable' },
            { id: '108', brand: 'Ezviz', name: 'Ezviz C6N 1080P Smart Wi-Fi Pan & Tilt Camera', category: 'Wi-Fi / Smart Camera', wholesalePrice: 7800, retailPrice: 9900, stock: 'In Stock', warranty: '2 Years Warranty', description: 'Smart IR Night Vision, Motion Tracking, MicroSD Slot' },
            { id: '109', brand: 'Baseus', name: 'Baseus 4G SIM Outdoor CPE Wireless Router 300Mbps', category: '4G / SIM Camera & Routers', wholesalePrice: 8900, retailPrice: 11500, stock: 'In Stock', warranty: '1 Year Warranty', description: 'Plug & Play 4G LTE Outdoor CPE Router for Remote CCTV Sites' },
            { id: '110', brand: 'Other', name: 'Seagate SkyHawk 1TB CCTV Hard Drive', category: 'Hard Disk / Storage', wholesalePrice: 14500, retailPrice: 17500, stock: 'In Stock', warranty: '2 Years Warranty', description: '24x7 surveillance workloads' }
        ];

        let products = [];
        let activeBrandFilter = 'ALL';
        let currentView = 'table';
        let currentSort = { key: 'name', dir: 'asc' };
        let pendingUrlProducts = null;

        window.addEventListener('DOMContentLoaded', () => {
            document.getElementById('printDate').innerText = new Date().toLocaleDateString('en-GB');
            loadProductsFromLocalStorage();
            checkForUrlSharedData();
        });

        // 1. READ FROM LOCALSTORAGE
        function loadProductsFromLocalStorage() {
            try {
                const stored = localStorage.getItem(STORAGE_KEY);
                if (stored) {
                    products = JSON.parse(stored);
                } else {
                    products = [...DEFAULT_PRODUCTS];
                    saveProductsToLocalStorage(false);
                }
            } catch (e) {
                products = [...DEFAULT_PRODUCTS];
            }
            renderBrandTabs();
            renderView();
            updateStats();
        }

        // 2. WRITE TO LOCALSTORAGE
        function saveProductsToLocalStorage(showToast = true, toastMsg = "Product Saved Successfully!") {
            try {
                localStorage.setItem(STORAGE_KEY, JSON.stringify(products));
                document.getElementById('lastSavedTimestamp').innerText = new Date().toLocaleTimeString();
                if (showToast) showSuccessToast(toastMsg);
            } catch (e) {
                alert("Storage error! Could not save data locally.");
            }
        }

        // 3. CHECK FOR SHARED DATA IN URL HASH (#data=...)
        function checkForUrlSharedData() {
            const hash = window.location.hash;
            if (hash && hash.startsWith('#data=')) {
                try {
                    const encodedStr = hash.replace('#data=', '');
                    const jsonStr = decodeURIComponent(atob(encodedStr));
                    const imported = JSON.parse(jsonStr);
                    if (Array.isArray(imported) && imported.length > 0) {
                        pendingUrlProducts = imported;
                        document.getElementById('urlSyncBanner').classList.remove('hidden');
                    }
                } catch (err) {
                    console.error("Failed to parse URL hash data", err);
                }
            }
        }

        function acceptSharedUrlData() {
            if (pendingUrlProducts) {
                products = pendingUrlProducts;
                saveProductsToLocalStorage(true, "Shared catalog imported successfully!");
                renderBrandTabs();
                renderView();
                updateStats();
                dismissUrlBanner();
            }
        }

        function dismissUrlBanner() {
            document.getElementById('urlSyncBanner').classList.add('hidden');
            history.replaceState(null, null, ' ');
        }

        // 4. SHARE CENTER LOGIC
        function generateSharedUrl() {
            try {
                const minimalList = products.map(p => ({
                    b: p.brand,
                    c: p.category,
                    n: p.name,
                    w: p.wholesalePrice,
                    r: p.retailPrice,
                    s: p.stock,
                    wr: p.warranty,
                    d: p.description
                }));
                const jsonStr = JSON.stringify(products);
                const encoded = btoa(encodeURIComponent(jsonStr));
                const baseUrl = window.location.href.split('#')[0];
                return `${baseUrl}#data=${encoded}`;
            } catch (e) {
                return window.location.href;
            }
        }

        function openShareModal() {
            const shareUrl = generateSharedUrl();
            document.getElementById('shareUrlInput').value = shareUrl;

            // Generate QR Code
            const qrContainer = document.getElementById('qrcode');
            qrContainer.innerHTML = '';
            new QRCode(qrContainer, {
                text: shareUrl,
                width: 128,
                height: 128,
                colorDark : "#0f172a",
                colorLight : "#ffffff",
                correctLevel : QRCode.CorrectLevel.L
            });

            document.getElementById('shareModal').classList.remove('hidden');
        }

        function closeShareModal() {
            document.getElementById('shareModal').classList.add('hidden');
        }

        function copyShareUrl() {
            const input = document.getElementById('shareUrlInput');
            input.select();
            document.execCommand('copy');
            showSuccessToast("Share URL Copied to Clipboard!");
        }

        function shareToWhatsApp() {
            const url = document.getElementById('shareUrlInput').value;
            const text = `📁 *CCTV Camera Equipment Price Catalog*\n\nContains ${products.length} CCTV products with wholesale & retail prices.\n\nClick to open & import directly: ${url}`;
            window.open(`https://api.whatsapp.com/send?text=${encodeURIComponent(text)}`, '_blank');
        }

        function triggerNativeShare() {
            const shareUrl = document.getElementById('shareUrlInput').value;
            if (navigator.share) {
                navigator.share({
                    title: 'CCTV Camera Price Catalog',
                    text: `CCTV Equipment Inventory Price List (${products.length} Items)`,
                    url: shareUrl
                }).catch(() => {});
            } else {
                copyShareUrl();
            }
        }

        function exportStandaloneHTML() {
            const currentDoc = "<!DOCTYPE html>\n" + document.documentElement.outerHTML;
            const blob = new Blob([currentDoc], { type: 'text/html' });
            const anchor = document.createElement('a');
            anchor.href = URL.createObjectURL(blob);
            anchor.download = `cctv_pricelist_system_${new Date().toISOString().slice(0,10)}.html`;
            document.body.appendChild(anchor);
            anchor.click();
            anchor.remove();
            showSuccessToast("Standalone HTML File Exported!");
        }

        // 5. TOAST NOTIFICATION
        function showSuccessToast(msg) {
            const container = document.getElementById('toastContainer');
            const toast = document.createElement('div');
            toast.className = "toast-animate bg-emerald-500 text-slate-950 font-bold px-4 py-3 rounded-xl shadow-2xl flex items-center gap-3 border border-emerald-400 text-sm";
            toast.innerHTML = `<i class="fa-solid fa-circle-check text-lg"></i><span>${msg}</span>`;
            container.appendChild(toast);

            setTimeout(() => {
                toast.style.opacity = '0';
                toast.style.transition = 'opacity 0.3s ease';
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        // 6. PRODUCT SUBMIT, EDIT & DELETE
        function handleProductSubmit(event) {
            event.preventDefault();

            const id = document.getElementById('productId').value;
            const productData = {
                brand: document.getElementById('productBrand').value,
                category: document.getElementById('productCategory').value,
                name: document.getElementById('productName').value.trim(),
                wholesalePrice: parseFloat(document.getElementById('productWholesalePrice').value) || 0,
                retailPrice: parseFloat(document.getElementById('productRetailPrice').value) || 0,
                stock: document.getElementById('productStock').value,
                warranty: document.getElementById('productWarranty').value.trim(),
                description: document.getElementById('productDescription').value.trim(),
                updatedAt: new Date().toISOString()
            };

            let isEdit = false;
            if (id) {
                const idx = products.findIndex(p => p.id === id);
                if (idx !== -1) {
                    products[idx] = { id, ...productData };
                    isEdit = true;
                }
            } else {
                products.unshift({ id: 'cctv_' + Date.now(), ...productData });
            }

            saveProductsToLocalStorage(true, isEdit ? "Product Updated!" : "Product Saved!");
            renderBrandTabs();
            renderView();
            updateStats();
            closeModal();
        }

        function deleteProduct(id) {
            if (!confirm('ඔබට මෙම CCTV උපකරණය පද්ධතියෙන් ඉවත් කිරීමට අවශ්‍යද?')) return;
            products = products.filter(p => p.id !== id);
            saveProductsToLocalStorage(true, "Product Deleted!");
            renderBrandTabs();
            renderView();
            updateStats();
        }

        function resetToDefaultData() {
            if (confirm('ඔබට නැවත මුල් Sample Products ලැයිස්තුව Restore කිරීමට අවශ්‍යද?')) {
                products = [...DEFAULT_PRODUCTS];
                saveProductsToLocalStorage(true, "Reset to default products!");
                renderBrandTabs();
                renderView();
                updateStats();
            }
        }

        function exportBackupJSON() {
            const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(products, null, 2));
            const anchor = document.createElement('a');
            anchor.setAttribute("href", dataStr);
            anchor.setAttribute("download", `cctv_inventory_backup_${new Date().toISOString().slice(0,10)}.json`);
            document.body.appendChild(anchor);
            anchor.click();
            anchor.remove();
            showSuccessToast("Backup Exported!");
        }

        function importBackupJSON(event) {
            const file = event.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = function(e) {
                try {
                    const imported = JSON.parse(e.target.result);
                    if (Array.isArray(imported)) {
                        if (confirm(`Backup ගොනුවේ ඇති උපකරණ ${imported.length} ක් Restore කිරීමට අවශ්‍යද?`)) {
                            products = imported;
                            saveProductsToLocalStorage(true, "Backup Restored!");
                            renderBrandTabs();
                            renderView();
                            updateStats();
                        }
                    }
                } catch(err) {
                    alert("අවලංගු JSON ගොනුවකි.");
                }
            };
            reader.readAsText(file);
        }

        // 7. SEARCH, FILTER & RENDER
        function getFilteredProducts() {
            const query = (document.getElementById('searchInput').value || '').toLowerCase().trim();
            const cat = document.getElementById('categoryFilter').value;

            return products.filter(p => {
                const matchBrand = (activeBrandFilter === 'ALL') || (p.brand.toLowerCase() === activeBrandFilter.toLowerCase());
                const matchCat = (cat === 'ALL') || (p.category === cat);
                const matchQ = !query || 
                    p.name.toLowerCase().includes(query) || 
                    p.brand.toLowerCase().includes(query) || 
                    p.category.toLowerCase().includes(query) ||
                    (p.description && p.description.toLowerCase().includes(query));

                return matchBrand && matchCat && matchQ;
            });
        }

        function filterProducts() {
            const val = document.getElementById('searchInput').value;
            document.getElementById('clearBtn').classList.toggle('hidden', val.length === 0);
            renderView();
        }

        function clearSearch() {
            document.getElementById('searchInput').value = '';
            filterProducts();
        }

        function renderView() {
            let list = getFilteredProducts();

            list.sort((a, b) => {
                let vA = a[currentSort.key];
                let vB = b[currentSort.key];
                if (typeof vA === 'string') vA = vA.toLowerCase();
                if (typeof vB === 'string') vB = vB.toLowerCase();
                if (vA < vB) return currentSort.dir === 'asc' ? -1 : 1;
                if (vA > vB) return currentSort.dir === 'asc' ? 1 : -1;
                return 0;
            });

            const emptyState = document.getElementById('emptyState');
            if (list.length === 0) {
                document.getElementById('productTableBody').innerHTML = '';
                document.getElementById('gridViewContainer').innerHTML = '';
                emptyState.classList.remove('hidden');
                return;
            }
            emptyState.classList.add('hidden');

            if (currentView === 'table') {
                renderTable(list);
            } else {
                renderGrid(list);
            }
        }

        function renderTable(list) {
            document.getElementById('productTableBody').innerHTML = list.map(p => {
                const profit = p.retailPrice - p.wholesalePrice;
                const markupPct = p.wholesalePrice > 0 ? ((profit / p.wholesalePrice) * 100).toFixed(1) : 0;

                return `
                <tr class="hover:bg-slate-800/40 transition-colors">
                    <td class="py-3.5 px-4">
                        <span class="inline-block px-2.5 py-1 rounded-md text-xs font-bold uppercase ${getBrandClass(p.brand)}">
                            ${p.brand}
                        </span>
                    </td>
                    <td class="py-3.5 px-4">
                        <div class="font-semibold text-white">${escapeHtml(p.name)}</div>
                        ${p.description ? `<div class="text-xs text-slate-400 mt-0.5">${escapeHtml(p.description)}</div>` : ''}
                    </td>
                    <td class="py-3.5 px-4 text-xs text-slate-300">
                        <span class="bg-slate-800 px-2 py-1 rounded border border-slate-700/60 inline-block">${escapeHtml(p.category)}</span>
                    </td>
                    <td class="py-3.5 px-4 text-center">${getStockBadge(p.stock)}</td>
                    <td class="py-3.5 px-4 text-center">
                        <span class="badge-price inline-flex items-center gap-1 bg-emerald-500/10 border border-emerald-500/30 text-emerald-400 font-bold px-3 py-1.5 rounded-lg text-sm">
                            <span class="text-xs text-emerald-500/70">රු.</span>${formatNum(p.wholesalePrice)}
                        </span>
                    </td>
                    <td class="py-3.5 px-4 text-center">
                        <span class="badge-price inline-flex items-center gap-1 bg-blue-500/10 border border-blue-500/30 text-blue-400 font-bold px-3 py-1.5 rounded-lg text-sm">
                            <span class="text-xs text-blue-500/70">රු.</span>${formatNum(p.retailPrice)}
                        </span>
                    </td>
                    <td class="py-3.5 px-4 text-center text-xs">
                        <div class="font-semibold text-slate-200">+රු. ${formatNum(profit)}</div>
                        <div class="text-[10px] text-emerald-400">${markupPct}% markup</div>
                    </td>
                    <td class="py-3.5 px-4 text-center no-print">
                        <div class="flex items-center justify-center gap-1">
                            <button onclick="editProduct('${p.id}')" class="p-2 text-slate-400 hover:text-blue-400 rounded-lg transition" title="Edit">
                                <i class="fa-solid fa-pen-to-square"></i>
                            </button>
                            <button onclick="deleteProduct('${p.id}')" class="p-2 text-slate-400 hover:text-red-400 rounded-lg transition" title="Delete">
                                <i class="fa-solid fa-trash-can"></i>
                            </button>
                        </div>
                    </td>
                </tr>
            `}).join('');
        }

        function renderGrid(list) {
            document.getElementById('gridViewContainer').innerHTML = list.map(p => {
                const profit = p.retailPrice - p.wholesalePrice;
                const markupPct = p.wholesalePrice > 0 ? ((profit / p.wholesalePrice) * 100).toFixed(1) : 0;

                return `
                <div class="bg-slate-900 border border-slate-800 rounded-2xl p-5 shadow-lg flex flex-col justify-between">
                    <div>
                        <div class="flex items-center justify-between mb-3">
                            <span class="px-2.5 py-1 rounded-md text-xs font-bold uppercase ${getBrandClass(p.brand)}">${p.brand}</span>
                            ${getStockBadge(p.stock)}
                        </div>
                        <h4 class="font-bold text-white text-base mb-1">${escapeHtml(p.name)}</h4>
                        <p class="text-xs text-slate-400 mb-4 line-clamp-2">${escapeHtml(p.description || 'N/A')}</p>
                    </div>

                    <div class="pt-3 border-t border-slate-800 space-y-2">
                        <div class="flex items-center justify-between">
                            <span class="text-xs text-slate-400">තොග මිල (Wholesale):</span>
                            <span class="text-emerald-400 font-bold text-base">රු. ${formatNum(p.wholesalePrice)}</span>
                        </div>
                        <div class="flex items-center justify-between">
                            <span class="text-xs text-slate-400">සිල්ලර මිල (Retail):</span>
                            <span class="text-blue-400 font-bold text-base">රු. ${formatNum(p.retailPrice)}</span>
                        </div>
                        <div class="flex items-center justify-between text-xs text-slate-500 pt-1">
                            <span>Profit:</span>
                            <span class="text-amber-400 font-medium">+රු. ${formatNum(profit)} (${markupPct}%)</span>
                        </div>

                        <div class="flex items-center justify-end gap-2 pt-3 no-print">
                            <button onclick="editProduct('${p.id}')" class="px-3 py-1.5 bg-slate-800 text-slate-300 text-xs rounded-lg transition hover:bg-slate-700">
                                <i class="fa-solid fa-pen-to-square mr-1"></i> Edit
                            </button>
                            <button onclick="deleteProduct('${p.id}')" class="px-3 py-1.5 bg-red-500/10 text-red-400 text-xs rounded-lg transition hover:bg-red-500/20">
                                <i class="fa-solid fa-trash-can mr-1"></i> Delete
                            </button>
                        </div>
                    </div>
                </div>
            `}).join('');
        }

        // 8. HELPERS
        function renderBrandTabs() {
            const container = document.getElementById('brandTabs');
            const defaultBrands = ['ALL', 'Hikvision', 'Dahua', 'Imou', 'Ezviz', 'Tiandy', 'Baseus', 'HiLook', 'Other'];
            
            container.innerHTML = defaultBrands.map(b => {
                const isActive = activeBrandFilter === b;
                const cls = isActive 
                    ? 'bg-blue-600 text-white font-bold shadow-md shadow-blue-500/20' 
                    : 'bg-slate-950 text-slate-400 hover:text-white border border-slate-800';

                return `<button onclick="setBrandFilter('${b}')" class="px-3 py-1.5 rounded-lg transition text-xs ${cls}">${b === 'ALL' ? 'සියලුම Brands' : b}</button>`;
            }).join('');
        }

        function setBrandFilter(brand) {
            activeBrandFilter = brand;
            renderBrandTabs();
            filterProducts();
        }

        function setView(v) {
            currentView = v;
            document.getElementById('viewTableBtn').className = v === 'table' ? "px-2.5 py-1.5 rounded text-xs font-medium bg-slate-800 text-blue-400" : "px-2.5 py-1.5 rounded text-xs font-medium text-slate-400 hover:text-white";
            document.getElementById('viewGridBtn').className = v === 'grid' ? "px-2.5 py-1.5 rounded text-xs font-medium bg-slate-800 text-blue-400" : "px-2.5 py-1.5 rounded text-xs font-medium text-slate-400 hover:text-white";
            document.getElementById('tableViewContainer').classList.toggle('hidden', v !== 'table');
            document.getElementById('gridViewContainer').classList.toggle('hidden', v !== 'grid');
            renderView();
        }

        function sortBy(key) {
            if (currentSort.key === key) {
                currentSort.dir = currentSort.dir === 'asc' ? 'desc' : 'asc';
            } else {
                currentSort.key = key;
                currentSort.dir = 'asc';
            }
            renderView();
        }

        function updateStats() {
            document.getElementById('statTotalItems').innerText = products.length;
            document.getElementById('statTotalBrands').innerText = new Set(products.map(p => p.brand)).size;

            let totalMarkup = 0, count = 0, lowStock = 0;
            products.forEach(p => {
                if (p.wholesalePrice > 0) {
                    totalMarkup += ((p.retailPrice - p.wholesalePrice) / p.wholesalePrice) * 100;
                    count++;
                }
                if (p.stock === 'Low Stock' || p.stock === 'Out of Stock') lowStock++;
            });

            document.getElementById('statAvgMargin').innerText = count > 0 ? `${(totalMarkup / count).toFixed(1)}%` : '0%';
            document.getElementById('statLowStock').innerText = lowStock;
        }

        function calculateModalMargin() {
            const wholesale = parseFloat(document.getElementById('productWholesalePrice').value) || 0;
            const retail = parseFloat(document.getElementById('productRetailPrice').value) || 0;
            const profit = retail - wholesale;
            const markupPct = wholesale > 0 ? ((profit / wholesale) * 100).toFixed(1) : 0;

            document.getElementById('previewProfit').innerText = `රු. ${formatNum(profit)}`;
            document.getElementById('previewMarkup').innerText = `${markupPct}%`;
        }

        function openAddModal() {
            document.getElementById('modalTitle').innerHTML = '<i class="fa-solid fa-plus-circle text-blue-500"></i><span>නව CCTV උපකරණයක් එකතු කරන්න</span>';
            document.getElementById('productId').value = '';
            document.getElementById('productForm').reset();
            document.getElementById('productStock').value = 'In Stock';
            document.getElementById('productWarranty').value = '2 Years Warranty';
            calculateModalMargin();
            document.getElementById('productModal').classList.remove('hidden');
        }

        function editProduct(id) {
            const p = products.find(item => item.id === id);
            if (!p) return;

            document.getElementById('modalTitle').innerHTML = '<i class="fa-solid fa-pen-to-square text-blue-500"></i><span>CCTV උපකරණය සංශෝධනය කරන්න</span>';
            document.getElementById('productId').value = p.id;
            document.getElementById('productBrand').value = p.brand;
            document.getElementById('productCategory').value = p.category;
            document.getElementById('productName').value = p.name;
            document.getElementById('productWholesalePrice').value = p.wholesalePrice;
            document.getElementById('productRetailPrice').value = p.retailPrice;
            document.getElementById('productStock').value = p.stock || 'In Stock';
            document.getElementById('productWarranty').value = p.warranty || '';
            document.getElementById('productDescription').value = p.description || '';

            calculateModalMargin();
            document.getElementById('productModal').classList.remove('hidden');
        }

        function closeModal() {
            document.getElementById('productModal').classList.add('hidden');
        }

        function getStockBadge(s) {
            if (s === 'In Stock') return '<span class="px-2 py-0.5 rounded text-xs bg-emerald-500/10 text-emerald-400 border border-emerald-500/20">In Stock</span>';
            if (s === 'Low Stock') return '<span class="px-2 py-0.5 rounded text-xs bg-amber-500/10 text-amber-400 border border-amber-500/20">Low Stock</span>';
            if (s === 'Out of Stock') return '<span class="px-2 py-0.5 rounded text-xs bg-red-500/10 text-red-400 border border-red-500/20">Out of Stock</span>';
            return '<span class="px-2 py-0.5 rounded text-xs bg-slate-800 text-slate-400">Available</span>';
        }

        function getBrandClass(b) {
            switch((b || '').toLowerCase()) {
                case 'imou': return 'bg-orange-500/20 text-orange-400 border border-orange-500/30';
                case 'hikvision': return 'bg-red-500/20 text-red-400 border border-red-500/30';
                case 'dahua': return 'bg-blue-500/20 text-blue-400 border border-blue-500/30';
                case 'ezviz': return 'bg-cyan-500/20 text-cyan-400 border border-cyan-500/30';
                case 'tiandy': return 'bg-amber-500/20 text-amber-400 border border-amber-500/30';
                case 'baseus': return 'bg-yellow-500/20 text-yellow-300 border border-yellow-500/30';
                case 'hilook': return 'bg-teal-500/20 text-teal-300 border border-teal-500/30';
                default: return 'bg-purple-500/20 text-purple-400 border border-purple-500/30';
            }
        }

        function formatNum(n) {
            return Number(n).toLocaleString('en-US', { minimumFractionDigits: 2, maximumFractionDigits: 2 });
        }

        function escapeHtml(str) {
            if (!str) return '';
            return str.replace(/[&<>"']/g, function(m) {
                return { '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#039;' }[m];
            });
        }
    </script>

</body></html>
