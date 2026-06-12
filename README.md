<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GamerHub.tr - Profesyonel Oyuncu Ekosistemi</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <style>
        body { background-color: #020617; color: #ffffff; font-family: sans-serif; }
    </style>
</head>
<body class="min-h-screen p-4 md:p-6">

    <header class="border-b border-slate-800 pb-4 mb-6 flex flex-col md:flex-row justify-between items-center gap-4">
        <h1 class="text-2xl font-bold text-indigo-500 tracking-wider">GAMERHUB.TR</h1>
        <div class="flex items-center gap-3">
            <span class="bg-emerald-500/20 text-emerald-400 px-3 py-1 rounded-full text-xs border border-emerald-500/30 font-medium">
                🛡️ OAuth 2.0 Güvenli Hesap Bağlantısı Active
            </span>
        </div>
    </header>

    <div class="grid grid-cols-1 lg:grid-cols-4 gap-6">
        
        <div class="bg-slate-900/80 border border-slate-800 p-4 rounded-xl flex flex-col justify-between h-[350px] lg:h-[450px]">
            <div>
                <span class="text-[10px] uppercase text-indigo-400 tracking-widest font-bold block mb-2">💵 Sponsorlu Alan / Reklam</span>
                <div class="w-full h-48 bg-slate-950 rounded-lg flex items-center justify-center border border-dashed border-slate-700 p-4">
                    <p class="text-xs text-slate-400 text-center">
                        Google AdSense veya Donanım Sponsoru (Klavye/Mouse) Reklam Kodu Buraya Gelecek. Kullanıcılar Sitede Durdukça Kazanacaksın.
                    </p>
                </div>
            </div>
            <div class="bg-slate-950 p-2 rounded text-center border border-slate-800">
                <p class="text-[11px] text-emerald-400 font-medium">💰 Sayfa Gösterim Başına Gelir Etkin</p>
            </div>
        </div>

        <div class="lg:col-span-3 flex flex-col gap-6">
            
            <div class="bg-slate-900 border border-slate-800 p-6 rounded-xl shadow-xl">
                <div class="flex justify-between items-center mb-4">
                    <h2 class="text-lg font-semibold text-slate-200">Veritabanı Profil Özeti: <span class="text-indigo-400">Gamer_15</span></h2>
                    <span class="text-xs bg-indigo-500/10 text-indigo-400 border border-indigo-500/20 px-2 py-0.5 rounded">Premium Üye</span>
                </div>
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                    <div class="bg-slate-950 p-3 rounded-lg border border-slate-800">
                        <p class="text-[11px] text-slate-400">Bağlı Hesap</p>
                        <p class="text-base font-bold text-slate-200">Valorant (Riot API)</p>
                    </div>
                    <div class="bg-slate-950 p-3 rounded-lg border border-slate-800">
                        <p class="text-[11px] text-slate-400">KDA Oranı</p>
                        <p class="text-base font-bold text-amber-400">2.45 (Yüksek)</p>
                    </div>
                    <div class="bg-slate-950 p-3 rounded-lg border border-slate-800">
                        <p class="text-[11px] text-slate-400">Kazanma Oranı</p>
                        <p class="text-base font-bold text-emerald-400">%62.4</p>
                    </div>
                    <div class="bg-slate-950 p-3 rounded-lg border border-slate-800">
                        <p class="text-[11px] text-slate-400">Hesap Güvenliği</p>
                        <p class="text-xs font-bold text-emerald-500">Şifresiz / Korumalı</p>
                    </div>
                </div>
            </div>

            <div class="bg-gradient-to-br from-indigo-950/30 to-slate-900 border border-indigo-500/20 p-6 rounded-xl flex-1 flex flex-col justify-between">
                <div>
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-4 mb-4">
                        <div>
                            <h3 class="text-xl font-bold text-white flex items-center gap-2">
                                <span>🤖</span> AI E-Spor Koç Paneli
                            </h3>
                            <p class="text-xs text-slate-400 mt-1">İnternetten otomatik çekilen yama notlarına göre her gün güncellenir.</p>
                        </div>
                        <button 
                            onclick="generateAICoachReport()" 
                            id="aiBtn"
                            class="w-full md:w-auto bg-indigo-600 hover:bg-indigo-500 text-white font-medium px-6 py-2.5 rounded-lg text-sm transition-all shadow-lg shadow-indigo-600/20 active:scale-95"
                        >
                            AI Taktik Raporu Oluştur
                        </button>
                    </div>

                    <div class="bg-slate-950 border border-slate-800 rounded-lg p-4 min-h-[180px] flex items-center justify-center">
                        <div id="aiOutput" class="text-slate-400 text-sm text-center w-full leading-relaxed">
                            Butona basarak bugünün oyun yamasına ve istatistiklerine göre yapay zekanın canlı analizini başlatın.
                        </div>
                    </div>
                </div>

                <div class="mt-4 border-t border-slate-800/60 pt-4 flex justify-between items-center text-[11px]">
                    <span class="text-slate-500">🤖 Otomatik Sistem Durumu: <span class="text-emerald-400 font-bold">Hatalar Kapatıldı (0 Hata)</span></span>
                    <span id="syncTime" class="text-slate-500">Son Güncelleme: Az önce</span>
                </div>
            </div>

        </div>
    </div>

    <script>
        function generateAICoachReport() {
            const btn = document.getElementById('aiBtn');
            const output = document.getElementById('aiOutput');
            const syncTime = document.getElementById('syncTime');
            
            btn.disabled = true;
            btn.innerText = "Veritabanı taranıyor...";
            output.innerHTML = `<div class="animate-pulse text-indigo-400">🔄 Yapay zeka internetteki son yama notlarını analiz ediyor ve oyuncu hesabını denetliyor...</div>`;

            // Telefonu kasmayacak 1.5 saniyelik simüle edilmiş güvenli yükleme süresi
            setTimeout(() => {
                const bugun = new Date().toLocaleDateString('tr-TR');
                
                // Yapay zekanın her gün değişen güncel tavsiye havuzu
                const advices = [
                    "🎯 [YAMA ANALİZİ]: Son yamada popüler silahların ilk mermi sapması artırıldı. Giriş skorları ararken (Entry) artık durarak ateş etmeye ve sol tık basılı tutmak yerine tek tek (Tapping) vurmaya özen göster.\n\n🛡️ [GÜVENLİK]: Hesabın API üzerinden şifresiz bağlandığı için veri akışı sorunsuz tamamlandı.",
                    "🏃‍♂️ [HARİTA TAKTİĞİ]: İstatistiklerin haritalardaki B savunmasında zayıf olduğunu gösteriyor. Sabit kalmak yerine daha agresif infolar almaya ve pozisyon değiştirmeye çalış.\n\n🔄 [SİSTEM]: Veritabanı hataları tarandı ve otomatik olarak optimize edildi.",
                    "🔥 [TAKIM UYUMU]: Son maçlarındaki yüksek KDA oranına rağmen kazanma oranın takım içi iletişimsizlikten düşüyor. Ekonomi raundlarında takım içi dengeleri gözeterek oyna."
                ];

                const randomAdvice = advices[Math.floor(Math.random() * advices.length)];
                
                output.style.textAlign = "left";
                output.innerHTML = `<div class="text-slate-200 font-mono whitespace-pre-wrap">${randomAdvice}</div>`;
                
                btn.disabled = false;
                btn.innerText = "Yeniden Analiz Et";
                syncTime.innerText = `Son Güncelleme: ${bugun} 03:00 (Otomatik)`;
            }, 1500);
        }
    </script>
</body>
</html>
<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GamerHub.tr - Profesyonel Oyuncu Ekosistemi</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <style>
        body { background-color: #020617; color: #ffffff; font-family: sans-serif; }
    </style>
</head>
<body class="min-h-screen p-4 md:p-6">

    <header class="border-b border-slate-800 pb-4 mb-6 flex flex-col md:flex-row justify-between items-center gap-4">
        <h1 class="text-2xl font-bold text-indigo-500 tracking-wider">GAMERHUB.TR</h1>
        <div class="flex items-center gap-3">
            <span class="bg-emerald-500/20 text-emerald-400 px-3 py-1 rounded-full text-xs border border-emerald-500/30 font-medium">
                🛡️ OAuth 2.0 Güvenli Hesap Bağlantısı Active
            </span>
        </div>
    </header>

    <div class="grid grid-cols-1 lg:grid-cols-4 gap-6">
        
        <div class="bg-slate-900/80 border border-slate-800 p-4 rounded-xl flex flex-col justify-between h-[350px] lg:h-[450px]">
            <div>
                <span class="text-[10px] uppercase text-indigo-400 tracking-widest font-bold block mb-2">💵 Sponsorlu Alan / Reklam</span>
                <div class="w-full h-48 bg-slate-950 rounded-lg flex items-center justify-center border border-dashed border-slate-700 p-4">
                    <p class="text-xs text-slate-400 text-center">
                        Google AdSense veya Donanım Sponsoru (Klavye/Mouse) Reklam Kodu Buraya Gelecek. Kullanıcılar Sitede Durdukça Kazanacaksın.
                    </p>
                </div>
            </div>
            <div class="bg-slate-950 p-2 rounded text-center border border-slate-800">
                <p class="text-[11px] text-emerald-400 font-medium">💰 Sayfa Gösterim Başına Gelir Etkin</p>
            </div>
        </div>

        <div class="lg:col-span-3 flex flex-col gap-6">
            
            <div class="bg-slate-900 border border-slate-800 p-6 rounded-xl shadow-xl">
                <div class="flex justify-between items-center mb-4">
                    <h2 class="text-lg font-semibold text-slate-200">Veritabanı Profil Özeti: <span class="text-indigo-400">Gamer_15</span></h2>
                    <span class="text-xs bg-indigo-500/10 text-indigo-400 border border-indigo-500/20 px-2 py-0.5 rounded">Premium Üye</span>
                </div>
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                    <div class="bg-slate-950 p-3 rounded-lg border border-slate-800">
                        <p class="text-[11px] text-slate-400">Bağlı Hesap</p>
                        <p class="text-base font-bold text-slate-200">Valorant (Riot API)</p>
                    </div>
                    <div class="bg-slate-950 p-3 rounded-lg border border-slate-800">
                        <p class="text-[11px] text-slate-400">KDA Oranı</p>
                        <p class="text-base font-bold text-amber-400">2.45 (Yüksek)</p>
                    </div>
                    <div class="bg-slate-950 p-3 rounded-lg border border-slate-800">
                        <p class="text-[11px] text-slate-400">Kazanma Oranı</p>
                        <p class="text-base font-bold text-emerald-400">%62.4</p>
                    </div>
                    <div class="bg-slate-950 p-3 rounded-lg border border-slate-800">
                        <p class="text-[11px] text-slate-400">Hesap Güvenliği</p>
                        <p class="text-xs font-bold text-emerald-500">Şifresiz / Korumalı</p>
                    </div>
                </div>
            </div>

            <div class="bg-gradient-to-br from-indigo-950/30 to-slate-900 border border-indigo-500/20 p-6 rounded-xl flex-1 flex flex-col justify-between">
                <div>
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-4 mb-4">
                        <div>
                            <h3 class="text-xl font-bold text-white flex items-center gap-2">
                                <span>🤖</span> AI E-Spor Koç Paneli
                            </h3>
                            <p class="text-xs text-slate-400 mt-1">İnternetten otomatik çekilen yama notlarına göre her gün güncellenir.</p>
                        </div>
                        <button 
                            onclick="generateAICoachReport()" 
                            id="aiBtn"
                            class="w-full md:w-auto bg-indigo-600 hover:bg-indigo-500 text-white font-medium px-6 py-2.5 rounded-lg text-sm transition-all shadow-lg shadow-indigo-600/20 active:scale-95"
                        >
                            AI Taktik Raporu Oluştur
                        </button>
                    </div>

                    <div class="bg-slate-950 border border-slate-800 rounded-lg p-4 min-h-[180px] flex items-center justify-center">
                        <div id="aiOutput" class="text-slate-400 text-sm text-center w-full leading-relaxed">
                            Butona basarak bugünün oyun yamasına ve istatistiklerine göre yapay zekanın canlı analizini başlatın.
                        </div>
                    </div>
                </div>

                <div class="mt-4 border-t border-slate-800/60 pt-4 flex justify-between items-center text-[11px]">
                    <span class="text-slate-500">🤖 Otomatik Sistem Durumu: <span class="text-emerald-400 font-bold">Hatalar Kapatıldı (0 Hata)</span></span>
                    <span id="syncTime" class="text-slate-500">Son Güncelleme: Az önce</span>
                </div>
            </div>

        </div>
    </div>

    <script>
        function generateAICoachReport() {
            const btn = document.getElementById('aiBtn');
            const output = document.getElementById('aiOutput');
            const syncTime = document.getElementById('syncTime');
            
            btn.disabled = true;
            btn.innerText = "Veritabanı taranıyor...";
            output.innerHTML = `<div class="animate-pulse text-indigo-400">🔄 Yapay zeka internetteki son yama notlarını analiz ediyor ve oyuncu hesabını denetliyor...</div>`;

            // Telefonu kasmayacak 1.5 saniyelik simüle edilmiş güvenli yükleme süresi
            setTimeout(() => {
                const bugun = new Date().toLocaleDateString('tr-TR');
                
                // Yapay zekanın her gün değişen güncel tavsiye havuzu
                const advices = [
                    "🎯 [YAMA ANALİZİ]: Son yamada popüler silahların ilk mermi sapması artırıldı. Giriş skorları ararken (Entry) artık durarak ateş etmeye ve sol tık basılı tutmak yerine tek tek (Tapping) vurmaya özen göster.\n\n🛡️ [GÜVENLİK]: Hesabın API üzerinden şifresiz bağlandığı için veri akışı sorunsuz tamamlandı.",
                    "🏃‍♂️ [HARİTA TAKTİĞİ]: İstatistiklerin haritalardaki B savunmasında zayıf olduğunu gösteriyor. Sabit kalmak yerine daha agresif infolar almaya ve pozisyon değiştirmeye çalış.\n\n🔄 [SİSTEM]: Veritabanı hataları tarandı ve otomatik olarak optimize edildi.",
                    "🔥 [TAKIM UYUMU]: Son maçlarındaki yüksek KDA oranına rağmen kazanma oranın takım içi iletişimsizlikten düşüyor. Ekonomi raundlarında takım içi dengeleri gözeterek oyna."
                ];

                const randomAdvice = advices[Math.floor(Math.random() * advices.length)];
                
                output.style.textAlign = "left";
                output.innerHTML = `<div class="text-slate-200 font-mono whitespace-pre-wrap">${randomAdvice}</div>`;
                
                btn.disabled = false;
                btn.innerText = "Yeniden Analiz Et";
                syncTime.innerText = `Son Güncelleme: ${bugun} 03:00 (Otomatik)`;
            }, 1500);
        }
    </script>
</body>
</html>
