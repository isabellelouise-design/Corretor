<!doctype html>
<html lang="pt-BR">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Corretor Inteligente - Teclado com Correção Automática para Android</title>
  <style>
        body {
            box-sizing: border-box;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            overflow-x: hidden;
        }

        /* Header e Navegação */
        header {
            background: linear-gradient(135deg, #8b5cf6 0%, #6366f1 100%);
            color: white;
            padding: 20px 0;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        nav {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 20px;
        }

        .logo {
            font-size: 24px;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 10px;
            text-decoration: none;
            color: white;
        }

        .keyboard-icon {
            font-size: 28px;
        }

        .nav-links {
            display: flex;
            gap: 30px;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: opacity 0.3s;
        }

        .nav-links a:hover {
            opacity: 0.8;
        }

        .mobile-menu {
            display: none;
            font-size: 28px;
            cursor: pointer;
        }

        /* Hero Section */
        .hero {
            margin-top: 80px;
            background: linear-gradient(135deg, #8b5cf6 0%, #6366f1 100%);
            color: white;
            padding: 100px 20px;
            text-align: center;
        }

        .hero h1 {
            font-size: 48px;
            margin-bottom: 20px;
            animation: fadeInUp 0.8s ease;
        }

        .hero p {
            font-size: 20px;
            margin-bottom: 40px;
            opacity: 0.9;
            animation: fadeInUp 1s ease;
        }

        .cta-buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap;
            animation: fadeInUp 1.2s ease;
        }

        .btn {
            padding: 15px 40px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            font-size: 16px;
            transition: transform 0.3s, box-shadow 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }

        .btn-primary {
            background: white;
            color: #8b5cf6;
        }

        .btn-secondary {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: 2px solid white;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
        }

        /* Seção do Corretor Web */
        .corretor-web-section {
            padding: 80px 20px;
            background: linear-gradient(180deg, #f7fafc 0%, #edf2f7 100%);
        }

        .corretor-web-container {
            max-width: 1000px;
            margin: 0 auto;
        }

        .corretor-web-header {
            text-align: center;
            margin-bottom: 50px;
        }

        .corretor-web-header h2 {
            font-size: 42px;
            color: #2d3748;
            margin-bottom: 15px;
        }

        .corretor-web-header p {
            font-size: 18px;
            color: #4a5568;
        }

        .corretor-card {
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.1);
        }

        .text-input-area {
            margin-bottom: 30px;
        }

        .text-input-area label {
            display: block;
            font-size: 18px;
            font-weight: 600;
            color: #2d3748;
            margin-bottom: 15px;
        }

        #textInput {
            width: 100%;
            min-height: 200px;
            padding: 20px;
            border: 2px solid #e2e8f0;
            border-radius: 15px;
            font-size: 16px;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            resize: vertical;
            transition: border-color 0.3s;
        }

        #textInput:focus {
            outline: none;
            border-color: #8b5cf6;
        }

        .controls {
            display: flex;
            gap: 15px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .control-btn {
            padding: 12px 30px;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .btn-correct {
            background: linear-gradient(135deg, #8b5cf6 0%, #6366f1 100%);
            color: white;
        }

        .btn-correct:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(139, 92, 246, 0.3);
        }

        .btn-correct:disabled {
            background: #cbd5e0;
            cursor: not-allowed;
            transform: none;
        }

        .btn-clear {
            background: #fff;
            color: #4a5568;
            border: 2px solid #e2e8f0;
        }

        .btn-clear:hover {
            background: #f7fafc;
            border-color: #cbd5e0;
        }

        .stats-bar {
            background: #f7fafc;
            padding: 20px;
            border-radius: 10px;
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat {
            text-align: center;
        }

        .stat-number {
            font-size: 32px;
            font-weight: bold;
            color: #8b5cf6;
        }

        .stat-label {
            font-size: 14px;
            color: #718096;
            margin-top: 5px;
        }

        .corrections-display {
            margin-top: 30px;
        }

        .corrections-display h3 {
            font-size: 20px;
            color: #2d3748;
            margin-bottom: 15px;
        }

        .correction-item {
            background: #fef3c7;
            border-left: 4px solid #f59e0b;
            padding: 15px;
            margin-bottom: 10px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            gap: 10px;
            animation: slideIn 0.3s ease;
        }

        .correction-wrong {
            color: #dc2626;
            text-decoration: line-through;
            font-weight: 600;
        }

        .correction-arrow {
            color: #059669;
            font-size: 20px;
        }

        .correction-right {
            color: #059669;
            font-weight: 600;
        }

        .no-errors {
            background: #d1fae5;
            border-left: 4px solid #10b981;
            padding: 20px;
            border-radius: 8px;
            text-align: center;
            color: #065f46;
            font-weight: 600;
        }

        .loading {
            text-align: center;
            padding: 30px;
            color: #718096;
        }

        .spinner {
            border: 4px solid #e2e8f0;
            border-top: 4px solid #8b5cf6;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 0 auto 15px;
        }

        /* Features Section */
        .features {
            padding: 80px 20px;
            background: white;
        }

        .features-container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .features h2 {
            text-align: center;
            font-size: 42px;
            color: #2d3748;
            margin-bottom: 60px;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 40px;
        }

        .feature-card {
            text-align: center;
            padding: 30px;
            border-radius: 15px;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .feature-icon {
            font-size: 60px;
            margin-bottom: 20px;
        }

        .feature-card h3 {
            font-size: 24px;
            color: #2d3748;
            margin-bottom: 15px;
        }

        .feature-card p {
            color: #4a5568;
            line-height: 1.8;
        }

        /* How It Works */
        .how-it-works {
            padding: 80px 20px;
            background: #f7fafc;
        }

        .how-container {
            max-width: 1000px;
            margin: 0 auto;
        }

        .how-it-works h2 {
            text-align: center;
            font-size: 42px;
            color: #2d3748;
            margin-bottom: 60px;
        }

        .steps {
            display: flex;
            flex-direction: column;
            gap: 40px;
        }

        .step {
            display: flex;
            gap: 30px;
            align-items: center;
        }

        .step-number {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #8b5cf6 0%, #6366f1 100%);
            color: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 32px;
            font-weight: bold;
            flex-shrink: 0;
        }

        .step-content h3 {
            font-size: 24px;
            color: #2d3748;
            margin-bottom: 10px;
        }

        .step-content p {
            color: #4a5568;
            line-height: 1.8;
        }

        /* Download Section */
        .download {
            padding: 80px 20px;
            background: linear-gradient(135deg, #8b5cf6 0%, #6366f1 100%);
            color: white;
            text-align: center;
        }

        .download h2 {
            font-size: 42px;
            margin-bottom: 20px;
        }

        .download p {
            font-size: 18px;
            margin-bottom: 40px;
            opacity: 0.9;
        }

        .download-links {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap;
        }

        .store-badge {
            background: white;
            padding: 15px 30px;
            border-radius: 15px;
            text-decoration: none;
            color: #2d3748;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: transform 0.3s;
        }

        .store-badge:hover {
            transform: scale(1.05);
        }

        /* Footer */
        footer {
            background: #1a202c;
            color: white;
            padding: 40px 20px;
            text-align: center;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
        }

        .footer-links {
            display: flex;
            gap: 30px;
            justify-content: center;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }

        .footer-links a {
            color: white;
            text-decoration: none;
            transition: opacity 0.3s;
        }

        .footer-links a:hover {
            opacity: 0.7;
        }

        .social-links {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin: 30px 0;
            font-size: 24px;
        }

        .social-links a {
            color: white;
            transition: transform 0.3s;
        }

        .social-links a:hover {
            transform: scale(1.2);
        }

        /* Animações */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateX(-20px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Responsivo */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .mobile-menu {
                display: block;
            }

            .hero h1 {
                font-size: 32px;
            }

            .hero p {
                font-size: 16px;
            }

            .features h2, .how-it-works h2, .download h2, .corretor-web-header h2 {
                font-size: 32px;
            }

            .step {
                flex-direction: column;
                text-align: center;
            }

            .corretor-card {
                padding: 25px;
            }

            .stats-bar {
                flex-direction: column;
            }
        }
    </style>
  <style>@view-transition { navigation: auto; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
  <script src="/_sdk/element_sdk.js" type="text/javascript"></script>
  <script src="https://cdn.tailwindcss.com" type="text/javascript"></script>
 </head>
 <body>
  <header>
   <nav><a href="#home" class="logo"> <span class="keyboard-icon">⌨️</span> <span>Corretor Inteligente</span> </a>
    <div class="nav-links"><a href="#features">Recursos</a> <a href="#corretor-web">Testar Online</a> <a href="#how-it-works">Como Funciona</a> <a href="#download">Download</a> <a href="privacidade.html">Privacidade</a> <a href="termos.html">Termos</a>
    </div>
    <div class="mobile-menu" id="mobileMenu">
     ☰
    </div>
   </nav>
  </header>
  <section class="hero" id="home">
   <h1>✨ Corretor Inteligente</h1>
   <p>O teclado Android que corrige seus textos automaticamente com precisão profissional</p>
   <div class="cta-buttons"><a href="#download" class="btn btn-primary"> <span>📱</span> Baixar para Android </a> <a href="#corretor-web" class="btn btn-secondary"> <span>💻</span> Testar no Navegador </a>
   </div>
  </section><!-- NOVA SEÇÃO: CORRETOR WEB -->
  <section class="corretor-web-section" id="corretor-web">
   <div class="corretor-web-container">
    <div class="corretor-web-header">
     <h2>💻 Teste o Corretor Agora!</h2>
     <p>Experimente a correção ortográfica inteligente direto no seu navegador</p>
    </div>
    <div class="corretor-card">
     <div class="text-input-area">
      <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px;"><label for="textInput" style="margin: 0;">Digite ou cole seu texto aqui:</label>
       <div id="planIndicator" style="display: flex; align-items: center; gap: 10px;"><span id="charCounter" style="font-size: 14px; color: #64748b; font-weight: 600;">0 / 500</span> <span id="planBadge" style="background: #cbd5e0; color: #1a202c; padding: 5px 12px; border-radius: 15px; font-size: 12px; font-weight: 700;">GRÁTIS</span> <button id="upgradBtn" style="background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%); color: white; border: none; padding: 8px 16px; border-radius: 15px; cursor: pointer; font-weight: 700; font-size: 12px; transition: transform 0.2s;">⭐ PREMIUM</button>
       </div>
      </div><textarea id="textInput" placeholder="Escreva algo com erros de portugues para testar o corretor automatico..."></textarea>
     </div>
     <div class="controls"><button class="control-btn btn-correct" id="correctBtn"> <span>✨</span> Corrigir Texto </button> <button class="control-btn" id="synonymBtn" style="background: #10b981; color: white;"> <span>📚</span> Ver Sinônimos </button> <button class="control-btn" id="aiDetectBtn" style="background: #8b5cf6; color: white; position: relative;"> <span>🤖</span> Detectar IA <span style="position: absolute; top: -8px; right: -8px; background: #f59e0b; color: white; font-size: 9px; padding: 2px 6px; border-radius: 10px; font-weight: 700;">PRO</span> </button> <button class="control-btn" id="coherenceBtn" style="background: #06b6d4; color: white; position: relative;"> <span>📊</span> Coerência <span style="position: absolute; top: -8px; right: -8px; background: #f59e0b; color: white; font-size: 9px; padding: 2px 6px; border-radius: 10px; font-weight: 700;">PRO</span> </button> <button class="control-btn btn-clear" id="clearBtn"> <span>🗑️</span> Limpar </button>
     </div>
     <div class="stats-bar" id="statsBar" style="display: none;">
      <div class="stat">
       <div class="stat-number" id="wordCount">
        0
       </div>
       <div class="stat-label">
        Palavras
       </div>
      </div>
      <div class="stat">
       <div class="stat-number" id="errorCount">
        0
       </div>
       <div class="stat-label">
        Erros Encontrados
       </div>
      </div>
      <div class="stat">
       <div class="stat-number" id="correctionCount">
        0
       </div>
       <div class="stat-label">
        Correções Feitas
       </div>
      </div>
     </div>
     <div class="corrections-display" id="correctionsDisplay"></div><!-- CAIXA DE TEXTO CORRIGIDO -->
     <div id="correctedTextBox" style="display: none; margin-top: 30px;">
      <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 15px;">
       <h3 style="color: #2d3748; margin: 0;">✅ Texto Corrigido:</h3><button id="copyBtn" class="control-btn" style="background: #10b981; color: white; padding: 10px 20px;"> <span>📋</span> Copiar Texto </button>
      </div>
      <div id="correctedTextContent" style="background: #f0fdf4; border: 2px solid #10b981; border-radius: 15px; padding: 20px; font-size: 16px; line-height: 1.8; white-space: pre-wrap; word-wrap: break-word;"></div>
      <div id="copySuccess" style="display: none; background: #d1fae5; padding: 10px; border-radius: 8px; margin-top: 10px; text-align: center; color: #065f46; font-weight: 600;">
       ✅ Texto copiado para a área de transfer��ncia!
      </div>
     </div>
    </div>
   </div>
  </section>
  <section class="features" id="features">
   <div class="features-container">
    <h2>🚀 Recursos Incríveis</h2>
    <div class="features-grid">
     <div class="feature-card">
      <div class="feature-icon">
       ✍️
      </div>
      <h3>Correção Automática</h3>
      <p>Corrige erros de ortografia em tempo real enquanto você digita</p>
     </div>
     <div class="feature-card">
      <div class="feature-icon">
       🎨
      </div>
      <h3>Temas Personalizáveis</h3>
      <p>Escolha cores e estilos que combinem com você</p>
     </div>
     <div class="feature-card">
      <div class="feature-icon">
       🧠
      </div>
      <h3>Modo Dislexia</h3>
      <p>Fonte especial e recursos para quem tem dislexia</p>
     </div>
     <div class="feature-card">
      <div class="feature-icon">
       🔒
      </div>
      <h3>100% Privado</h3>
      <p>Nada do que você digita é enviado para servidores</p>
     </div>
     <div class="feature-card">
      <div class="feature-icon">
       ⚡
      </div>
      <h3>Super Rápido</h3>
      <p>Processamento local e instantâneo</p>
     </div>
     <div class="feature-card">
      <div class="feature-icon">
       📊
      </div>
      <h3>Estatísticas</h3>
      <p>Veja quantas correções foram feitas</p>
     </div>
    </div>
   </div>
  </section>
  <section class="how-it-works" id="how-it-works">
   <div class="how-container">
    <h2>📱 Como Funciona</h2>
    <div class="steps">
     <div class="step">
      <div class="step-number">
       1
      </div>
      <div class="step-content">
       <h3>Baixe e Instale</h3>
       <p>Baixe o app da Play Store e instale no seu Android</p>
      </div>
     </div>
     <div class="step">
      <div class="step-number">
       2
      </div>
      <div class="step-content">
       <h3>Ative o Teclado</h3>
       <p>Vá em Configurações → Idioma e entrada → Teclados virtuais e ative o Corretor Inteligente</p>
      </div>
     </div>
     <div class="step">
      <div class="step-number">
       3
      </div>
      <div class="step-content">
       <h3>Personalize</h3>
       <p>Escolha seu tema favorito, configure a altura do teclado e ative o modo dislexia se necessário</p>
      </div>
     </div>
     <div class="step">
      <div class="step-number">
       4
      </div>
      <div class="step-content">
       <h3>Digite Sem Preocupações!</h3>
       <p>Agora é só usar em qualquer app. O corretor vai te ajudar automaticamente!</p>
      </div>
     </div>
    </div>
   </div>
  </section>
  <section class="download" id="download">
   <h2>📲 Baixe Agora Grátis!</h2>
   <p>Disponível para Android 8.0 ou superior</p>
   <div class="download-links"><a href="#" class="store-badge"> <span style="font-size: 32px;">📱</span>
     <div style="text-align: left;">
      <div style="font-size: 12px; opacity: 0.7;">
       Disponível na
      </div>
      <div>
       Google Play
      </div>
     </div></a> <a href="#" class="store-badge"> <span style="font-size: 32px;">🔗</span>
     <div style="text-align: left;">
      <div style="font-size: 12px; opacity: 0.7;">
       Download
      </div>
      <div>
       APK Direto
      </div>
     </div></a>
   </div>
  </section>
  <footer>
   <div class="footer-content">
    <div class="footer-links"><a href="privacidade.html">Política de Privacidade</a> <a href="termos.html">Termos de Uso</a> <a href="mailto:contato@corretorapp.com">Contato</a> <a href="mailto:suportecorretorinteligente@gmail.com">Suporte</a> <a href="#" id="adminLink" style="opacity: 0.3; font-size: 10px;">•</a>
    </div>
    <div class="social-links"><a href="#" title="Instagram">📷</a> <a href="#" title="Twitter">🐦</a> <a href="#" title="Facebook">📘</a> <a href="#" title="GitHub">💻</a>
    </div>
    <p>© 2024 Corretor Inteligente. Todos os direitos reservados.</p>
    <p style="opacity: 0.7; margin-top: 10px;">Feito com 💜 no Brasil</p>
   </div>
  </footer><!-- MODAL DE LOGIN ADMIN -->
  <div id="adminModal" style="display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); z-index: 9999; justify-content: center; align-items: center;">
   <div style="background: white; padding: 40px; border-radius: 20px; max-width: 400px; width: 90%; box-shadow: 0 20px 60px rgba(0,0,0,0.3);">
    <h2 style="text-align: center; color: #8b5cf6; margin-bottom: 30px;">🔐 Admin Login</h2>
    <form id="adminLoginForm"><label for="adminPassword" style="display: block; margin-bottom: 10px; font-weight: 600; color: #2d3748;">Senha de Administrador:</label> <input type="password" id="adminPassword" style="width: 100%; padding: 12px; border: 2px solid #e2e8f0; border-radius: 10px; font-size: 16px; margin-bottom: 20px;" placeholder="Digite a senha"> <button type="submit" style="width: 100%; padding: 15px; background: linear-gradient(135deg, #8b5cf6 0%, #6366f1 100%); color: white; border: none; border-radius: 10px; font-size: 16px; font-weight: 600; cursor: pointer;">Entrar</button> <button type="button" id="closeModalBtn" style="width: 100%; padding: 15px; background: #f7fafc; color: #4a5568; border: 2px solid #e2e8f0; border-radius: 10px; font-size: 16px; font-weight: 600; cursor: pointer; margin-top: 10px;">Cancelar</button>
    </form>
    <p id="loginError" style="color: #dc2626; text-align: center; margin-top: 15px; display: none; font-weight: 600;"></p>
   </div>
  </div><!-- MODAL PREMIUM -->
  <div id="premiumModal" style="display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.85); z-index: 9998; justify-content: center; align-items: center; overflow-y: auto; padding: 20px;">
   <div style="background: white; padding: 50px; border-radius: 25px; max-width: 600px; width: 100%; box-shadow: 0 25px 70px rgba(0,0,0,0.4); position: relative;"><button id="closePremiumModal" style="position: absolute; top: 20px; right: 20px; background: #e2e8f0; border: none; width: 35px; height: 35px; border-radius: 50%; cursor: pointer; font-size: 20px; color: #64748b; transition: all 0.3s;">×</button>
    <div style="text-align: center; margin-bottom: 40px;">
     <div style="font-size: 60px; margin-bottom: 15px;">
      ⭐
     </div>
     <h2 style="color: #8b5cf6; font-size: 36px; margin-bottom: 10px;">Desbloqueie o Premium!</h2>
     <p style="color: #64748b; font-size: 16px;">Tenha acesso a recursos avançados por apenas <span style="color: #f59e0b; font-weight: 700; font-size: 24px;">R$ 10,00</span></p>
    </div>
    <div style="background: linear-gradient(135deg, #f7fafc 0%, #edf2f7 100%); padding: 30px; border-radius: 15px; margin-bottom: 30px;">
     <h3 style="color: #2d3748; margin-bottom: 20px; text-align: center;">✨ Recursos Premium:</h3>
     <div style="display: flex; flex-direction: column; gap: 15px;">
      <div style="display: flex; align-items: center; gap: 12px;"><span style="background: #10b981; color: white; width: 30px; height: 30px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: 700;">✓</span> <span style="color: #2d3748; font-weight: 600;"><strong>7.000 caracteres</strong> por análise (vs 500 grátis)</span>
      </div>
      <div style="display: flex; align-items: center; gap: 12px;"><span style="background: #10b981; color: white; width: 30px; height: 30px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: 700;">✓</span> <span style="color: #2d3748; font-weight: 600;">🤖 <strong>Detecção de IA</strong> com porcentagem de originalidade</span>
      </div>
      <div style="display: flex; align-items: center; gap: 12px;"><span style="background: #10b981; color: white; width: 30px; height: 30px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: 700;">✓</span> <span style="color: #2d3748; font-weight: 600;">📊 <strong>Análise de coerência</strong> textual avançada</span>
      </div>
      <div style="display: flex; align-items: center; gap: 12px;"><span style="background: #10b981; color: white; width: 30px; height: 30px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: 700;">✓</span> <span style="color: #2d3748; font-weight: 600;">📝 <strong>Correções de concordância</strong> verbal e nominal</span>
      </div>
      <div style="display: flex; align-items: center; gap: 12px;"><span style="background: #10b981; color: white; width: 30px; height: 30px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: 700;">✓</span> <span style="color: #2d3748; font-weight: 600;">🚀 <strong>Sem anúncios</strong> e processamento prioritário</span>
      </div>
     </div>
    </div>
    <div style="text-align: center;"><button id="activatePremiumBtn" style="background: linear-gradient(135deg, #f59e0b 0%, #d97706 100%); color: white; border: none; padding: 18px 50px; border-radius: 15px; font-size: 18px; font-weight: 700; cursor: pointer; transition: all 0.3s; box-shadow: 0 10px 25px rgba(245, 158, 11, 0.3); width: 100%;"> 🎉 Ativar Premium - R$ 10,00 </button>
     <p style="color: #94a3b8; font-size: 13px; margin-top: 15px;">💳 Pagamento único. Sem renovação automática.</p>
     <p style="color: #cbd5e0; font-size: 11px; margin-top: 8px; font-style: italic;">* Simulação - Em breve com pagamento real via PIX</p>
    </div>
   </div>
  </div><!-- PAINEL ADMIN -->
  <div id="adminPanel" style="display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.9); z-index: 9999; overflow-y: auto;">
   <div style="max-width: 800px; margin: 50px auto; background: white; padding: 40px; border-radius: 20px;">
    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 30px;">
     <h2 style="color: #8b5cf6; margin: 0;">⚙️ Painel de Administração</h2><button id="closeAdminBtn" style="padding: 10px 20px; background: #dc2626; color: white; border: none; border-radius: 10px; cursor: pointer; font-weight: 600;">Sair</button>
    </div>
    <div style="background: #f7fafc; padding: 20px; border-radius: 10px; margin-bottom: 30px;">
     <h3 style="color: #2d3748; margin-bottom: 20px;">📱 Link da Play Store</h3><label for="playStoreLink" style="display: block; margin-bottom: 10px; font-weight: 600; color: #4a5568;">URL do App:</label> <input type="url" id="playStoreLink" style="width: 100%; padding: 12px; border: 2px solid #e2e8f0; border-radius: 10px; margin-bottom: 15px;" placeholder="https://play.google.com/store/apps/details?id=..."> <button id="savePlayStore" style="padding: 12px 30px; background: #10b981; color: white; border: none; border-radius: 10px; cursor: pointer; font-weight: 600;">💾 Salvar Link</button>
    </div>
    <div style="background: #f7fafc; padding: 20px; border-radius: 10px; margin-bottom: 30px;">
     <h3 style="color: #2d3748; margin-bottom: 20px;">🔗 Link APK Direto</h3><label for="apkLink" style="display: block; margin-bottom: 10px; font-weight: 600; color: #4a5568;">URL do APK:</label> <input type="url" id="apkLink" style="width: 100%; padding: 12px; border: 2px solid #e2e8f0; border-radius: 10px; margin-bottom: 15px;" placeholder="https://seu-servidor.com/corretor.apk"> <button id="saveApk" style="padding: 12px 30px; background: #10b981; color: white; border: none; border-radius: 10px; cursor: pointer; font-weight: 600;">💾 Salvar Link</button>
    </div>
    <div style="background: #f7fafc; padding: 20px; border-radius: 10px; margin-bottom: 30px;">
     <h3 style="color: #2d3748; margin-bottom: 20px;">📧 Email de Contato</h3><label for="contactEmail" style="display: block; margin-bottom: 10px; font-weight: 600; color: #4a5568;">Email:</label> <input type="email" id="contactEmail" style="width: 100%; padding: 12px; border: 2px solid #e2e8f0; border-radius: 10px; margin-bottom: 15px;" placeholder="contato@corretorapp.com"> <button id="saveEmail" style="padding: 12px 30px; background: #10b981; color: white; border: none; border-radius: 10px; cursor: pointer; font-weight: 600;">💾 Salvar Email</button>
    </div>
    <div style="background: #fef3c7; padding: 20px; border-radius: 10px; border-left: 4px solid #f59e0b;">
     <h3 style="color: #92400e; margin-bottom: 15px;">🔑 Trocar Senha Admin</h3><label for="newPassword" style="display: block; margin-bottom: 10px; font-weight: 600; color: #78350f;">Nova Senha:</label> <input type="password" id="newPassword" style="width: 100%; padding: 12px; border: 2px solid #fbbf24; border-radius: 10px; margin-bottom: 15px;" placeholder="Digite a nova senha"> <button id="changePassword" style="padding: 12px 30px; background: #f59e0b; color: white; border: none; border-radius: 10px; cursor: pointer; font-weight: 600;">🔒 Alterar Senha</button>
    </div>
    <div style="background: #dbeafe; padding: 20px; border-radius: 10px; margin-top: 30px; border-left: 4px solid #3b82f6;">
     <h3 style="color: #1e40af; margin-bottom: 15px;">📝 Gerenciar Palavras Personalizadas</h3>
     <p style="color: #1e3a8a; margin-bottom: 20px; font-size: 14px;">Adicione palavras que o corretor deve corrigir automaticamente</p>
     <div style="display: flex; gap: 10px; margin-bottom: 20px; flex-wrap: wrap;">
      <div style="flex: 1; min-width: 200px;"><label for="wrongWord" style="display: block; margin-bottom: 8px; font-weight: 600; color: #1e40af; font-size: 14px;">Palavra Errada:</label> <input type="text" id="wrongWord" style="width: 100%; padding: 10px; border: 2px solid #93c5fd; border-radius: 8px; font-size: 14px;" placeholder="Ex: bunitinha">
      </div>
      <div style="flex: 1; min-width: 200px;"><label for="correctWord" style="display: block; margin-bottom: 8px; font-weight: 600; color: #1e40af; font-size: 14px;">Palavra Correta:</label> <input type="text" id="correctWord" style="width: 100%; padding: 10px; border: 2px solid #93c5fd; border-radius: 8px; font-size: 14px;" placeholder="Ex: bonitinha">
      </div>
     </div><button id="addCustomWord" style="padding: 12px 30px; background: #3b82f6; color: white; border: none; border-radius: 10px; cursor: pointer; font-weight: 600; margin-bottom: 20px;">➕ Adicionar Palavra</button>
     <div style="background: white; padding: 15px; border-radius: 10px; max-height: 300px; overflow-y: auto;">
      <h4 style="color: #1e40af; margin-bottom: 15px; font-size: 16px;">Palavras Cadastradas (<span id="customWordCount">0</span>):</h4>
      <div id="customWordsList" style="display: flex; flex-direction: column; gap: 8px;">
       <p style="color: #64748b; text-align: center; padding: 20px;">Nenhuma palavra personalizada cadastrada ainda</p>
      </div>
     </div>
    </div>
    <div id="successMsg" style="display: none; background: #d1fae5; padding: 15px; border-radius: 10px; margin-top: 20px; color: #065f46; font-weight: 600; text-align: center;"></div>
   </div>
  </div>
  <script>
        // Dicionário expandido de correções
        const corrections = {
            // Erros comuns de digitação e semelhança fonética
            'bunitinha': 'bonitinha',
            'bunitu': 'bonito',
            'bunito': 'bonito',
            'bunita': 'bonita',
            'biito': 'bonito',
            'lindu': 'lindo',
            'linda': 'linda',
            'lindo': 'lindo',
            'muinto': 'muito',
            'munto': 'muito',
            'presiza': 'precisa',
            'presiso': 'preciso',
            'intao': 'então',
            'vc': 'você',
            'tb': 'também',
            'tbm': 'também',
            'pq': 'porque',
            'td': 'tudo',
            'msg': 'mensagem',
            'hj': 'hoje',
            'agr': 'agora',
            'dps': 'depois',
            'blz': 'beleza',
            'flw': 'falou',
            'vlw': 'valeu',
            'obg': 'obrigado',
            'obgd': 'obrigado',
            'obgda': 'obrigada',
            'sdd': 'saudade',
            'sdds': 'saudades',
            'kk': 'rsrs',
            'kkk': 'rsrsrs',
            'mt': 'muito',
            'mto': 'muito',
            'nois': 'nós',
            'axo': 'acho',
            'di': 'de',
            'ki': 'que',
            'naum': 'não',
            'num': 'não',
            'eh': 'é',
            'tah': 'está',
            'tava': 'estava',
            // Erros comuns de acentuação
            'portugues': 'português',
            'voce': 'você',
            'nao': 'não',
            'tambem': 'também',
            'ate': 'até',
            'esta': 'está',
            'sao': 'são',
            'so': 'só',
            'pra': 'para',
            'automatico': 'automático',
            'rapido': 'rápido',
            'facil': 'fácil',
            'util': 'útil',
            'publico': 'público',
            'basico': 'básico',
            'proximo': 'próximo',
            'numero': 'número',
            'codigo': 'código',
            'frances': 'francês',
            'ingles': 'inglês',
            'pais': 'país',
            'cafe': 'café',
            'pe': 'pé',
            'po': 'pó',
            'agradavel': 'agradável',
            'responsavel': 'responsável',
            'incrivel': 'incrível',
            'dificil': 'difícil',
            'movel': 'móvel',
            'possivel': 'possível',
            'pratico': 'prático',
            'simpatico': 'simpático',
            'otimo': 'ótimo',
            'unico': 'único',
            'logico': 'lógico',
            'tecnico': 'técnico',
            'eletronico': 'eletrônico',
            'mecanico': 'mecânico',
            'organico': 'orgânico',
            'fantastico': 'fantástico',
            'romantico': 'romântico',
            'economico': 'econômico',
            'historico': 'histórico',
            'cientifico': 'científico',
            'massa': 'massa',
            'legal': 'legal',
            'maneiro': 'maneiro',
            'bacana': 'bacana',
            'fofo': 'fofo',
            'fofinho': 'fofinho',
            'fofinha': 'fofinha',
            'amor': 'amor',
            'delicia': 'delícia',
            'gostoso': 'gostoso',
            'horror': 'horror',
            'pena': 'pena',
            'triste': 'triste',
            'saudade': 'saudade',
            'chato': 'chato',
            'ruim': 'ruim',
            'pessimo': 'péssimo',
            'demais': 'demais',
            'sensacional': 'sensacional'
        };

        let punctuationAdded = 0;
        let capitalizationFixed = 0;

        const textInput = document.getElementById('textInput');
        const correctBtn = document.getElementById('correctBtn');
        const synonymBtn = document.getElementById('synonymBtn');
        const clearBtn = document.getElementById('clearBtn');
        const statsBar = document.getElementById('statsBar');
        const correctionsDisplay = document.getElementById('correctionsDisplay');
        const wordCount = document.getElementById('wordCount');
        const errorCount = document.getElementById('errorCount');
        const correctionCount = document.getElementById('correctionCount');

        let foundCorrections = [];

        // ===== SISTEMA PREMIUM =====
        const FREE_LIMIT = 500; // caracteres
        const PREMIUM_LIMIT = 7000; // caracteres
        const PREMIUM_PRICE = 10; // reais
        let isPremiumUser = localStorage.getItem('isPremium') === 'true';

        // NOVO: Dicionário de sinônimos
        const synonyms = {
            'bom': ['ótimo', 'excelente', 'maravilhoso', 'legal'],
            'ruim': ['péssimo', 'terrível', 'horrível', 'desagradável'],
            'grande': ['enorme', 'gigante', 'vasto', 'amplo'],
            'pequeno': ['minúsculo', 'diminuto', 'reduzido', 'compacto'],
            'feliz': ['alegre', 'contente', 'satisfeito', 'radiante'],
            'triste': ['melancólico', 'deprimido', 'abatido', 'desanimado'],
            'bonito': ['belo', 'lindo', 'formoso', 'atraente'],
            'feio': ['horrível', 'desagradável', 'repulsivo', 'grotesco'],
            'rápido': ['veloz', 'ágil', 'ligeiro', 'acelerado'],
            'devagar': ['lento', 'vagaroso', 'moroso', 'demorado'],
            'difícil': ['complicado', 'árduo', 'trabalhoso', 'complexo'],
            'fácil': ['simples', 'prático', 'elementar', 'descomplicado'],
            'importante': ['relevante', 'significativo', 'essencial', 'fundamental'],
            'novo': ['recente', 'moderno', 'atual', 'inédito'],
            'velho': ['antigo', 'arcaico', 'obsoleto', 'ultrapassado'],
            'quente': ['ardente', 'escaldante', 'caloroso', 'tórrido'],
            'frio': ['gelado', 'gélido', 'congelante', 'glacial'],
            'fazer': ['realizar', 'executar', 'efetuar', 'produzir'],
            'ver': ['observar', 'visualizar', 'contemplar', 'avistar'],
            'dizer': ['falar', 'expressar', 'declarar', 'afirmar'],
            'gostar': ['apreciar', 'adorar', 'curtir', 'amar'],
            'casa': ['residência', 'moradia', 'lar', 'domicílio'],
            'trabalho': ['emprego', 'ocupação', 'ofício', 'profissão'],
            'pessoa': ['indivíduo', 'sujeito', 'ser', 'cidadão']
        };

        // NOVO: Regras gramaticais básicas
        const grammarRules = [
            {
                pattern: /\b(mais|menos)\s+(melhor|pior)\b/gi,
                error: 'redundância (mais melhor/mais pior)',
                fix: (match) => match.replace(/mais\s+/gi, '').replace(/menos\s+/gi, '')
            },
            {
                pattern: /\b(mim|ti)\s+(fazer|ir|ver|ter|ser|estar)\b/gi,
                error: 'uso incorreto de pronome oblíquo antes de verbo',
                fix: (match) => match.replace(/mim/gi, 'eu').replace(/ti\s+/gi, 'tu ')
            }
        ];

        // Atualizar contador de caracteres
        textInput.addEventListener('input', () => {
            const charCount = textInput.value.length;
            const limit = isPremiumUser ? PREMIUM_LIMIT : FREE_LIMIT;
            const charCounter = document.getElementById('charCounter');
            
            charCounter.textContent = `${charCount} / ${limit}`;
            
            // Mudar cor conforme se aproxima do limite
            if (charCount > limit) {
                charCounter.style.color = '#dc2626';
                charCounter.style.fontWeight = '700';
                textInput.style.borderColor = '#dc2626';
            } else if (charCount > limit * 0.8) {
                charCounter.style.color = '#f59e0b';
                charCounter.style.fontWeight = '700';
                textInput.style.borderColor = '#f59e0b';
            } else {
                charCounter.style.color = '#64748b';
                charCounter.style.fontWeight = '600';
                textInput.style.borderColor = '#e2e8f0';
            }
        });

        // Atualizar indicador de plano
        function updatePlanIndicator() {
            const planBadge = document.getElementById('planBadge');
            const charCounter = document.getElementById('charCounter');
            const upgradBtn = document.getElementById('upgradBtn');
            
            if (isPremiumUser) {
                planBadge.style.background = 'linear-gradient(135deg, #f59e0b 0%, #d97706 100%)';
                planBadge.style.color = 'white';
                planBadge.textContent = '⭐ PREMIUM';
                charCounter.textContent = `0 / ${PREMIUM_LIMIT}`;
                upgradBtn.style.display = 'none';
            } else {
                planBadge.style.background = '#cbd5e0';
                planBadge.style.color = '#1a202c';
                planBadge.textContent = 'GRÁTIS';
                charCounter.textContent = `0 / ${FREE_LIMIT}`;
                upgradBtn.style.display = 'block';
            }
        }

        updatePlanIndicator();

        correctBtn.addEventListener('click', () => {
            const text = textInput.value.trim();
            
            if (!text) {
                showToast('Por favor, digite algum texto primeiro!', 'error');
                return;
            }

            // Verificar limite
            const limit = isPremiumUser ? PREMIUM_LIMIT : FREE_LIMIT;
            if (text.length > limit) {
                showToast(`Limite de ${limit} caracteres excedido! ${isPremiumUser ? '' : 'Assine o Premium para até 7.000 caracteres.'}`, 'error');
                if (!isPremiumUser) {
                    document.getElementById('premiumModal').style.display = 'flex';
                }
                return;
            }

            correctBtn.disabled = true;
            correctionsDisplay.innerHTML = '<div class="loading"><div class="spinner"></div><p>Analisando seu texto...</p></div>';
            statsBar.style.display = 'none';

            // Simular processamento
            setTimeout(() => {
                processText(text);
                correctBtn.disabled = false;
            }, 800);
        });

        synonymBtn.addEventListener('click', () => {
            const text = textInput.value.trim();
            
            if (!text) {
                showToast('Por favor, digite algum texto primeiro!', 'error');
                return;
            }

            const limit = isPremiumUser ? PREMIUM_LIMIT : FREE_LIMIT;
            if (text.length > limit) {
                showToast(`Limite de ${limit} caracteres excedido!`, 'error');
                if (!isPremiumUser) {
                    document.getElementById('premiumModal').style.display = 'flex';
                }
                return;
            }

            synonymBtn.disabled = true;
            correctionsDisplay.innerHTML = '<div class="loading"><div class="spinner"></div><p>Procurando sinônimos...</p></div>';
            
            setTimeout(() => {
                showSynonyms(text);
                synonymBtn.disabled = false;
            }, 600);
        });

        // Botão de detectar IA
        document.getElementById('aiDetectBtn').addEventListener('click', () => {
            if (!isPremiumUser) {
                document.getElementById('premiumModal').style.display = 'flex';
                return;
            }

            const text = textInput.value.trim();
            if (!text) {
                showToast('Por favor, digite algum texto primeiro!', 'error');
                return;
            }

            if (text.length > PREMIUM_LIMIT) {
                showToast(`Limite de ${PREMIUM_LIMIT} caracteres excedido!`, 'error');
                return;
            }

            document.getElementById('aiDetectBtn').disabled = true;
            correctionsDisplay.innerHTML = '<div class="loading"><div class="spinner"></div><p>🤖 Analisando probabilidade de IA...</p></div>';
            
            setTimeout(() => {
                detectAI(text);
                document.getElementById('aiDetectBtn').disabled = false;
            }, 1500);
        });

        // Botão de análise de coerência
        document.getElementById('coherenceBtn').addEventListener('click', () => {
            if (!isPremiumUser) {
                document.getElementById('premiumModal').style.display = 'flex';
                return;
            }

            const text = textInput.value.trim();
            if (!text) {
                showToast('Por favor, digite algum texto primeiro!', 'error');
                return;
            }

            if (text.length > PREMIUM_LIMIT) {
                showToast(`Limite de ${PREMIUM_LIMIT} caracteres excedido!`, 'error');
                return;
            }

            document.getElementById('coherenceBtn').disabled = true;
            correctionsDisplay.innerHTML = '<div class="loading"><div class="spinner"></div><p>📊 Analisando coerência textual...</p></div>';
            
            setTimeout(() => {
                analyzeCoherence(text);
                document.getElementById('coherenceBtn').disabled = false;
            }, 1200);
        });

        clearBtn.addEventListener('click', () => {
            textInput.value = '';
            correctionsDisplay.innerHTML = '';
            statsBar.style.display = 'none';
            document.getElementById('correctedTextBox').style.display = 'none';
            document.getElementById('copySuccess').style.display = 'none';
            foundCorrections = [];
        });

        function processText(text) {
            // Separar palavras
            const words = text.toLowerCase().match(/\b[a-záàâãéèêíïóôõöúçñ]+\b/gi) || [];
            foundCorrections = [];
            punctuationAdded = 0;
            capitalizationFixed = 0;
            let correctedText = text;

            // NOVO: Aplicar regras gramaticais
            grammarRules.forEach(rule => {
                if (rule.fix) {
                    const matches = correctedText.match(rule.pattern);
                    if (matches) {
                        matches.forEach(match => {
                            const fixed = rule.fix(match);
                            if (fixed !== match) {
                                foundCorrections.push({
                                    wrong: match,
                                    correct: fixed,
                                    type: '⚠️ Gramática'
                                });
                                correctedText = correctedText.replace(match, fixed);
                            }
                        });
                    }
                }
            });

            // PREMIUM: Correções de concordância verbal e nominal
            if (isPremiumUser) {
                // Concordância verbal: sujeito plural + verbo singular
                const concordanciaVerbal = [
                    { pattern: /\b(os|as)\s+([a-záàâãéèêíïóôõöúçñ]+)\s+(é|está|foi|era|vai|tem)\b/gi, type: 'sujeito plural + verbo singular' },
                    { pattern: /\b(o|a)\s+([a-záàâãéèêíïóôõöúçñ]+)\s+(são|estão|foram|eram|vão|têm)\b/gi, type: 'sujeito singular + verbo plural' },
                    { pattern: /\b(nós|vocês|eles|elas)\s+(é|está|foi|era|vai|tem)\b/gi, type: 'pronome plural + verbo singular' },
                    { pattern: /\b(eu|você|ele|ela)\s+(são|estão|foram|eram|vão|têm)\b/gi, type: 'pronome singular + verbo plural' }
                ];

                concordanciaVerbal.forEach(rule => {
                    const matches = correctedText.match(rule.pattern);
                    if (matches) {
                        matches.forEach(match => {
                            let fixed = match;
                            // Pluralizar ou singularizar verbo
                            fixed = fixed.replace(/\bé\b/gi, 'são');
                            fixed = fixed.replace(/\bestá\b/gi, 'estão');
                            fixed = fixed.replace(/\bfoi\b/gi, 'foram');
                            fixed = fixed.replace(/\bera\b/gi, 'eram');
                            fixed = fixed.replace(/\bvai\b/gi, 'vão');
                            fixed = fixed.replace(/\btem\b/gi, 'têm');
                            fixed = fixed.replace(/\bsão\b/gi, 'é');
                            fixed = fixed.replace(/\bestão\b/gi, 'está');
                            fixed = fixed.replace(/\bforam\b/gi, 'foi');
                            fixed = fixed.replace(/\beram\b/gi, 'era');
                            fixed = fixed.replace(/\bvão\b/gi, 'vai');
                            fixed = fixed.replace(/\btêm\b/gi, 'tem');
                            
                            if (fixed !== match) {
                                foundCorrections.push({
                                    wrong: match,
                                    correct: fixed,
                                    type: '👥 Concordância (PRO)'
                                });
                                correctedText = correctedText.replace(match, fixed);
                            }
                        });
                    }
                });
            }

            // NOVO: Corrigir frases exclamativas (como "que bunitinha" → "Que bonitinha!")
            const exclamationPatterns = [
                /\b(que)\s+(bunitinha|bunitu|bunito|bunita|biito)\b/gi,
                /\b(que)\s+(lindu|linda|lindo)\b/gi,
                /\b(que)\s+(massa|legal|maneiro|bacana|show|top)\b/gi,
                /\b(que)\s+(incrivel|maravilha|perfeito|fantastico|sensacional)\b/gi,
                /\b(que)\s+(fofo|fofinho|fofinha|amor|delicia|gostoso)\b/gi,
                /\b(que)\s+(horror|pena|triste|saudade|chato|ruim|pessimo)\b/gi,
                /\b(que)\s+(otimo|demais|da\s+hora)\b/gi,
                /\b(que)\s+(loucura|absurdo)\b/gi
            ];

            exclamationPatterns.forEach(pattern => {
                const matches = correctedText.match(pattern);
                if (matches) {
                    matches.forEach(match => {
                        const words = match.trim().split(/\s+/);
                        let secondWord = words[1].toLowerCase();
                        
                        // Corrigir ortografia da segunda palavra se necessário
                        if (corrections[secondWord]) {
                            secondWord = corrections[secondWord];
                        }
                        
                        // Capitalizar primeira letra e adicionar ponto de exclamação
                        const correctedPhrase = 'Que ' + secondWord + '!';
                        
                        // Verificar se não termina com pontuação já
                        const regex = new RegExp('\\b' + match.replace(/[.*+?^${}()|[\]\\]/g, '\\$&') + '(?![!?.])', 'gi');
                        
                        if (correctedText.match(regex)) {
                            foundCorrections.push({
                                wrong: match,
                                correct: correctedPhrase,
                                type: '🎉 Exclamação'
                            });
                            correctedText = correctedText.replace(regex, correctedPhrase);
                        }
                    });
                }
            });

            // NOVO: Detectar e corrigir perguntas (adicionar ? no final)
            const questionWords = [
                'como', 'quando', 'onde', 'por que', 'porque', 'pq', 'qual', 'quais', 
                'quanto', 'quantos', 'quanta', 'quantas', 'quem', 'o que', 'que',
                'cadê', 'cade', 'tem', 'há', 'existe', 'será', 'sera', 'pode', 'poderia',
                'vai', 'vou', 'vamos', 'quer', 'gostaria', 'sabe', 'conhece', 'entende'
            ];

            // Dividir texto em sentenças
            const sentences = correctedText.split(/([.!?\n]+)/);
            
            for (let i = 0; i < sentences.length; i++) {
                let sentence = sentences[i].trim();
                
                // Pular se for apenas pontuação ou vazio
                if (!sentence || /^[.!?\n]+$/.test(sentence)) continue;
                
                // Verificar se já tem pontuação no final
                const lastChar = sentence[sentence.length - 1];
                if (/[.!?]/.test(lastChar)) continue;
                
                // Verificar se começa com palavra interrogativa
                const firstWords = sentence.toLowerCase().split(/\s+/).slice(0, 3).join(' ');
                const isQuestion = questionWords.some(word => {
                    const pattern = new RegExp('^' + word + '\\b', 'i');
                    return pattern.test(firstWords);
                });
                
                if (isQuestion) {
                    // Capitalizar primeira letra se necessário
                    let correctedSentence = sentence;
                    if (sentence[0] === sentence[0].toLowerCase()) {
                        correctedSentence = sentence[0].toUpperCase() + sentence.slice(1);
                    }
                    correctedSentence += '?';
                    
                    sentences[i] = correctedSentence;
                    
                    foundCorrections.push({
                        wrong: sentence,
                        correct: correctedSentence,
                        type: '❓ Pergunta'
                    });
                }
            }
            
            correctedText = sentences.join('');

            // 1. Corrigir ortografia
            words.forEach(word => {
                const lowerWord = word.toLowerCase();
                if (corrections[lowerWord]) {
                    foundCorrections.push({
                        wrong: word,
                        correct: corrections[lowerWord],
                        type: '���️ Ortografia'
                    });

                    // Substituir no texto (mantendo capitalização aproximada)
                    const isCapitalized = word[0] === word[0].toUpperCase();
                    const correctWord = isCapitalized 
                        ? corrections[lowerWord].charAt(0).toUpperCase() + corrections[lowerWord].slice(1)
                        : corrections[lowerWord];
                    
                    const regex = new RegExp('\\b' + word + '\\b', 'gi');
                    correctedText = correctedText.replace(regex, correctWord);
                }
            });

            // 2. Adicionar pontos finais em frases sem pontuação
            const sentences = correctedText.split('\n');
            correctedText = sentences.map(sentence => {
                sentence = sentence.trim();
                if (sentence.length > 0) {
                    // Verifica se termina com pontuação
                    const lastChar = sentence[sentence.length - 1];
                    if (!/[.!?;:,]/.test(lastChar)) {
                        punctuationAdded++;
                        foundCorrections.push({
                            wrong: 'falta de ponto final',
                            correct: 'ponto adicionado',
                            type: '📝 Pontuação'
                        });
                        return sentence + '.';
                    }
                }
                return sentence;
            }).join('\n');

            // 3. Capitalizar primeira letra após pontos
            correctedText = correctedText.replace(/([.!?;:]\s+)([a-záàâãéèêíïóôõöúçñ])/g, (match, punct, letter) => {
                capitalizationFixed++;
                return punct + letter.toUpperCase();
            });

            // 4. Capitalizar primeira letra do texto
            if (correctedText.length > 0 && /[a-záàâãéèêíïóôõöúçñ]/.test(correctedText[0])) {
                const firstLetter = correctedText[0];
                if (firstLetter === firstLetter.toLowerCase()) {
                    correctedText = firstLetter.toUpperCase() + correctedText.slice(1);
                    capitalizationFixed++;
                    foundCorrections.push({
                        wrong: 'letra minúscula no início',
                        correct: 'primeira letra maiúscula',
                        type: '🔤 Capitalização'
                    });
                }
            }

            // 5. Capitalizar primeira letra após quebras de linha
            correctedText = correctedText.replace(/(\n)([a-záàâãéèêíïóôõöúçñ])/g, (match, newline, letter) => {
                if (letter === letter.toLowerCase()) {
                    capitalizationFixed++;
                    return newline + letter.toUpperCase();
                }
                return match;
            });

            // Aplicar texto corrigido
            if (foundCorrections.length > 0 || punctuationAdded > 0 || capitalizationFixed > 0) {
                textInput.value = correctedText;
            }

            // Mostrar estatísticas
            const totalCorrections = foundCorrections.length;
            updateStats(words.length, totalCorrections);
            displayCorrections();
        }

        function updateStats(words, errors) {
            wordCount.textContent = words;
            errorCount.textContent = errors;
            correctionCount.textContent = errors;
            statsBar.style.display = 'flex';
        }

        function showSynonyms(text) {
            const words = text.toLowerCase().match(/\b[a-záàâãéèêíïóôõöúçñ]+\b/gi) || [];
            const foundSynonyms = [];
            
            words.forEach(word => {
                const lowerWord = word.toLowerCase();
                if (synonyms[lowerWord]) {
                    foundSynonyms.push({
                        word: word,
                        options: synonyms[lowerWord]
                    });
                }
            });

            if (foundSynonyms.length === 0) {
                correctionsDisplay.innerHTML = `
                    <div class="no-errors">
                        <span style="font-size: 32px; display: block; margin-bottom: 10px;">💭</span>
                        Nenhum sinônimo disponível para as palavras do texto.
                    </div>
                `;
                statsBar.style.display = 'none';
            } else {
                let html = '<h3>📚 Sugestões de Sinônimos:</h3>';
                correctionsDisplay.innerHTML = html;
                
                foundSynonyms.forEach((item, index) => {
                    setTimeout(() => {
                        const synonymItem = document.createElement('div');
                        synonymItem.className = 'correction-item';
                        synonymItem.style.background = '#e0f2fe';
                        synonymItem.style.borderLeftColor = '#0284c7';
                        
                        const synonymList = item.options.map(syn => 
                            `<span style="background: white; padding: 4px 10px; border-radius: 15px; margin: 3px; display: inline-block; cursor: pointer; transition: transform 0.2s;" onmouseover="this.style.transform='scale(1.05)'" onmouseout="this.style.transform='scale(1)'" onclick="replaceSynonym('${item.word}', '${syn}')">${syn}</span>`
                        ).join('');
                        
                        synonymItem.innerHTML = `
                            <div style="width: 100%;">
                                <div style="font-weight: 600; color: #0c4a6e; margin-bottom: 10px;">
                                    "${item.word}" pode ser substituído por:
                                </div>
                                <div style="display: flex; flex-wrap: wrap; gap: 5px;">
                                    ${synonymList}
                                </div>
                            </div>
                        `;
                        correctionsDisplay.appendChild(synonymItem);
                    }, index * 150);
                });

                statsBar.style.display = 'flex';
                wordCount.textContent = words.length;
                errorCount.textContent = foundSynonyms.length;
                correctionCount.textContent = 'Palavras com sinônimos';
                document.querySelector('.stat:nth-child(3) .stat-label').textContent = 'Sugestões';
            }

            document.getElementById('correctedTextBox').style.display = 'none';
        }

        function replaceSynonym(originalWord, synonym) {
            const text = textInput.value;
            const regex = new RegExp('\\b' + originalWord + '\\b', 'gi');
            
            const newText = text.replace(regex, (match) => {
                // Manter capitalização original
                if (match[0] === match[0].toUpperCase()) {
                    return synonym.charAt(0).toUpperCase() + synonym.slice(1);
                }
                return synonym;
            });
            
            textInput.value = newText;
            
            // Mostrar feedback
            showToast(`✅ "${originalWord}" substituído por "${synonym}"!`, 'success');
        }

        // Função para detectar texto gerado por IA
        function detectAI(text) {
            const sentences = text.split(/[.!?]+/).filter(s => s.trim().length > 0);
            const words = text.match(/\b[a-záàâãéèêíïóôõöúçñ]+\b/gi) || [];
            
            // Indicadores de texto gerado por IA (simulação)
            let aiScore = 0;
            
            // 1. Vocabulário muito formal e repetitivo
            const formalWords = ['ademais', 'outrossim', 'destarte', 'portanto', 'todavia', 'contudo', 'entretanto'];
            const formalCount = words.filter(w => formalWords.includes(w.toLowerCase())).length;
            aiScore += (formalCount / words.length) * 30;
            
            // 2. Frases muito longas e estruturadas
            const avgSentenceLength = words.length / sentences.length;
            if (avgSentenceLength > 20) aiScore += 20;
            
            // 3. Pouca variação de vocabulário
            const uniqueWords = new Set(words.map(w => w.toLowerCase()));
            const vocabularyRatio = uniqueWords.size / words.length;
            if (vocabularyRatio < 0.5) aiScore += 25;
            
            // 4. Uso excessivo de conectivos
            const conectivos = ['além disso', 'por outro lado', 'dessa forma', 'nesse sentido', 'em suma'];
            let conectivoCount = 0;
            conectivos.forEach(c => {
                if (text.toLowerCase().includes(c)) conectivoCount++;
            });
            aiScore += (conectivoCount / sentences.length) * 25;
            
            // Limitar entre 0-100
            aiScore = Math.min(100, Math.max(0, aiScore));
            const originalityScore = 100 - aiScore;
            
            // Determinar categoria
            let category, categoryColor, recommendation;
            if (aiScore < 30) {
                category = 'Provavelmente Humano';
                categoryColor = '#10b981';
                recommendation = 'O texto apresenta características naturais de escrita humana.';
            } else if (aiScore < 60) {
                category = 'Possível Edição de IA';
                categoryColor = '#f59e0b';
                recommendation = 'O texto pode ter sido escrito com auxílio de IA ou apresenta padrões formais.';
            } else {
                category = 'Alta Probabilidade de IA';
                categoryColor = '#ef4444';
                recommendation = 'O texto apresenta fortes características de geração por IA.';
            }

            statsBar.style.display = 'none';
            document.getElementById('correctedTextBox').style.display = 'none';
            
            correctionsDisplay.innerHTML = `
                <div style="text-align: center; padding: 30px; background: linear-gradient(135deg, #f7fafc 0%, #edf2f7 100%); border-radius: 15px;">
                    <h3 style="color: #2d3748; font-size: 24px; margin-bottom: 30px;">🤖 Análise de Detecção de IA</h3>
                    
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-bottom: 30px;">
                        <div style="background: white; padding: 25px; border-radius: 15px; box-shadow: 0 4px 15px rgba(0,0,0,0.08);">
                            <div style="font-size: 48px; font-weight: 700; color: ${categoryColor}; margin-bottom: 10px;">${aiScore.toFixed(1)}%</div>
                            <div style="font-size: 14px; color: #64748b; font-weight: 600;">Probabilidade de IA</div>
                            <div style="width: 100%; height: 8px; background: #e2e8f0; border-radius: 10px; margin-top: 15px; overflow: hidden;">
                                <div style="width: ${aiScore}%; height: 100%; background: ${categoryColor}; transition: width 1s ease;"></div>
                            </div>
                        </div>
                        
                        <div style="background: white; padding: 25px; border-radius: 15px; box-shadow: 0 4px 15px rgba(0,0,0,0.08);">
                            <div style="font-size: 48px; font-weight: 700; color: #10b981; margin-bottom: 10px;">${originalityScore.toFixed(1)}%</div>
                            <div style="font-size: 14px; color: #64748b; font-weight: 600;">Originalidade Humana</div>
                            <div style="width: 100%; height: 8px; background: #e2e8f0; border-radius: 10px; margin-top: 15px; overflow: hidden;">
                                <div style="width: ${originalityScore}%; height: 100%; background: #10b981; transition: width 1s ease;"></div>
                            </div>
                        </div>
                    </div>
                    
                    <div style="background: ${categoryColor}20; border-left: 4px solid ${categoryColor}; padding: 20px; border-radius: 10px; text-align: left; margin-bottom: 20px;">
                        <div style="font-weight: 700; color: ${categoryColor}; font-size: 18px; margin-bottom: 10px;">📋 Classificação: ${category}</div>
                        <div style="color: #4a5568; line-height: 1.6;">${recommendation}</div>
                    </div>
                    
                    <div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 15px; text-align: left;">
                        <div style="background: white; padding: 15px; border-radius: 10px;">
                            <div style="color: #8b5cf6; font-weight: 700; margin-bottom: 5px;">📏 Média de palavras/frase</div>
                            <div style="color: #2d3748; font-size: 24px; font-weight: 700;">${avgSentenceLength.toFixed(1)}</div>
                        </div>
                        <div style="background: white; padding: 15px; border-radius: 10px;">
                            <div style="color: #8b5cf6; font-weight: 700; margin-bottom: 5px;">📚 Variação vocabular</div>
                            <div style="color: #2d3748; font-size: 24px; font-weight: 700;">${(vocabularyRatio * 100).toFixed(1)}%</div>
                        </div>
                    </div>
                    
                    <div style="margin-top: 20px; padding: 15px; background: #dbeafe; border-radius: 10px; font-size: 13px; color: #1e40af;">
                        ℹ️ Esta análise é baseada em heurísticas e padrões estatísticos. Não é 100% precisa.
                    </div>
                </div>
            `;
        }

        // Função para analisar coerência textual
        function analyzeCoherence(text) {
            const sentences = text.split(/[.!?]+/).filter(s => s.trim().length > 0);
            const words = text.match(/\b[a-záàâãéèêíïóôõöúçñ]+\b/gi) || [];
            
            let coherenceScore = 100;
            const issues = [];
            
            // 1. Verificar conectivos e coesão
            const conectivos = ['portanto', 'entretanto', 'todavia', 'além disso', 'por outro lado', 'dessa forma', 'assim', 'porém', 'contudo'];
            let hasConectivos = false;
            conectivos.forEach(c => {
                if (text.toLowerCase().includes(c)) hasConectivos = true;
            });
            if (!hasConectivos && sentences.length > 3) {
                coherenceScore -= 15;
                issues.push('Faltam conectivos para melhor coesão entre frases');
            }
            
            // 2. Repetição excessiva de palavras
            const wordFreq = {};
            words.forEach(w => {
                const lower = w.toLowerCase();
                wordFreq[lower] = (wordFreq[lower] || 0) + 1;
            });
            const repeatedWords = Object.entries(wordFreq).filter(([word, count]) => count > 5 && word.length > 4);
            if (repeatedWords.length > 0) {
                coherenceScore -= repeatedWords.length * 5;
                issues.push(`Palavras muito repetidas: ${repeatedWords.map(([w]) => w).join(', ')}`);
            }
            
            // 3. Frases muito curtas ou muito longas
            let shortSentences = 0;
            let longSentences = 0;
            sentences.forEach(s => {
                const wordCount = s.trim().split(/\s+/).length;
                if (wordCount < 5) shortSentences++;
                if (wordCount > 30) longSentences++;
            });
            if (shortSentences > sentences.length * 0.4) {
                coherenceScore -= 10;
                issues.push('Muitas frases muito curtas prejudicam a fluência');
            }
            if (longSentences > sentences.length * 0.3) {
                coherenceScore -= 10;
                issues.push('Frases muito longas dificultam a compreensão');
            }
            
            // 4. Falta de pontuação adequada
            const commaCount = (text.match(/,/g) || []).length;
            if (commaCount < sentences.length * 0.5 && words.length > 100) {
                coherenceScore -= 10;
                issues.push('Uso insuficiente de vírgulas para organizar ideias');
            }
            
            coherenceScore = Math.max(0, Math.min(100, coherenceScore));
            
            let category, categoryColor, recommendation;
            if (coherenceScore >= 80) {
                category = 'Excelente Coerência';
                categoryColor = '#10b981';
                recommendation = 'O texto está bem estruturado e coerente.';
            } else if (coherenceScore >= 60) {
                category = 'Boa Coerência';
                categoryColor = '#3b82f6';
                recommendation = 'O texto é compreensível, mas pode melhorar em alguns aspectos.';
            } else if (coherenceScore >= 40) {
                category = 'Coerência Moderada';
                categoryColor = '#f59e0b';
                recommendation = 'O texto precisa de melhorias na estruturação e coesão.';
            } else {
                category = 'Baixa Coerência';
                categoryColor = '#ef4444';
                recommendation = 'O texto apresenta problemas significativos de coerência.';
            }

            statsBar.style.display = 'none';
            document.getElementById('correctedTextBox').style.display = 'none';
            
            correctionsDisplay.innerHTML = `
                <div style="padding: 30px; background: linear-gradient(135deg, #f7fafc 0%, #edf2f7 100%); border-radius: 15px;">
                    <h3 style="color: #2d3748; font-size: 24px; margin-bottom: 30px; text-align: center;">📊 Análise de Coerência Textual</h3>
                    
                    <div style="text-align: center; background: white; padding: 30px; border-radius: 15px; margin-bottom: 25px; box-shadow: 0 4px 15px rgba(0,0,0,0.08);">
                        <div style="font-size: 64px; font-weight: 700; color: ${categoryColor}; margin-bottom: 15px;">${coherenceScore}%</div>
                        <div style="font-size: 18px; color: #64748b; font-weight: 600; margin-bottom: 20px;">Índice de Coerência</div>
                        <div style="width: 100%; max-width: 400px; height: 12px; background: #e2e8f0; border-radius: 10px; margin: 0 auto; overflow: hidden;">
                            <div style="width: ${coherenceScore}%; height: 100%; background: ${categoryColor}; transition: width 1s ease;"></div>
                        </div>
                    </div>
                    
                    <div style="background: ${categoryColor}20; border-left: 4px solid ${categoryColor}; padding: 20px; border-radius: 10px; margin-bottom: 25px;">
                        <div style="font-weight: 700; color: ${categoryColor}; font-size: 18px; margin-bottom: 10px;">📋 Classificação: ${category}</div>
                        <div style="color: #4a5568; line-height: 1.6;">${recommendation}</div>
                    </div>
                    
                    <div style="background: white; padding: 20px; border-radius: 15px; margin-bottom: 20px;">
                        <h4 style="color: #2d3748; margin-bottom: 15px; font-size: 18px;">🔍 Análise Detalhada:</h4>
                        <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px;">
                            <div style="background: #f7fafc; padding: 15px; border-radius: 10px;">
                                <div style="color: #64748b; font-size: 13px; font-weight: 600; margin-bottom: 5px;">Total de frases</div>
                                <div style="color: #2d3748; font-size: 28px; font-weight: 700;">${sentences.length}</div>
                            </div>
                            <div style="background: #f7fafc; padding: 15px; border-radius: 10px;">
                                <div style="color: #64748b; font-size: 13px; font-weight: 600; margin-bottom: 5px;">Total de palavras</div>
                                <div style="color: #2d3748; font-size: 28px; font-weight: 700;">${words.length}</div>
                            </div>
                            <div style="background: #f7fafc; padding: 15px; border-radius: 10px;">
                                <div style="color: #64748b; font-size: 13px; font-weight: 600; margin-bottom: 5px;">Palavras/frase</div>
                                <div style="color: #2d3748; font-size: 28px; font-weight: 700;">${(words.length / sentences.length).toFixed(1)}</div>
                            </div>
                        </div>
                    </div>
                    
                    ${issues.length > 0 ? `
                        <div style="background: white; padding: 20px; border-radius: 15px;">
                            <h4 style="color: #2d3748; margin-bottom: 15px; font-size: 18px;">⚠️ Pontos de Melhoria:</h4>
                            <div style="display: flex; flex-direction: column; gap: 10px;">
                                ${issues.map(issue => `
                                    <div style="background: #fef3c7; border-left: 3px solid #f59e0b; padding: 12px; border-radius: 8px; color: #92400e; font-size: 14px;">
                                        ${issue}
                                    </div>
                                `).join('')}
                            </div>
                        </div>
                    ` : `
                        <div style="background: #d1fae5; border-left: 4px solid #10b981; padding: 20px; border-radius: 10px; text-align: center;">
                            <span style="font-size: 32px; display: block; margin-bottom: 10px;">✅</span>
                            <span style="color: #065f46; font-weight: 600;">Nenhum problema de coerência detectado!</span>
                        </div>
                    `}
                </div>
            `;
        }

        // Sistema de notificações toast
        function showToast(message, type = 'info') {
            const colors = {
                success: '#10b981',
                error: '#ef4444',
                info: '#3b82f6',
                warning: '#f59e0b'
            };
            
            const toast = document.createElement('div');
            toast.style.cssText = `
                position: fixed;
                top: 20px;
                right: 20px;
                background: ${colors[type]};
                color: white;
                padding: 16px 24px;
                border-radius: 12px;
                font-weight: 600;
                z-index: 10000;
                animation: slideIn 0.3s ease;
                box-shadow: 0 10px 25px rgba(0,0,0,0.2);
                max-width: 400px;
            `;
            toast.textContent = message;
            document.body.appendChild(toast);
            
            setTimeout(() => {
                toast.style.animation = 'fadeOut 0.3s ease';
                setTimeout(() => toast.remove(), 300);
            }, 3000);
        }

        function displayCorrections() {
            const correctedTextBox = document.getElementById('correctedTextBox');
            const correctedTextContent = document.getElementById('correctedTextContent');
            
            // Restaurar label das estatísticas
            document.querySelector('.stat:nth-child(3) .stat-label').textContent = 'Correções Feitas';
            
            // Mostrar caixa de texto corrigido
            correctedTextBox.style.display = 'block';
            correctedTextContent.textContent = textInput.value;
            
            if (foundCorrections.length === 0) {
                correctionsDisplay.innerHTML = `
                    <div class="no-errors">
                        <span style="font-size: 32px; display: block; margin-bottom: 10px;">✅</span>
                        Parabéns! Nenhum erro encontrado!
                    </div>
                `;
            } else {
                let html = '<h3>📝 Correções Realizadas:</h3>';
                correctionsDisplay.innerHTML = html;
                
                foundCorrections.forEach((item, index) => {
                    setTimeout(() => {
                        const correctionItem = document.createElement('div');
                        correctionItem.className = 'correction-item';
                        
                        // Adicionar categoria se existir
                        const categoryBadge = item.type ? `<span style="background: #8b5cf6; color: white; padding: 3px 8px; border-radius: 5px; font-size: 11px; margin-right: 8px;">${item.type}</span>` : '';
                        
                        correctionItem.innerHTML = `
                            ${categoryBadge}
                            <span class="correction-wrong">${item.wrong}</span>
                            <span class="correction-arrow">→</span>
                            <span class="correction-right">${item.correct}</span>
                        `;
                        correctionsDisplay.appendChild(correctionItem);
                    }, index * 100);
                });
            }
        }

        // Botão de copiar
        document.getElementById('copyBtn').addEventListener('click', () => {
            const correctedText = document.getElementById('correctedTextContent').textContent;
            const copySuccess = document.getElementById('copySuccess');
            
            navigator.clipboard.writeText(correctedText).then(() => {
                copySuccess.style.display = 'block';
                setTimeout(() => {
                    copySuccess.style.display = 'none';
                }, 3000);
            }).catch(err => {
                alert('Erro ao copiar texto. Tente selecionar e copiar manualmente.');
            });
        });

        // Menu mobile
        document.getElementById('mobileMenu').addEventListener('click', () => {
            const navLinks = document.querySelector('.nav-links');
            navLinks.style.display = navLinks.style.display === 'flex' ? 'none' : 'flex';
        });

        // Smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                }
            });
        });

        // ==================== SISTEMA ADMIN ====================
        
        // Configurações iniciais (salvos no localStorage)
        const STORAGE_KEY = 'corretorAdminData';
        
        // Senha padrão inicial: "admin123" (você deve trocar!)
        const defaultSettings = {
            password: 'admin123',
            playStoreLink: '',
            apkLink: '',
            contactEmail: 'contato@corretorapp.com'
        };

        // Carregar configurações salvas
        function loadSettings() {
            const saved = localStorage.getItem(STORAGE_KEY);
            return saved ? JSON.parse(saved) : defaultSettings;
        }

        // Salvar configurações
        function saveSettings(settings) {
            localStorage.setItem(STORAGE_KEY, JSON.stringify(settings));
            applySettings(settings);
        }

        // Aplicar configurações aos links do site
        function applySettings(settings) {
            // Atualizar botões de download
            const playStoreBtn = document.querySelector('.download-links a:first-child');
            const apkBtn = document.querySelector('.download-links a:last-child');
            
            if (settings.playStoreLink && playStoreBtn) {
                playStoreBtn.href = settings.playStoreLink;
            }
            if (settings.apkLink && apkBtn) {
                apkBtn.href = settings.apkLink;
            }

            // Atualizar links de email
            document.querySelectorAll('a[href^="mailto:"]').forEach(link => {
                link.href = `mailto:${settings.contactEmail}`;
            });

            // Atualizar também os botões do Hero
            const heroBtns = document.querySelectorAll('.hero .cta-buttons a');
            if (heroBtns[0] && settings.playStoreLink) {
                heroBtns[0].href = settings.playStoreLink;
            }
        }

        // Aplicar configurações ao carregar página
        let currentSettings = loadSettings();
        applySettings(currentSettings);

        // ===== GERENCIADOR DE PALAVRAS PERSONALIZADAS =====
        const CUSTOM_WORDS_KEY = 'corretorCustomWords';
        
        // Carregar palavras personalizadas
        function loadCustomWords() {
            const saved = localStorage.getItem(CUSTOM_WORDS_KEY);
            return saved ? JSON.parse(saved) : {};
        }

        // Salvar palavras personalizadas
        function saveCustomWords(customWords) {
            localStorage.setItem(CUSTOM_WORDS_KEY, JSON.stringify(customWords));
            // Atualizar o dicionário de correções
            Object.assign(corrections, customWords);
        }

        // Carregar e aplicar palavras personalizadas ao iniciar
        let customWords = loadCustomWords();
        Object.assign(corrections, customWords);

        // ===== MODAL DE LOGIN =====
        const adminLink = document.getElementById('adminLink');
        const adminModal = document.getElementById('adminModal');
        const adminPanel = document.getElementById('adminPanel');
        const loginForm = document.getElementById('adminLoginForm');
        const loginError = document.getElementById('loginError');
        const closeModalBtn = document.getElementById('closeModalBtn');
        const closeAdminBtn = document.getElementById('closeAdminBtn');

        // Abrir modal de login
        adminLink.addEventListener('click', (e) => {
            e.preventDefault();
            adminModal.style.display = 'flex';
            document.getElementById('adminPassword').focus();
        });

        // Fechar modal
        closeModalBtn.addEventListener('click', () => {
            adminModal.style.display = 'none';
            loginError.style.display = 'none';
            document.getElementById('adminPassword').value = '';
        });

        // Login
        loginForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const password = document.getElementById('adminPassword').value;

            if (password === currentSettings.password) {
                adminModal.style.display = 'none';
                adminPanel.style.display = 'block';
                loadAdminData();
                loginError.style.display = 'none';
                document.getElementById('adminPassword').value = '';
            } else {
                loginError.textContent = '❌ Senha incorreta!';
                loginError.style.display = 'block';
            }
        });

        // Fechar painel admin
        closeAdminBtn.addEventListener('click', () => {
            adminPanel.style.display = 'none';
        });

        // Carregar dados no painel admin
        function loadAdminData() {
            document.getElementById('playStoreLink').value = currentSettings.playStoreLink || '';
            document.getElementById('apkLink').value = currentSettings.apkLink || '';
            document.getElementById('contactEmail').value = currentSettings.contactEmail || '';
            renderCustomWords();
        }

        // Mostrar mensagem de sucesso
        function showSuccess(message) {
            const successMsg = document.getElementById('successMsg');
            successMsg.textContent = '✅ ' + message;
            successMsg.style.display = 'block';
            setTimeout(() => {
                successMsg.style.display = 'none';
            }, 3000);
        }

        // ===== BOTÕES DO PAINEL =====

        // Salvar link Play Store
        document.getElementById('savePlayStore').addEventListener('click', () => {
            currentSettings.playStoreLink = document.getElementById('playStoreLink').value;
            saveSettings(currentSettings);
            showSuccess('Link da Play Store salvo com sucesso!');
        });

        // Salvar link APK
        document.getElementById('saveApk').addEventListener('click', () => {
            currentSettings.apkLink = document.getElementById('apkLink').value;
            saveSettings(currentSettings);
            showSuccess('Link do APK salvo com sucesso!');
        });

        // Salvar email
        document.getElementById('saveEmail').addEventListener('click', () => {
            currentSettings.contactEmail = document.getElementById('contactEmail').value;
            saveSettings(currentSettings);
            showSuccess('Email de contato salvo com sucesso!');
        });

        // Trocar senha
        document.getElementById('changePassword').addEventListener('click', () => {
            const newPassword = document.getElementById('newPassword').value;
            
            if (!newPassword || newPassword.length < 6) {
                alert('A senha deve ter pelo menos 6 caracteres!');
                return;
            }

            currentSettings.password = newPassword;
            saveSettings(currentSettings);
            document.getElementById('newPassword').value = '';
            showSuccess('Senha alterada com sucesso! Anote sua nova senha!');
        });

        // ===== GERENCIAMENTO DE PALAVRAS PERSONALIZADAS =====

        // Renderizar lista de palavras personalizadas
        function renderCustomWords() {
            const customWordsList = document.getElementById('customWordsList');
            const customWordCount = document.getElementById('customWordCount');
            
            const words = Object.entries(customWords);
            customWordCount.textContent = words.length;
            
            if (words.length === 0) {
                customWordsList.innerHTML = '<p style="color: #64748b; text-align: center; padding: 20px;">Nenhuma palavra personalizada cadastrada ainda</p>';
                return;
            }
            
            customWordsList.innerHTML = words.map(([wrong, correct]) => `
                <div style="display: flex; justify-content: space-between; align-items: center; padding: 12px; background: #f1f5f9; border-radius: 8px; border-left: 3px solid #3b82f6;">
                    <div>
                        <span style="color: #dc2626; font-weight: 600; text-decoration: line-through;">${wrong}</span>
                        <span style="margin: 0 10px; color: #059669;">→</span>
                        <span style="color: #059669; font-weight: 600;">${correct}</span>
                    </div>
                    <button onclick="removeCustomWord('${wrong}')" style="padding: 6px 12px; background: #ef4444; color: white; border: none; border-radius: 6px; cursor: pointer; font-size: 12px; font-weight: 600; transition: all 0.2s;" onmouseover="this.style.background='#dc2626'" onmouseout="this.style.background='#ef4444'">🗑️ Remover</button>
                </div>
            `).join('');
        }

        // Adicionar palavra personalizada
        document.getElementById('addCustomWord').addEventListener('click', () => {
            const wrongWord = document.getElementById('wrongWord').value.trim().toLowerCase();
            const correctWord = document.getElementById('correctWord').value.trim().toLowerCase();
            
            if (!wrongWord || !correctWord) {
                alert('Por favor, preencha ambos os campos!');
                return;
            }
            
            if (wrongWord === correctWord) {
                alert('As palavras não podem ser iguais!');
                return;
            }
            
            // Adicionar ao dicionário personalizado
            customWords[wrongWord] = correctWord;
            saveCustomWords(customWords);
            
            // Limpar campos
            document.getElementById('wrongWord').value = '';
            document.getElementById('correctWord').value = '';
            
            // Atualizar lista
            renderCustomWords();
            showSuccess(`Palavra "${wrongWord}" → "${correctWord}" adicionada com sucesso!`);
        });

        // Remover palavra personalizada (função global para onclick)
        window.removeCustomWord = function(wrongWord) {
            if (confirm(`Tem certeza que deseja remover a correção "${wrongWord}"?`)) {
                delete customWords[wrongWord];
                delete corrections[wrongWord];
                saveCustomWords(customWords);
                renderCustomWords();
                showSuccess(`Palavra "${wrongWord}" removida com sucesso!`);
            }
        };

        // Fechar modal ao clicar fora
        adminModal.addEventListener('click', (e) => {
            if (e.target === adminModal) {
                adminModal.style.display = 'none';
            }
        });

        // ===== CONTROLES DO MODAL PREMIUM =====
        const premiumModal = document.getElementById('premiumModal');
        const upgradBtn = document.getElementById('upgradBtn');
        const closePremiumModal = document.getElementById('closePremiumModal');
        const activatePremiumBtn = document.getElementById('activatePremiumBtn');

        // Abrir modal premium
        upgradBtn.addEventListener('click', () => {
            premiumModal.style.display = 'flex';
        });

        // Fechar modal premium
        closePremiumModal.addEventListener('click', () => {
            premiumModal.style.display = 'none';
        });

        // Fechar ao clicar fora
        premiumModal.addEventListener('click', (e) => {
            if (e.target === premiumModal) {
                premiumModal.style.display = 'none';
            }
        });

        // Ativar premium (simulação)
        activatePremiumBtn.addEventListener('click', () => {
            // Simular ativação
            isPremiumUser = true;
            localStorage.setItem('isPremium', 'true');
            updatePlanIndicator();
            premiumModal.style.display = 'none';
            
            // Confete de celebração
            showToast('🎉 Premium ativado com sucesso! Aproveite todos os recursos!', 'success');
            
            // Simular confete
            for (let i = 0; i < 50; i++) {
                setTimeout(() => {
                    const confetti = document.createElement('div');
                    confetti.textContent = ['🎉', '⭐', '✨', '🎊', '💎'][Math.floor(Math.random() * 5)];
                    confetti.style.cssText = `
                        position: fixed;
                        top: -50px;
                        left: ${Math.random() * 100}%;
                        font-size: 24px;
                        z-index: 10001;
                        animation: fall ${2 + Math.random() * 2}s linear;
                        pointer-events: none;
                    `;
                    document.body.appendChild(confetti);
                    setTimeout(() => confetti.remove(), 4000);
                }, i * 50);
            }
        });

        // Adicionar animação de queda no CSS
        const style = document.createElement('style');
        style.textContent = `
            @keyframes fall {
                to {
                    transform: translateY(100vh) rotate(360deg);
                    opacity: 0;
                }
            }
            @keyframes fadeOut {
                to {
                    opacity: 0;
                    transform: translateY(-10px);
                }
            }
        `;
        document.head.appendChild(style);
    </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9a87fec6a198e2ae',t:'MTc2NDgxNjYxNS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
