<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>🫐 Blueberry Burst 🫐</title>
   <script src="https://cdn.tailwindcss.com"></script>
   <!-- QR Code Library -->
   <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
   <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;600;800&display=swap" rel="stylesheet">
   <style>
       body {
           font-family: 'Plus Jakarta Sans', sans-serif;
           background: radial-gradient(circle at top right, #1e3a8a, #4c1d95, #1e1b4b);
           color: #f8fafc;
           min-height: 100vh;
       }
       .glass {
           background: rgba(255, 255, 255, 0.05);
           backdrop-filter: blur(12px);
           border: 1px solid rgba(255, 255, 255, 0.1);
           border-radius: 24px;
       }
       .flavor-card {
           transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
           cursor: pointer;
       }
       .flavor-card:hover {
           transform: translateY(-5px);
           background: rgba(255, 255, 255, 0.1);
           border-color: #6366f1;
       }
       .flavor-active {
           background: rgba(99, 102, 241, 0.2) !important;
           border-color: #818cf8 !important;
           box-shadow: 0 0 20px rgba(99, 102, 241, 0.3);
       }
       .gradient-text {
           background: linear-gradient(to right, #60a5fa, #a78bfa);
           -webkit-background-clip: text;
           -webkit-text-fill-color: transparent;
       }
       #qrcode img {
           margin: 0 auto;
           border-radius: 12px;
           padding: 8px;
           background: white;
       }
   </style>
</head>
<body class="p-4 md:p-8">
   <div class="max-w-5xl mx-auto">
       <!-- Header -->
       <header class="text-center mb-12">
           <h1 class="text-5xl md:text-7xl font-extrabold mb-4 tracking-tight">
               🫐 <span class="gradient-text">  Blueberry Burst  </span> 🫐
           </h1>
           <p class="text-blue-200 text-lg md:text-xl font-light">Experience the essence of pure vibrance.</p>
       </header>

       <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
          
           <!-- Sidebar: QR & Branding -->
           <div class="lg:col-span-1 space-y-6">
               <div class="glass p-8 text-center">
                   <h2 class="text-xl font-semibold mb-4 text-blue-300">Official QR Code</h2>
                   <div id="qrcode" class="mb-4 flex justify-center"></div>
                   <p class="text-sm text-blue-100 opacity-70">Scan to share the Burst</p>
               </div>
              
               <div class="glass p-6">
                   <h3 class="font-bold mb-2">The Vibe</h3>
                   <p class="text-sm text-blue-100 leading-relaxed italic">
                       "Deep indigos, neon violets, and the electric fizz of fresh Hand Sanitizer. Blueberry Burst isn't just a scent—it's an atmosphere."
                   </p>
               </div>
           </div>

           <!-- Main Content: Flavors -->
           <div class="lg:col-span-2 space-y-6">
               <div class="glass p-6 md:p-8">
                   <h2 class="text-2xl font-bold mb-6 flex items-center gap-2">
                       <span class="w-2 h-8 bg-blue-500 rounded-full"></span>
                       Signature Scented Flavors
                   </h2>
                  
                   <div class="grid grid-cols-1 gap-3 mb-8" id="flavor-list">
                       <!-- Flavor Items -->
                       <div onclick="showDetails('blueberry')" id="btn-blueberry" class="flavor-card glass p-4 flex items-center justify-between group">
                           <span class="font-medium flex items-center gap-3">
                               <span class="text-blue-400 font-bold">01.</span> Blueberry
                           </span>
                           <span class="text-xs uppercase tracking-widest text-blue-300 group-hover:translate-x-1 transition-transform">Details →</span>
                       </div>

                       <div onclick="showDetails('watermelon')" id="btn-watermelon" class="flavor-card glass p-4 flex items-center justify-between group">
                           <span class="font-medium flex items-center gap-3">
                               <span class="text-pink-400 font-bold">02.</span> Watermelon
                           </span>
                           <span class="text-xs uppercase tracking-widest text-pink-300 group-hover:translate-x-1 transition-transform">Details →</span>
                       </div>

                       <div onclick="showDetails('peppermint')" id="btn-peppermint" class="flavor-card glass p-4 flex items-center justify-between group">
                           <span class="font-medium flex items-center gap-3">
                               <span class="text-teal-400 font-bold">03.</span> Peppermint
                           </span>
                           <span class="text-xs uppercase tracking-widest text-teal-300 group-hover:translate-x-1 transition-transform">Details →</span>
                       </div>

                       <div onclick="showDetails('mango')" id="btn-mango" class="flavor-card glass p-4 flex items-center justify-between group">
                           <span class="font-medium flex items-center gap-3">
                               <span class="text-orange-400 font-bold">04.</span> Mango
                           </span>
                           <span class="text-xs uppercase tracking-widest text-orange-300 group-hover:translate-x-1 transition-transform">Details →</span>
                       </div>

                       <div onclick="showDetails('coconut')" id="btn-coconut" class="flavor-card glass p-4 flex items-center justify-between group">
                           <span class="font-medium flex items-center gap-3">
                               <span class="text-gray-300 font-bold">05.</span> Coconut
                           </span>
                           <span class="text-xs uppercase tracking-widest text-gray-400 group-hover:translate-x-1 transition-transform">Details →</span>
                       </div>
                   </div>

                   <!-- Details Display Area -->
                   <div id="details-box" class="min-h-[200px] border-t border-white/10 pt-8 animate-in fade-in duration-500">
                       <div id="placeholder-text" class="text-center py-10 opacity-50">
                           <p>Click a flavor above to explore its profile.</p>
                       </div>
                       <div id="content-area" class="hidden">
                           <div class="flex flex-col sm:flex-row items-center sm:items-start gap-6 mb-6">
                               <!-- Dynamic Logo Image -->
                               <img id="detail-logo" src="" alt="Flavor Logo" class="w-24 h-24 object-cover rounded-2xl shadow-xl shadow-blue-500/20 border border-white/20">
                               <div class="text-center sm:text-left">
                                   <h3 id="detail-title" class="text-3xl font-bold mb-2"></h3>
                                   <p id="detail-tagline" class="text-blue-400 font-semibold mb-4 italic"></p>
                               </div>
                           </div>
                           <p id="detail-desc" class="text-blue-100 leading-relaxed mb-6"></p>
                           <div class="grid grid-cols-2 gap-4">
                               <div class="bg-white/5 p-3 rounded-xl border border-white/5">
                                   <span class="block text-[10px] uppercase text-blue-300 mb-1">Top Notes</span>
                                   <span id="detail-top" class="text-sm"></span>
                               </div>
                               <div class="bg-white/5 p-3 rounded-xl border border-white/5">
                                   <span class="block text-[10px] uppercase text-blue-300 mb-1">Mood</span>
                                   <span id="detail-mood" class="text-sm"></span>
                               </div>
                           </div>
                       </div>
                   </div>
               </div>
           </div>
       </div>
      
       <footer class="mt-12 text-center text-blue-400/50 text-sm">
           &copy; 2026 Blueberry Burst Inc. • Stay Fresh
       </footer>
   </div>

   <script>
       const flavorData = {
           blueberry: {
               title: "01. Classic Blueberry Burst",
               tagline: "The Signature Burst",
               image: "https://media.post.rvohealth.io/wp-content/uploads/2020/08/blueberries-1200x628-facebook-1200x628.jpg",
               desc: "Our flagship scent captures the exact moment a ripe blueberry pops. It's a complex blend of tart skin and sugary-sweet pulp, finishing with a hint of earthy forest floor. It's bold, unyielding, and deeply blue.",
               top: "Wild Berries, Zest",
               mood: "Energizing & Bold"
           },
           watermelon: {
               title: "02. Watermelon Burst",
               tagline: "Summer in a Bottle",
               image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRd3-khYH4sUeg9Cor5Pp-ZefSzkSbbWV6GJQ&s",
               desc: "Not your average candy scent. This is the hyper-realistic aroma of a fresh-cut melon on a 100-degree day. Crisp, aqueous, and refreshingly sweet with a subtle green-rind finish that keeps it sophisticated.",
               top: "Crisp Melon, Cucumber",
               mood: "Playful & Refreshing"
           },
           peppermint: {
               title: "03. Arctic Peppermint",
               tagline: "The Chill Factor",
               image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTYkX0BMYh6uy3O09wr0KNzOTfnLqweoV2q7g&s",
               desc: "An icy blast that cuts through the noise. This high-clarity peppermint is infused with a touch of spearmint for sweetness and a microscopic hint of vanilla to smooth out the edges. It clears the mind instantly.",
               top: "Crushed Mint, Menthol",
               mood: "Focused & Cooling"
           },
           mango: {
               title: "04. Explosive Mango",
               tagline: "Tropical Decadence",
               image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT3Qf8R603TtMkkRT7G04Nupe9SUZmwToGb-g&s",
               desc: "A rich, sun-drenched Alphonso mango profile. It leans into the creamy, buttery side of the fruit rather than just the citrus. It smells like golden hour on a private beach—dense, warm, and exotic.",
               top: "Nectar, Peach Skin",
               mood: "Sensual & Sunny"
           },
           coconut: {
               title: "05. Nutty Coconut",
               tagline: "The Island Dream",
               image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQS49O7jwuO0jzDwAxrThk_igIRxgjLuJt4ZQ&s",
               desc: "Escape the ordinary with a scent that balances milky coconut water with a charred, nutty warmth. It avoids the 'sunscreen' cliche, opting instead for a raw, natural coconut husk aroma that feels grounded and premium.",
               top: "Coconut Milk",
               mood: "Calming & Sophisticated"
           }
       };

       function showDetails(key) {
           const data = flavorData[key];
           const content = document.getElementById('content-area');
           const placeholder = document.getElementById('placeholder-text');
          
           // UI Feedback
           document.querySelectorAll('.flavor-card').forEach(el => el.classList.remove('flavor-active'));
           document.getElementById(`btn-${key}`).classList.add('flavor-active');

           // Set Data
           document.getElementById('detail-title').innerText = data.title;
           document.getElementById('detail-tagline').innerText = data.tagline;
           document.getElementById('detail-desc').innerText = data.desc;
           document.getElementById('detail-top').innerText = data.top;
           document.getElementById('detail-mood').innerText = data.mood;
          
           // Set Logo Image
           const logoEl = document.getElementById('detail-logo');
           logoEl.src = data.image;

           // Animate
           placeholder.classList.add('hidden');
           content.classList.remove('hidden');
           content.classList.remove('animate-in', 'fade-in');
           void content.offsetWidth; // Trigger reflow
           content.classList.add('animate-in', 'fade-in');
       }

       window.onload = function() {
           // Generate QR Code targeting the brand
           new QRCode(document.getElementById("qrcode"), {
               text: "https://blueberry-burst-fragrance.example.com",
               width: 140,
               height: 140,
               colorDark : "#1e1b4b",
               colorLight : "#ffffff",
               correctLevel : QRCode.CorrectLevel.H
           });
       };
   </script>
</body>
</html>
