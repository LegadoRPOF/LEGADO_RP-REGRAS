<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Regras da Cidade - LEGADO_RP</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        :root {
            --dark: #0a0a0a;
            --darker: #050505;
            --accent: #006ab0;
            --accent-dark: #13a8ec;
            --accent-light: #4fc3f7;
            --gray: #888888;
            --light-gray: #aaaaaa;
            --border: rgba(255, 255, 255, 0.1);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', sans-serif;
        }
        
        body {
            background-color: var(--dark);
            color: white;
            line-height: 1.6;
            overflow-x: hidden;
        }
        
        header {
            background-color: rgba(0, 0, 0, 0.7);
            backdrop-filter: blur(10px);
            position: fixed;
            width: 100%;
            z-index: 1000;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid var(--border);
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        
        .logo img {
            height: 50px;
        }
        
        .logo h1 {
            font-size: 1.8rem;
            font-weight: 600;
            letter-spacing: 2px;
        }
        
        .logo span {
            color: var(--accent);
        }
        
        nav ul {
            display: flex;
            list-style: none;
            gap: 2rem;
        }
        
        nav a {
            color: white;
            text-decoration: none;
            font-size: 1.1rem;
            font-weight: 500;
            letter-spacing: 1px;
            text-transform: uppercase;
            transition: color 0.3s;
            position: relative;
        }
        
        nav a:hover {
            color: var(--accent);
        }
        
        nav a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -5px;
            left: 0;
            background-color: var(--accent);
            transition: width 0.3s;
        }
        
        nav a:hover::after {
            width: 100%;
        }
        
        .connect-btn {
            background: linear-gradient(90deg, var(--accent), var(--accent-dark));
            color: white;
            border: none;
            padding: 0.7rem 1.5rem;
            font-size: 1rem;
            font-weight: 600;
            letter-spacing: 1px;
            border-radius: 4px;
            cursor: pointer;
            text-transform: uppercase;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .connect-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 106, 176, 0.3);
        }
        
        .hero {
            height: 60vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            position: relative;
            padding: 0 1rem;
            overflow: hidden;
        }
        
        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('https://images.unsplash.com/photo-1591822059941-4d5cb3a4b3a9?ixlib=rb-1.2.1&auto=format&fit=crop&w=1950&q=80');
            background-size: cover;
            background-position: center;
            filter: brightness(0.3);
            z-index: -1;
        }
        
        .hero h2 {
            font-size: 4rem;
            font-weight: 700;
            margin-bottom: 1.5rem;
            text-transform: uppercase;
            letter-spacing: 4px;
            text-shadow: 0 0 10px rgba(0, 0, 0, 0.7);
        }
        
        .hero p {
            font-size: 1.3rem;
            max-width: 800px;
            margin-bottom: 2rem;
            color: var(--light-gray);
        }
        
        .server-stats {
            display: flex;
            gap: 2rem;
            background-color: rgba(0, 0, 0, 0.7);
            padding: 1.5rem 3rem;
            border-radius: 8px;
            border: 1px solid var(--border);
            backdrop-filter: blur(10px);
        }
        
        .stat {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .stat-value {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--accent);
            text-shadow: 0 0 16px var(--accent-light);
        }
        
        .stat-label {
            font-size: 1rem;
            color: var(--light-gray);
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .rules {
            padding: 6rem 2rem;
            background-color: var(--darker);
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 4rem;
            position: relative;
        }
        
        .section-title h2 {
            font-size: 2.5rem;
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            width: 80px;
            height: 3px;
            background-color: var(--accent);
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
        }
        
        .rules-container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .rules-tabs {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            margin-bottom: 2rem;
            justify-content: center;
        }
        
        .rules-tab {
            background-color: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 1rem 2rem;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .rules-tab.active {
            background-color: var(--accent);
            border-color: var(--accent);
        }
        
        .rules-tab:hover {
            background-color: rgba(0, 106, 176, 0.3);
        }
        
        .rules-content {
            display: none;
        }
        
        .rules-content.active {
            display: block;
        }
        
        .rule-card {
            background-color: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 2rem;
            margin-bottom: 1.5rem;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .rule-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 7px 20px rgba(0, 106, 176, 0.3);
        }
        
        .rule-card h3 {
            font-size: 1.5rem;
            color: var(--accent);
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        
        .rule-card ul {
            list-style: none;
        }
        
        .rule-card li {
            padding: 0.5rem 0;
            border-bottom: 1px solid var(--border);
            display: flex;
        }
        
        .rule-card li:last-child {
            border-bottom: none;
        }
        
        .rule-card li::before {
            content: '•';
            color: var(--accent);
            margin-right: 0.5rem;
            font-weight: bold;
        }
        
        .penalty {
            display: inline-block;
            background-color: rgba(209, 44, 44, 0.2);
            color: #ff4d4d;
            padding: 0.2rem 0.5rem;
            border-radius: 4px;
            font-size: 0.8rem;
            margin-left: 0.5rem;
        }
        
        .rules-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }
        
        .info-section {
            padding: 6rem 2rem;
            background-color: var(--dark);
        }
        
        .info-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .info-card {
            background-color: rgba(255, 255, 255, 0.05);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 2rem;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .info-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 7px 20px rgba(0, 106, 176, 0.3);
        }
        
        .info-card h3 {
            font-size: 1.5rem;
            color: var(--accent);
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        
        .info-card p {
            color: var(--light-gray);
            margin-bottom: 1rem;
        }
        
        .info-card ul {
            list-style: none;
            color: var(--light-gray);
        }
        
        .info-card li {
            padding: 0.3rem 0;
            display: flex;
        }
        
        .info-card li::before {
            content: '•';
            color: var(--accent);
            margin-right: 0.5rem;
            font-weight: bold;
        }
        
        .join {
            padding: 6rem 2rem;
            text-align: center;
            background-color: var(--darker);
            position: relative;
            overflow: hidden;
        }
        
        .join::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('https://images.unsplash.com/photo-1591822059941-4d5cb3a4b3a9?ixlib=rb-1.2.1&auto=format&fit=crop&w=1950&q=80');
            background-size: cover;
            background-position: center;
            filter: brightness(0.1);
            z-index: 0;
        }
        
        .join-content {
            position: relative;
            z-index: 1;
            max-width: 800px;
            margin: 0 auto;
        }
        
        .join h2 {
            font-size: 3rem;
            margin-bottom: 1.5rem;
            text-transform: uppercase;
            letter-spacing: 3px;
        }
        
        .join p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            color: var(--light-gray);
        }
        
        .join-buttons {
            display: flex;
            justify-content: center;
            gap: 1rem;
        }
        
        .discord-btn {
            background-color: #5865F2;
            color: white;
            border: none;
            padding: 0.7rem 1.5rem;
            font-size: 1rem;
            font-weight: 600;
            letter-spacing: 1px;
            border-radius: 4px;
            cursor: pointer;
            text-transform: uppercase;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .discord-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(88, 101, 242, 0.3);
        }
        
        footer {
            background-color: var(--darker);
            padding: 3rem 2rem;
            border-top: 1px solid var(--border);
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .footer-logo {
            display: flex;
            align-items: center;
            gap: 1rem;
        }
        
        .footer-logo img {
            height: 40px;
        }
        
        .footer-logo h3 {
            font-size: 1.5rem;
            font-weight: 600;
            letter-spacing: 2px;
        }
        
        .footer-links {
            display: flex;
            gap: 1.5rem;
        }
        
        .footer-links a {
            color: var(--light-gray);
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-links a:hover {
            color: var(--accent);
        }
        
        .copyright {
            text-align: center;
            margin-top: 2rem;
            color: var(--gray);
            font-size: 0.9rem;
        }
        
        @media (max-width: 768px) {
            header {
                padding: 1rem;
            }
            
            .logo h1 {
                font-size: 1.5rem;
            }
            
            nav ul {
                display: none;
            }
            
            .hero h2 {
                font-size: 2.5rem;
            }
            
            .hero p {
                font-size: 1.1rem;
            }
            
            .server-stats {
                flex-direction: column;
                gap: 1rem;
                padding: 1.5rem;
            }
            
            .footer-content {
                flex-direction: column;
                gap: 2rem;
                text-align: center;
            }
            
            .footer-logo {
                justify-content: center;
            }
            
            .rules-tabs {
                flex-direction: column;
            }
            
            .join-buttons {
                flex-direction: column;
            }
        }

        .city-decoration {
            position: absolute;
            top: 50%;
            left: -50px;
            transform: translateY(-50%);
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background: rgba(0, 106, 176, 0.1);
            z-index: -1;
        }
        
        .city-decoration::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 80px;
            height: 80px;
            border-radius: 50%;
            border: 2px dashed var(--accent);
        }
        
        .digital-effect {
            position: absolute;
            bottom: -50px;
            right: -50px;
            width: 200px;
            height: 200px;
            background: 
                linear-gradient(0deg, rgba(0, 106, 176, 0.05) 25%, transparent 25%) 0 0,
                linear-gradient(0deg, rgba(0, 106, 176, 0.05) 25%, transparent 25%) 10px 10px,
                linear-gradient(0deg, transparent 75%, rgba(0, 106, 176, 0.05) 75%) 0 0,
                linear-gradient(0deg, transparent 75%, rgba(0, 106, 176, 0.05) 75%) 10px 10px;
            background-size: 20px 20px;
            z-index: -1;
        }
    </style>
</head>
<body>
    <header>
        <div class="logo">
            <img src="https://cdn-icons-png.flaticon.com/512/906/906194.png" alt="Logo LEGADO_RP">
            <h1>LEGADO<span>_RP</span></h1>
        </div>
        <nav>
            <ul>
                <li><a href="#rules">Regras</a></li>
                <li><a href="#info">Informações</a></li>
                <li><a href="#join">Entrar</a></li>
            </ul>
        </nav>
        <button class="connect-btn" onclick="connectToServer()">Conectar agora</button>
    </header>
    
    <section class="hero">
        <h2>Regras da <a style="color: #13a8ec;">Cidade</a></h2>
        <p>Conheça as regras e diretrizes do servidor LEGADO_RP para uma experiência de roleplay imersiva e justa para todos os jogadores.</p>
        <div class="server-stats">
            <div class="stat">
                <div class="stat-value">128</div>
                <div class="stat-label">Slots</div>
            </div>
            <div class="stat">
                <div class="stat-value">24/7</div>
                <div class="stat-label">Online</div>
            </div>
            <div class="stat">
                <div class="stat-value">5</div>
                <div class="stat-label">Fações</div>
            </div>
            <div class="stat">
                <div class="stat-value">30+</div>
                <div class="stat-label">Empregos</div>
            </div>
        </div>
    </section>
    
    <section class="rules" id="rules">
        <div class="section-title">
            <h2>Regras da Cidade</h2>
        </div>
        <div class="rules-container">
            <div class="rules-tabs">
                <div class="rules-tab active" data-tab="geral">Regras Gerais</div>
                <div class="rules-tab" data-tab="roleplay">Regras de Roleplay</div>
                <div class="rules-tab" data-tab="policia">Regras Policiais</div>
                <div class="rules-tab" data-tab="faccao">Regras de Facções</div>
                <div class="rules-tab" data-tab="veiculos">Regras de Veículos</div>
            </div>
            
            <div class="rules-content active" id="geral-content">
                <div class="rule-card">
                    <h3><i class="fas fa-exclamation-circle"></i> Regras Gerais</h3>
                    <ul>
                        <li>Respeitar todos os jogadores, independente de patente ou função <span class="penalty">Banimento</span></li>
                        <li>Proibido qualquer forma de discriminação ou preconceito <span class="penalty">Banimento permanente</span></li>
                        <li>Proibido divulgação de links ou conteúdos inadequados <span class="penalty">Banimento 7 dias</span></li>
                        <li>Não é permitido metagaming (uso de informações OOC em IC) <span class="penalty">Banimento 3 dias</span></li>
                        <li>Proibido exploração de bugs ou glitches <span class="penalty">Banimento 14 dias</span></li>
                    </ul>
                </div>
                
                <div class="rule-card">
                    <h3><i class="fas fa-microphone"></i> Comunicação por Voz</h3>
                    <ul>
                        <li>Use o modo de voz adequado para a situação (gritar, sussurrar, normal)</li>
                        <li>Proibido uso de modificadores de voz não realistas <span class="penalty">Banimento 1 dia</span></li>
                        <li>Evite ruídos de fundo excessivos no microfone <span class="penalty">Advertência</span></li>
                        <li>Use o rádio apenas para comunicações IC (in character) <span class="penalty">Advertência</span></li>
                    </ul>
                </div>
            </div>
            
            <div class="rules-content" id="roleplay-content">
                <div class="rule-card">
                    <h3><i class="fas fa-theater-masks"></i> Regras de Roleplay</h3>
                    <ul>
                        <li>Mantenha sempre o roleplay, mesmo em situações adversas <span class="penalty">Banimento 3 dias</span></li>
                        <li>Proibido RDM (Random Deathmatch - matar sem motivo) <span class="penalty">Banimento 7 dias</span></li>
                        <li>Proibido VDM (Vehicle Deathmatch - atropelar sem motivo) <span class="penalty">Banimento 7 dias</span></li>
                        <li>Não cometa crimes sem roleplay adequado <span class="penalty">Banimento 3 dias</span></li>
                        <li>Respeite a situação de NEW LIFE (após ser revivido) <span class="penalty">Banimento 5 dias</span></li>
                    </ul>
                </div>
                
                <div class="rule-card">
                    <h3><i class="fas fa-fist-raised"></i> Situações de Combate</h3>
                    <ul>
                        <li>Initiation obrigatória antes de qualquer ação hostil <span class="penalty">Banimento 3 dias</span></li>
                        <li>Proibido combat logging (sair durante combate) <span class="penalty">Banimento 7 dias</span></li>
                        <li>Respeite a regra de NLR (No Life Rule) <span class="penalty">Banimento 3 dias</span></li>
                        <li>Não reutilize informações após morte <span class="penalty">Banimento 3 dias</span></li>
                    </ul>
                </div>
            </div>
            
            <div class="rules-content" id="policia-content">
                <div class="rule-card">
                    <h3><i class="fas fa-shield-alt"></i> Regras Policiais</h3>
                    <ul>
                        <li>Policiais devem sempre seguir a lei e procedimentos <span class="penalty">Rebaixamento</span></li>
                        <li>Uso proporcional da força em todas as situações <span class="penalty">Suspensão</span></li>
                        <li>Proibido abuso de autoridade ou corrupção excessiva <span class="penalty">Demissão</span></li>
                        <li>Respeite os direitos dos civis durante abordagens <span class="penalty">Advertência</span></li>
                    </ul>
                </div>
                
                <div class="rule-card">
                    <h3><i class="fas fa-gavel"></i> Sistema Judicial</h3>
                    <ul>
                        <li>Julgamentos devem ser realizados com base em evidências</li>
                        <li>Procuradores e defensores devem atuar com profissionalismo</li>
                        <li>Juízes devem ser imparciais em suas decisões</li>
                        <li>Testemunhas devem falar apenas a verdade</li>
                    </ul>
                </div>
            </div>
            
            <!-- Conteúdo adicional para outras abas -->
        </div>
    </section>
    
    <section class="info-section" id="info">
        <div class="section-title">
            <h2>Informações Importantes</h2>
        </div>
        <div class="info-cards">
            <div class="info-card">
                <h3><i class="fas fa-exclamation-triangle"></i> Sistema de Punções</h3>
                <p>As infrações às regras resultam em punições progressivas:</p>
                <ul>
                    <li>1ª infração: Advertência</li>
                    <li>2ª infração: Banimento de 1-3 dias</li>
                    <li>3ª infração: Banimento de 7-14 dias</li>
                    <li>Infrações graves: Banimento permanente</li>
                </ul>
            </div>
            
            <div class="info-card">
                <h3><i class="fas fa-headset"></i> Suporte</h3>
                <p>Para reportar jogadores ou problemas:</p>
                <ul>
                    <li>Use o sistema de tickets no Discord</li>
                    <li>Forneça sempre evidências (vídeos, prints)</li>
                    <li>Seja claro e objetivo em sua denúncia</li>
                    <li>Respeite os staff members</li>
                </ul>
            </div>
            
            <div class="info-card">
                <h3><i class="fas fa-id-card"></i> Whitelist</h3>
                <p>Para jogar no servidor é necessário:</p>
                <ul>
                    <li>Ter mais de 16 anos</li>
                    <li>Preencher formulário de whitelist</li>
                    <li>Participar de entrevista com staff</li>
                    <li>Passar pelo treinamento inicial</li>
                </ul>
            </div>
        </div>
    </section>
    
    <section class="join" id="join">
        <div class="join-content">
            <h2>Junte-se à Cidade</h2>
            <p>Pronto para fazer parte da comunidade LEGADO_RP? Conecte-se ao nosso servidor e comece sua jornada na cidade!</p>
            <div class="join-buttons">
                <button class="connect-btn" onclick="connectToServer()">Conectar ao servidor</button>
                <button class="discord-btn" onclick="joinDiscord()"><i class="fab fa-discord"></i> Entrar no Discord</button>
            </div>
        </div>
        <div class="city-decoration"></div>
        <div class="digital-effect"></div>
    </section>
    
    <footer>
        <div class="footer-content">
            <div class="footer-logo">
                <img src="https://cdn-icons-png.flaticon.com/512/906/906194.png" alt="Logo LEGADO_RP">
                <h3>LEGADO<span>_RP</span></h3>
            </div>
            <div class="footer-links">
                <a href="#">Suporte</a>
                <a href="#">Doação</a>
                <a href="#">Contato</a>
            </div>
        </div>
        <div class="copyright">
            <p>© 2025 LEGADO_RP - Servidor FiveM de Roleplay. Todos os direitos reservados. Não afiliado à Rockstar Games ou Take-Two Interactive.</p>
        </div>
    </footer>

    <script>
        // Script para as abas de regras
        document.addEventListener('DOMContentLoaded', function() {
            const tabs = document.querySelectorAll('.rules-tab');
            const contents = document.querySelectorAll('.rules-content');
            
            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    // Remove a classe active de todas as tabs e contents
                    tabs.forEach(t => t.classList.remove('active'));
                    contents.forEach(c => c.classList.remove('active'));
                    
                    // Adiciona a classe active à tab clicada
                    tab.classList.add('active');
                    
                    // Mostra o content correspondente
                    const tabId = tab.getAttribute('data-tab');
                    document.getElementById(`${tabId}-content`).classList.add('active');
                });
            });
        });

        // Função para conectar ao servidor FiveM
        function connectToServer() {
            // Substitua pelo link de conexão do seu servidor FiveM
            window.location.href = 'fivem://connect/seu-ip-do-servidor';
        }

        // Função para entrar no Discord
        function joinDiscord() {
            // Substitua pelo link de convite do seu Discord
            window.open('https://discord.gg/seu-link-de-convite', '_blank');
        }

        // Botão de conectar no header
        const connectButtons = document.querySelectorAll('.connect-btn');
        connectButtons.forEach(button => {
            button.addEventListener('click', connectToServer);
        });
    </script>
</body>
</html>
