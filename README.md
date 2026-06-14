<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AVA Movies & Animes - Ultra Secure Portal</title>
    <style>
        /* پلت رنگی تاریک با درخشش‌های فوق نئونی */
        :root {
            --bg-color: #060810;
            --neon-blue: #00f0ff;
            --neon-glow-blue: rgba(0, 240, 255, 0.35);
            --neon-green: #00ffaa;
            --neon-glow-green: rgba(0, 255, 170, 0.4);
            --neon-gradient: linear-gradient(135deg, #0055ff, #00f0ff, #00ffaa);
            --btn-dark-init: #0f121d;
            --text-dim: #435169;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Roboto, Helvetica, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: #ffffff;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            overflow-x: hidden;
            position: relative;
        }

        /* --- پس‌زمینه کهکشانی متحرک پر از المان‌های ریز سینما و انیمه --- */
        body::before {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 200%;
            /* چیدمان المان‌های مینیاتوری درخواستی: دوربین، کلاکت، تلویزیون، فیلم، میکروفون، پاپ‌کورن، عینک ۳بعدی و... */
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="140" height="140" viewBox="0 0 140 140"><text x="15" y="30" fill="rgba(0, 240, 255, 0.05)" font-size="18">🎥</text><text x="85" y="25" fill="rgba(0, 255, 170, 0.04)" font-size="16">🎬</text><text x="50" y="65" fill="rgba(0, 240, 255, 0.04)" font-size="15">📺</text><text x="110" y="70" fill="rgba(0, 255, 170, 0.05)" font-size="17">🎞️</text><text x="20" y="105" fill="rgba(0, 240, 255, 0.04)" font-size="16">🎙️</text><text x="75" y="115" fill="rgba(0, 255, 170, 0.06)" font-size="18">🍿</text><text x="115" y="120" fill="rgba(0, 240, 255, 0.04)" font-size="15">🕶️</text><text x="10" y="70" fill="rgba(0, 255, 170, 0.03)" font-size="14">🦊</text><text x="80" y="75" fill="rgba(255, 255, 255, 0.04)" font-size="10">✨</text></svg>');
            background-repeat: repeat;
            z-index: -1;
            animation: cinemaSpaceScroll 30s linear infinite;
        }

        @keyframes cinemaSpaceScroll {
            0% { transform: translateY(0); }
            100% { transform: translateY(-50%); }
        }

        /* تصویر اصلی هدر در بالاترین نقطه صفحه (دقیقاً لینک ارسالی شما) */
        .premium-top-banner {
            width: 100%;
            max-width: 460px;
            height: auto;
            margin-top: 25px;
            border-radius: 14px;
            box-shadow: 0 15px 45px rgba(0, 0, 0, 0.7), 0 0 25px rgba(0, 240, 255, 0.1);
            z-index: 10;
        }

        /* بخش تبلیغات نیتیو کاملاً خالص بدون کادر اضافه */
        .native-ad-space {
            width: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 30px 0;
            z-index: 10;
        }

        /* بخش مرکزی محتوا */
        .content-theater {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            flex-grow: 1;
            padding: 20px;
            width: 100%;
            z-index: 10;
        }

        /* متن وضعیت نئونی لوکس */
        .neon-status-text {
            font-size: 1.65rem;
            font-weight: 900;
            letter-spacing: 3px;
            color: var(--neon-blue);
            text-shadow: 0 0 10px var(--neon-glow-blue), 0 0 25px var(--neon-glow-blue);
            margin-bottom: 30px;
            text-transform: uppercase;
            transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
        }

        /* تغییر حالت متن به وضعیت امن نئون سبز */
        .neon-status-text.secured {
            color: var(--neon-green);
            text-shadow: 0 0 10px var(--neon-glow-green), 0 0 25px var(--neon-glow-green);
        }

        /* لودینگ نوستالژیک نوار فیلم آپارات */
        .loader-theater-zone {
            width: 110px;
            height: 110px;
            margin-bottom: 45px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }

        /* طراحی چرخ فیلم قدیمی آپارات با سوراخ‌های بزرگ */
        .cinema-reel-loader {
            width: 80px;
            height: 80px;
            border: 6px solid var(--neon-blue);
            border-radius: 50%;
            position: relative;
            box-shadow: 0 0 20px var(--neon-glow-blue), inset 0 0 15px var(--neon-glow-blue);
            animation: fastReelSpin 1.3s linear infinite;
        }

        /* ایجاد افکت سوراخ‌های داخلی چرخ فیلم */
        .cinema-reel-loader::before {
            content: '';
            position: absolute;
            top: 6px; left: 6px; right: 6px; bottom: 6px;
            border: 5px dashed var(--neon-blue);
            border-radius: 50%;
        }

        @keyframes fastReelSpin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* انیمیشن پنهان‌سازی سریع برای جابجایی */
        .wipe-out {
            opacity: 0;
            transform: scale(0.4) rotate(-90deg);
            pointer-events: none;
            height: 0;
            margin: 0;
            overflow: hidden;
        }

        /* دکمه با طراحی تمام نئونی و گرادینت لاکچری */
        .ultra-neon-btn {
            background: var(--btn-dark-init);
            color: var(--text-dim);
            border: 1px solid rgba(255, 255, 255, 0.01);
            padding: 22px 55px;
            font-size: 1.25rem;
            font-weight: 800;
            border-radius: 50px;
            cursor: not-allowed;
            text-decoration: none;
            pointer-events: none;
            position: relative;
            transition: all 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            letter-spacing: 0.5px;
            box-shadow: inset 0 4px 8px rgba(0,0,0,0.9);
        }

        /* فعال شدن دکمه با گرادینت متحرک و پالس نوری خیره‌کننده */
        .ultra-neon-btn.unlocked {
            background: var(--neon-gradient);
            background-size: 200% auto;
            color: #ffffff;
            cursor: pointer;
            pointer-events: auto;
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 15px 40px rgba(0, 240, 255, 0.35), 0 0 25px var(--neon-glow-green);
            animation: moveGradient 3s linear infinite, glowPulse 2s infinite alternate;
        }

        /* انیمیشن به جریان درآوردن رنگ‌های نئونی داخل دکمه */
        @keyframes moveGradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        /* افکت لرزش و پالس امواج نوری دور دکمه */
        @keyframes glowPulse {
            0% { box-shadow: 0 12px 35px rgba(0, 240, 255, 0.3), 0 0 20px rgba(0, 255, 170, 0.2); }
            100% { box-shadow: 0 20px 50px rgba(0, 240, 255, 0.55), 0 0 40px rgba(0, 255, 170, 0.5); filter: brightness(1.1); }
        }

        /* افکت واکنش سریع و شناور زمان قرارگیری موس */
        .ultra-neon-btn.unlocked:hover {
            transform: translateY(-6px) scale(1.03);
            box-shadow: 0 25px 55px rgba(0, 240, 255, 0.6), 0 0 45px rgba(0, 255, 170, 0.6);
        }

        .ultra-neon-btn.unlocked:active {
            transform: translateY(-2px) scale(1);
        }
    </style>
</head>
<body>

    <img src="https://trilliardaire.sirv.com/6156717967236862865_120.jpg" alt="AVA Streaming Content" class="premium-top-banner">

    <div class="native-ad-space">
        <script async="async" data-cfasync="false" src="https://pl29741961.effectivecpmnetwork.com/46fa53bab184d6979bf4dbeee413d25f/invoke.js"></script>
        <div id="container-46fa53bab184d6979bf4dbeee413d25f"></div>
    </div>

    <div class="content-theater">
        
        <div class="neon-status-text" id="statusPanel">DDos Gard</div>

        <div class="loader-theater-zone" id="theaterLoader">
            <div class="cinema-reel-loader"></div>
        </div>

        <a href="https://www.effectivecpmnetwork.com/t6555sr5ph?key=bf1001c9598de0606ec941ab9e3698d4" class="ultra-neon-btn" id="actionTrigger">
            AVA Free Movies & Animes
        </a>
        
    </div>

    <script>
        document.addEventListener("DOMContentLoaded", function() {
            // اجرای زمان‌بندی غیب شدن و تغییر وضعیت پس از ۲ ثانیه کامل
            setTimeout(function() {
                
                // ۱. غیب کردن و انیمیشن خروج لودینگ آپارات سینمایی
                const loader = document.getElementById('theaterLoader');
                loader.classList.add('wipe-out');

                // ۲. دگرگونی متن و سوییچ رنگ نئونی به حالت امن
                const status = document.getElementById('statusPanel');
                status.classList.add('secured');
                status.innerText = 'Site is protected';

                // ۳. روشن شدن موتور نئونی دکمه، تزریق گرادینت و فعال‌سازی قابلیت کلیک
                const btn = document.getElementById('actionTrigger');
                btn.classList.add('unlocked');

            }, 2000);
        });
    </script>
</body>
</html>
