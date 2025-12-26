<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KyraAI V2 — Твой чат оживает</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://unpkg.com/scrollreveal"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Unbounded:wght@300;400;700;900&family=Plus+Jakarta+Sans:wght@300;400;600&display=swap');
        
        :root {
            --primary: #8b5cf6;
            --secondary: #ec4899;
            --bg-dark: #050507;
        }

        body {
            font-family: 'Plus Jakarta Sans', sans-serif;
            background-color: var(--bg-dark);
            color: #ffffff;
            scroll-behavior: smooth;
            overflow-x: hidden;
        }

        h1, h2, .brand-font {
            font-family: 'Unbounded', sans-serif;
        }

        /* Анимированный фон */
        .bg-animate {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: 
                radial-gradient(circle at 20% 30%, rgba(139, 92, 246, 0.1) 0%, transparent 50%),
                radial-gradient(circle at 80% 70%, rgba(236, 72, 153, 0.1) 0%, transparent 50%);
            filter: blur(80px);
        }

        .floating-orb {
            position: absolute;
            width: 300px;
            height: 300px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 50%;
            opacity: 0.2;
            filter: blur(100px);
            animation: float 20s infinite alternate;
        }

        @keyframes float {
            0% { transform: translate(0, 0); }
            100% { transform: translate(100px, 100px); }
        }

        /* Glassmorphism */
        .glass {
            background: rgba(255, 255, 255, 0.02);
            backdrop-filter: blur(15px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        .glass:hover {
            background: rgba(255, 255, 255, 0.05);
            border-color: var(--primary);
            box-shadow: 0 20px 40px rgba(0,0,0,0.4);
            transform: translateY(-10px) scale(1.02);
        }

        .btn-shiny {
            position: relative;
            overflow: hidden;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            transition: all 0.3s ease;
        }

        .btn-shiny:hover {
            box-shadow: 0 0 30px rgba(139, 92, 246, 0.6);
            transform: scale(1.05);
        }

        .btn-shiny::after {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(transparent, rgba(255,255,255,0.3), transparent);
            transform: rotate(45deg);
            transition: 0.5s;
        }

        .btn-shiny:hover::after {
            left: 120%;
        }

        .text-glow {
            text-shadow: 0 0 20px rgba(139, 92, 246, 0.5);
        }

        .stat-card {
            border-left: 2px solid var(--primary);
        }
    </style>
</head>
<body>

    <div class="bg-animate"></div>
    <div class="floating-orb top-0 right-0"></div>
    <div class="floating-orb bottom-0 left-0" style="animation-delay: -5s;"></div>

    <!-- Навигация -->
    <nav class="fixed w-full z-50 p-6">
        <div class="max-w-7xl mx-auto flex items-center justify-between glass rounded-3xl px-8 py-4">
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 bg-gradient-to-tr from-purple-600 to-pink-500 rounded-xl flex items-center justify-center shadow-lg">
                    <i class="fas fa-bolt text-white"></i>
                </div>
                <span class="text-xl font-black brand-font tracking-tighter uppercase">Kyra<span class="text-purple-500">AI</span></span>
            </div>
            <div class="hidden md:flex items-center gap-10 font-bold text-sm tracking-widest uppercase">
                <a href="#features" class="hover:text-purple-400 transition">Протоколы</a>
                <a href="#commands" class="hover:text-purple-400 transition">Команды</a>
                <a href="https://t.me/kyraai_official_bot" class="btn-shiny px-6 py-3 rounded-xl text-white">Взломать скуку</a>
            </div>
        </div>
    </nav>

    <!-- Главная секция -->
    <header class="relative min-h-screen flex items-center justify-center pt-20">
        <div class="max-w-5xl mx-auto px-6 text-center">
            <div class="inline-block glass px-6 py-2 rounded-full mb-8 border-purple-500/30">
                <span class="text-xs font-bold uppercase tracking-[0.3em] text-purple-400">Evolution Version 2.0</span>
            </div>
            <h1 class="text-6xl md:text-8xl font-black mb-8 leading-none tracking-tighter">
                ТВОЙ ЧАТ — <br> ЭТО <span class="text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-pink-500 text-glow">ЭНЕРГИЯ</span>
            </h1>
            <p class="text-gray-400 text-lg md:text-2xl mb-12 max-w-2xl mx-auto leading-relaxed font-light">
                KyraAI V2 превращает обычную переписку в живую экосистему с ИИ-памятью, экономикой и игровыми механиками.
            </p>
            <div class="flex flex-wrap justify-center gap-6">
                <a href="https://t.me/kyraai_official_bot" class="btn-shiny px-12 py-5 rounded-2xl font-black text-xl shadow-2xl">
                    ЗАПУСТИТЬ МОДУЛЬ
                </a>
                <a href="#commands" class="glass px-12 py-5 rounded-2xl font-black text-xl hover:bg-white/10 transition">
                    БАЗА ДАННЫХ
                </a>
            </div>
        </div>
    </header>

    <!-- Секция Статистики -->
    <section class="py-10 px-6">
        <div class="max-w-6xl mx-auto grid grid-cols-2 md:grid-cols-4 gap-8">
            <div class="glass p-8 rounded-3xl text-center stat-card reveal">
                <div class="text-4xl font-black mb-2 brand-font">500+</div>
                <div class="text-xs uppercase tracking-widest text-gray-500 font-bold">Чатов</div>
            </div>
            <div class="glass p-8 rounded-3xl text-center stat-card reveal" style="transition-delay: 0.1s;">
                <div class="text-4xl font-black mb-2 brand-font">140+</div>
                <div class="text-xs uppercase tracking-widest text-gray-500 font-bold">Фраз в памяти</div>
            </div>
            <div class="glass p-8 rounded-3xl text-center stat-card reveal" style="transition-delay: 0.2s;">
                <div class="text-4xl font-black mb-2 brand-font">24/7</div>
                <div class="text-xs uppercase tracking-widest text-gray-500 font-bold">Uptime</div>
            </div>
            <div class="glass p-8 rounded-3xl text-center stat-card reveal" style="transition-delay: 0.3s;">
                <div class="text-4xl font-black mb-2 brand-font">∞</div>
                <div class="text-xs uppercase tracking-widest text-gray-500 font-bold">Веселья</div>
            </div>
        </div>
    </section>

    <!-- Возможности -->
    <section id="features" class="py-32 px-6">
        <div class="max-w-7xl mx-auto">
            <h2 class="text-4xl md:text-6xl font-black mb-20 brand-font tracking-tighter reveal">ПОЛНЫЙ <br><span class="text-purple-500">КОНТРОЛЬ</span></h2>
            
            <div class="grid grid-cols-1 md:grid-cols-3 gap-10">
                <div class="glass p-10 rounded-[2.5rem] relative group reveal">
                    <div class="absolute top-0 right-0 p-8 text-6xl text-white/5 font-black group-hover:text-purple-500/20 transition">01</div>
                    <div class="w-16 h-16 bg-purple-500/20 rounded-2xl flex items-center justify-center mb-10">
                        <i class="fas fa-brain text-3xl text-purple-400"></i>
                    </div>
                    <h3 class="text-2xl font-bold mb-4 brand-font">НЕЙРО-АРХИВ</h3>
                    <p class="text-gray-400 leading-relaxed">Бот не просто отвечает, он мимикрирует под стиль вашего общения, создавая уникальную атмосферу.</p>
                </div>

                <div class="glass p-10 rounded-[2.5rem] relative group reveal" style="transition-delay: 0.2s;">
                    <div class="absolute top-0 right-0 p-8 text-6xl text-white/5 font-black group-hover:text-pink-500/20 transition">02</div>
                    <div class="w-16 h-16 bg-pink-500/20 rounded-2xl flex items-center justify-center mb-10">
                        <i class="fas fa-coins text-3xl text-pink-400"></i>
                    </div>
                    <h3 class="text-2xl font-bold mb-4 brand-font">КРИПТО-ЭКО</h3>
                    <p class="text-gray-400 leading-relaxed">Зарабатывай монеты через работу, соревнуйся в балансе и стань самым богатым в чате.</p>
                </div>

                <div class="glass p-10 rounded-[2.5rem] relative group reveal" style="transition-delay: 0.4s;">
                    <div class="absolute top-0 right-0 p-8 text-6xl text-white/5 font-black group-hover:text-indigo-500/20 transition">03</div>
                    <div class="w-16 h-16 bg-indigo-500/20 rounded-2xl flex items-center justify-center mb-10">
                        <i class="fas fa-heart text-3xl text-indigo-400"></i>
                    </div>
                    <h3 class="text-2xl font-bold mb-4 brand-font">СОЦ-УЗЛЫ</h3>
                    <p class="text-gray-400 leading-relaxed">Браки, репутация, варны и игра «Кто?». Полный набор инструментов для управления толпой.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Команды -->
    <section id="commands" class="py-32 px-6">
        <div class="max-w-4xl mx-auto">
            <div class="glass rounded-[3rem] p-12 reveal">
                <h2 class="text-4xl font-black mb-12 brand-font text-center">ТЕРМИНАЛ</h2>
                <div class="space-y-6">
                    <div class="flex items-center justify-between p-6 border-b border-white/5 hover:bg-white/5 rounded-2xl transition group">
                        <div>
                            <span class="text-xl font-bold text-purple-400 group-hover:text-white">кто ...</span>
                            <p class="text-sm text-gray-500 uppercase mt-1">Рандомайзер участников</p>
                        </div>
                        <i class="fas fa-arrow-right text-gray-800"></i>
                    </div>
                    <div class="flex items-center justify-between p-6 border-b border-white/5 hover:bg-white/5 rounded-2xl transition group">
                        <div>
                            <span class="text-xl font-bold text-purple-400 group-hover:text-white">работа</span>
                            <p class="text-sm text-gray-500 uppercase mt-1">Майнинг внутренней валюты</p>
                        </div>
                        <i class="fas fa-arrow-right text-gray-800"></i>
                    </div>
                    <div class="flex items-center justify-between p-6 border-b border-white/5 hover:bg-white/5 rounded-2xl transition group">
                        <div>
                            <span class="text-xl font-bold text-purple-400 group-hover:text-white">брак</span>
                            <p class="text-sm text-gray-500 uppercase mt-1">Создание семейного союза</p>
                        </div>
                        <i class="fas fa-arrow-right text-gray-800"></i>
                    </div>
                    <div class="flex items-center justify-between p-6 hover:bg-white/5 rounded-2xl transition group">
                        <div>
                            <span class="text-xl font-bold text-purple-400 group-hover:text-white">баланс</span>
                            <p class="text-sm text-gray-500 uppercase mt-1">Проверка крипто-счета</p>
                        </div>
                        <i class="fas fa-arrow-right text-gray-800"></i>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Подвал -->
    <footer class="py-20 border-t border-white/5">
        <div class="max-w-7xl mx-auto px-6 flex flex-col md:flex-row justify-between items-center gap-10">
            <div class="brand-font font-black text-2xl uppercase tracking-tighter">
                Kyra<span class="text-purple-500">AI</span>
            </div>
            <div class="text-gray-500 text-sm font-bold uppercase tracking-widest">
                © 2025 Все права защищены протоколом Kyra
            </div>
            <div class="flex gap-8 text-2xl text-gray-400">
                <a href="#" class="hover:text-white transition"><i class="fab fa-telegram"></i></a>
                <a href="#" class="hover:text-white transition"><i class="fab fa-github"></i></a>
            </div>
        </div>
    </footer>

    <script>
        // Анимация при скролле
        ScrollReveal().reveal('.reveal', { 
            delay: 200, 
            distance: '50px', 
            origin: 'bottom', 
            opacity: 0,
            interval: 100 
        });
    </script>
</body>
</html>

