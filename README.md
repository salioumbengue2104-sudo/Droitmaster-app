# index.html
Application mobile pour les étudiants 
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DroitMaster - App Mobile</title>
    <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>⚖️</text></svg>">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        :root {
            --primary: #4361ee;
            --secondary: #3a0ca3;
            --accent: #7209b7;
            --success: #4cc9f0;
            --warning: #f72585;
            --light: #f8f9fa;
            --dark: #212529;
            --text: #2b2d42;
            --card-bg: #ffffff;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: var(--text);
            line-height: 1.6;
            min-height: 100vh;
        }
        
        .app-container {
            max-width: 400px;
            margin: 0 auto;
            background: white;
            min-height: 100vh;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
            position: relative;
        }
        
        .app-header {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 20px 15px;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: var(--shadow);
        }
        
        .app-header h1 {
            font-size: 1.4rem;
            font-weight: 700;
            margin-bottom: 5px;
        }
        
        .tab-navigation {
            display: flex;
            background: var(--light);
            border-bottom: 1px solid #e9ecef;
            position: sticky;
            top: 110px;
            z-index: 90;
        }
        
        .tab-btn {
            flex: 1;
            padding: 15px 10px;
            text-align: center;
            background: none;
            border: none;
            font-size: 0.8rem;
            font-weight: 600;
            color: var(--text);
            cursor: pointer;
            transition: all 0.3s ease;
            border-bottom: 3px solid transparent;
        }
        
        .tab-btn.active {
            color: var(--primary);
            border-bottom-color: var(--primary);
            background: white;
        }
        
        .tab-btn i {
            display: block;
            font-size: 1.2rem;
            margin-bottom: 5px;
        }
        
        .tab-content {
            display: none;
            padding: 20px 15px;
            animation: fadeIn 0.3s ease;
        }
        
        .tab-content.active {
            display: block;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .card {
            background: var(--card-bg);
            border-radius: 15px;
            padding: 20px;
            margin-bottom: 15px;
            box-shadow: var(--shadow);
            border: 1px solid #f1f3f4;
            transition: transform 0.2s ease;
        }
        
        .card:hover {
            transform: translateY(-2px);
        }
        
        .card h3 {
            color: var(--primary);
            margin-bottom: 10px;
            font-size: 1.1rem;
        }
        
        .btn {
            display: inline-block;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 25px;
            font-size: 0.9rem;
            font-weight: 600;
            text-decoration: none;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: var(--shadow);
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }
        
        .btn-block {
            display: block;
            width: 100%;
        }
        
        .menu-list {
            list-style: none;
        }
        
        .menu-item {
            display: flex;
            align-items: center;
            padding: 15px;
            background: white;
            border-radius: 10px;
            margin-bottom: 10px;
            box-shadow: var(--shadow);
            cursor: pointer;
            transition: all 0.3s ease;
            border-left: 4px solid var(--primary);
        }
        
        .menu-item:hover {
            transform: translateX(5px);
            background: #f8f9fa;
        }
        
        .menu-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.2rem;
            margin-right: 15px;
        }
        
        .chat-container {
            height: 400px;
            background: #f8f9fa;
            border-radius: 15px;
            padding: 15px;
            margin-bottom: 15px;
            overflow-y: auto;
            border: 1px solid #e9ecef;
        }
        
        .message {
            max-width: 80%;
            margin-bottom: 15px;
            padding: 12px 16px;
            border-radius: 18px;
            line-height: 1.4;
            animation: messageSlide 0.3s ease;
        }
        
        @keyframes messageSlide {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .user-message {
            background: linear-gradient(135deg, var(--primary), var(--secondary));
            color: white;
            margin-left: auto;
            border-bottom-right-radius: 5px;
        }
        
        .bot-message {
            background: white;
            border: 1px solid #e9ecef;
            border-bottom-left-radius: 5px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }
        
        .input-group {
            display: flex;
            gap: 10px;
            margin-top: 15px;
        }
        
        .chat-input {
            flex: 1;
            padding: 12px 15px;
            border: 2px solid #e9ecef;
            border-radius: 25px;
            font-size: 0.9rem;
            outline: none;
            transition: border-color 0.3s ease;
        }
        
        .chat-input:focus {
            border-color: var(--primary);
        }
        
        .progress-bar {
            background: #e9ecef;
            height: 8px;
            border-radius: 4px;
            margin: 10px 0;
            overflow: hidden;
        }
        
        .progress {
            height: 100%;
            background: linear-gradient(135deg, var(--success), #4cc9f0);
            border-radius: 4px;
            transition: width 0.5s ease;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
            margin: 15px 0;
        }
        
        .stat-card {
            background: white;
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            box-shadow: var(--shadow);
        }
        
        .stat-number {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 5px;
        }
        
        .qcm-option {
            background: white;
            padding: 15px;
            margin: 10px 0;
            border-radius: 10px;
            border: 2px solid #e9ecef;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .qcm-option:hover {
            border-color: var(--primary);
            background: #f8f9fa;
        }
        
        .qcm-option.selected {
            border-color: var(--success);
            background: #e8f5e8;
        }
        
        .badge {
            display: inline-block;
            padding: 4px 8px;
            background: var(--accent);
            color: white;
            border-radius: 12px;
            font-size: 0.7rem;
            font-weight: 600;
            margin-left: 10px;
        }
        
        @media (max-width: 480px) {
            .app-container {
                max-width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="app-container">
        <header class="app-header">
            <h1>⚖️ DroitMaster</h1>
            <p>Votre assistant juridique mobile</p>
        </header>

        <nav class="tab-navigation">
            <button class="tab-btn active" onclick="showTab('accueil')">
                <i>🏠</i> Accueil
            </button>
            <button class="tab-btn" onclick="showTab('cours')">
                <i>📚</i> Cours
            </button>
            <button class="tab-btn" onclick="showTab('chat')">
                <i>🤖</i> Assistant
            </button>
            <button class="tab-btn" onclick="showTab('qcm')">
                <i>📝</i> QCM
            </button>
            <button class="tab-btn" onclick="showTab('profil')">
                <i>👤</i> Profil
            </button>
        </nav>

        <main>
            <div id="accueil" class="tab-content active">
                <div class="card">
                    <h3>🎯 Votre Progression</h3>
                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-number">75%</div>
                            <div class="stat-label">L1 Complété</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number">45%</div>
                            <div class="stat-label">L2 Complété</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number">82%</div>
                            <div class="stat-label">QCM Réussis</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-number">12</div>
                            <div class="stat-label">Jours Actifs</div>
                        </div>
                    </div>
                </div>

                <div class="card">
                    <h3>🚀 Actions Rapides</h3>
                    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-top: 15px;">
                        <button class="btn" onclick="showTab('chat')">Poser une Question</button>
                        <button class="btn" onclick="startQuickQCM()">QCM Rapide</button>
                        <button class="btn" onclick="showTab('cours')">Voir les Cours</button>
                        <button class="btn" onclick="showTab('partage')">Partager</button>
                    </div>
                </div>

                <div class="card">
                    <h3>📅 Aujourd'hui</h3>
                    <ul class="menu-list">
                        <li class="menu-item" onclick="showTab('cours')">
                            <div class="menu-icon">📖</div>
                            <div class="menu-content">
                                <h4>Révision Droit Civil</h4>
                                <p>Contrats et obligations - 30min</p>
                            </div>
                            <div class="badge">À faire</div>
                        </li>
                        <li class="menu-item" onclick="showTab('qcm')">
                            <div class="menu-icon">✏️</div>
                            <div class="menu-content">
                                <h4>QCM Constitutionnel</h4>
                                <p>10 questions - Non commencé</p>
                            </div>
                            <div class="badge">Nouveau</div>
                        </li>
                    </ul>
                </div>
            </div>

            <div id="cours" class="tab-content">
                <div class="card">
                    <h3>🎓 Licence 1</h3>
                    <ul class="menu-list">
                        <li class="menu-item" onclick="openCourse('intro')">
                            <div class="menu-icon">📚</div>
                            <div class="menu-content">
                                <h4>Introduction au Droit</h4>
                                <p>Notions fondamentales • 5 chapitres</p>
                            </div>
                            <div class="progress-bar">
                                <div class="progress" style="width: 80%"></div>
                            </div>
                        </li>
                        <li class="menu-item" onclick="openCourse('civil')">
                            <div class="menu-icon">⚖️</div>
                            <div class="menu-content">
                                <h4>Droit Civil</h4>
                                <p>Personnes, biens, contrats • 8 chapitres</p>
                            </div>
                            <div class="progress-bar">
                                <div class="progress" style="width: 65%"></div>
                            </div>
                        </li>
                    </ul>
                </div>
            </div>

            <div id="chat" class="tab-content">
                <div class="card">
                    <h3>🤖 Assistant Juridique IA</h3>
                    <div class="chat-container" id="chatMobile">
                        <div class="message bot-message">
                            Bonjour ! Je suis votre assistant juridique. Posez-moi vos questions sur le droit civil, constitutionnel, administratif...
                        </div>
                    </div>
                    <div class="input-group">
                        <input type="text" class="chat-input" id="mobileInput" placeholder="Votre question..." onkeypress="if(event.key=='Enter') sendMobileMessage()">
                        <button class="btn" onclick="sendMobileMessage()">📤</button>
                    </div>
                </div>

                <div class="card">
                    <h3>💡 Questions Rapides</h3>
                    <div style="display: flex; flex-wrap: wrap; gap: 8px; margin-top: 10px;">
                        <button class="btn" onclick="askQuickQuestion('Qu\\'est-ce qu\\'un contrat ?')" style="font-size: 0.8rem; padding: 8px 12px;">Contrat</button>
                        <button class="btn" onclick="askQuickQuestion('Définition droit objectif')" style="font-size: 0.8rem; padding: 8px 12px;">Droit Objectif</button>
                        <button class="btn" onclick="askQuickQuestion('Sources du droit')" style="font-size: 0.8rem; padding: 8px 12px;">Sources</button>
                    </div>
                </div>
            </div>

            <div id="qcm" class="tab-content">
                <div class="card">
                    <h3>📝 Quiz du Jour</h3>
                    <div id="qcmMobile">
                        <p>Testez vos connaissances avec notre QCM interactif !</p>
                        <button class="btn btn-block" onclick="startMobileQCM()" style="margin-top: 15px;">
                            🚀 Commencer le Quiz
                        </button>
                    </div>
                </div>
            </div>

            <div id="profil" class="tab-content">
                <div class="card" style="text-align: center;">
                    <div style="width: 80px; height: 80px; background: linear-gradient(135deg, var(--primary), var(--secondary)); border-radius: 50%; margin: 0 auto 15px; display: flex; align-items: center; justify-content: center; color: white; font-size: 2rem;">
                        👨‍⚖️
                    </div>
                    <h3>Étudiant en Droit</h3>
                    <p style="color: #6c757d; margin-bottom: 15px;">Licence 2 • Université de Droit</p>
                </div>

                <div class="card">
                    <h3>📊 Progression Globale</h3>
                    <div style="margin: 15px 0;">
                        <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                            <span>Licence 1</span>
                            <span>75%</span>
                        </div>
                        <div class="progress-bar">
                            <div class="progress" style="width: 75%"></div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- NOUVEL ONGLET PARTAGE -->
            <div id="partage" class="tab-content">
                <div class="card">
                    <h3>📲 Partager DroitMaster</h3>
                    <p style="margin-bottom: 20px;">Partagez cette application avec vos camarades :</p>
                    
                    <button class="btn btn-block" onclick="shareApp()" style="margin-bottom: 15px; background: #25D366;">
                        💬 Partager sur WhatsApp
                    </button>
                    
                    <button class="btn btn-block" onclick="copyLink()" style="margin-bottom: 15px;">
                        📋 Copier le Lien
                    </button>
                    
                    <div class="input-group">
                        <input type="text" id="shareLink" class="chat-input" value="Chargement..." readonly>
                        <button class="btn" onclick="copyLink()">📋</button>
                    </div>
                    
                    <div style="text-align: center; margin: 20px 0;">
                        <p>Scannez le QR Code :</p>
                        <div style="background: white; padding: 15px; border-radius: 10px; display: inline-block; margin: 10px 0;">
                            <div style="width: 150px; height: 150px; background: #f0f0f0; display: flex; align-items: center; justify-content: center; border: 2px dashed #ccc; font-size: 0.8rem; text-align: center;">
                                📱<br>QR Code<br>Disponible en ligne
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="card">
                    <h3>👥 Inviter des Camarades</h3>
                    <p style="margin-bottom: 15px;">Message pré-rédigé :</p>
                    <div style="background: #f8f9fa; padding: 15px; border-radius: 10px; border-left: 4px solid var(--primary);">
                        <p style="font-style: italic; margin-bottom: 10px;">
                            "Salut ! Découvre DroitMaster, une app géniale pour réviser le droit 📱⚖️. Cours interactifs, QCM, assistant IA... Parfait pour nos révisions !"
                        </p>
                    </div>
                    <button class="btn btn-block" onclick="shareMessage()" style="margin-top: 15px;">
                        📤 Partager ce Message
                    </button>
                </div>
            </div>
        </main>
    </div>

    <script>
        // Navigation
        function showTab(tabName) {
            document.querySelectorAll('.tab-content').forEach(tab => {
                tab.classList.remove('active');
            });
            document.querySelectorAll('.tab-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            document.getElementById(tabName).classList.add('active');
            event.currentTarget.classList.add('active');
        }

        // Chat functions
        function sendMobileMessage() {
            const input = document.getElementById('mobileInput');
            const message = input.value.trim();
            if (message === '') return;
            
            addMobileMessage(message, 'user');
            input.value = '';
            
            setTimeout(() => {
                const response = getMobileResponse(message);
                addMobileMessage(response, 'bot');
            }, 1000);
        }

        function askQuickQuestion(question) {
            document.getElementById('mobileInput').value = question;
            sendMobileMessage();
        }

        function addMobileMessage(text, sender) {
            const container = document.getElementById('chatMobile');
            const messageDiv = document.createElement('div');
            messageDiv.className = `message ${sender}-message`;
            messageDiv.textContent = text;
            container.appendChild(messageDiv);
            container.scrollTop = container.scrollHeight;
        }

        function getMobileResponse(question) {
            const responses = {
                'contrat': "📝 Un contrat est un accord de volontés entre deux ou plusieurs personnes destiné à créer des obligations juridiques.",
                'droit objectif': "⚖️ Le droit objectif est l'ensemble des règles juridiques applicables dans un État.",
                'sources': "📚 Les sources du droit : loi, coutume, jurisprudence, doctrine."
            };
            
            for (const [key, response] of Object.entries(responses)) {
                if (question.toLowerCase().includes(key)) {
                    return response;
                }
            }
            
            return "🤔 Je suis votre assistant juridique. Posez-moi des questions sur le droit !";
        }

        // QCM functions
        function startMobileQCM() {
            const qcmContainer = document.getElementById('qcmMobile');
            qcmContainer.innerHTML = `
                <h3>Question 1/3</h3>
                <p style="margin: 15px 0; font-weight: 600;">Qu'est-ce que le droit objectif ?</p>
                
                <div class="qcm-option" onclick="selectMobileAnswer(this)">A) Les droits individuels</div>
                <div class="qcm-option" onclick="selectMobileAnswer(this)">B) L'ensemble des règles juridiques</div>
                <div class="qcm-option" onclick="selectMobileAnswer(this)">C) Les décisions de justice</div>
                
                <button class="btn btn-block" onclick="nextMobileQuestion()" style="margin-top: 20px;">
                    Question Suivante →
                </button>
            `;
        }

        function selectMobileAnswer(element) {
            document.querySelectorAll('.qcm-option').forEach(option => {
                option.classList.remove('selected');
            });
            element.classList.add('selected');
        }

        function nextMobileQuestion() {
            const qcmContainer = document.getElementById('qcmMobile');
            qcmContainer.innerHTML = `
                <div style="text-align: center; padding: 40px 20px;">
                    <div style="font-size: 3rem; margin-bottom: 20px;">🎉</div>
                    <h3>Quiz Terminé !</h3>
                    <p style="margin: 15px 0;">Vous avez obtenu 2/3 bonnes réponses</p>
                    <p style="color: #28a745; font-weight: 600;">🌟 Excellent travail !</p>
                    
                    <button class="btn btn-block" onclick="startMobileQCM()" style="margin-top: 20px;">
                        🔄 Recommencer
                    </button>
                </div>
            `;
        }

        // Partage functions
        function shareApp() {
            const message = `Découvre DroitMaster ! 🎓⚖️

Une app mobile géniale pour réviser le droit :
• Cours interactifs
• QCM automatiques  
• Assistant IA juridique
• Suivi de progression

Parfait pour nos révisions !

Lien : ${window.location.href}`;

            window.open(`https://wa.me/?text=${encodeURIComponent(message)}`, '_blank');
        }

        function copyLink() {
            const link = window.location.href;
            navigator.clipboard.writeText(link).then(() => {
                alert('✅ Lien copié ! Partagez-le à vos camarades');
            });
        }

        function shareMessage() {
            const message = `Salut ! Découvre DroitMaster, une app géniale pour réviser le droit 📱⚖️. Cours interactifs, QCM, assistant IA... Parfait pour nos révisions ! ${window.location.href}`;
            
            if (navigator.share) {
                navigator.share({
                    title: 'DroitMaster - App Juridique',
                    text: message
                });
            } else {
                navigator.clipboard.writeText(message).then(() => {
                    alert('✅ Message copié ! Collez-le dans WhatsApp/Telegram');
                });
            }
        }

        // Other functions
        function startQuickQCM() {
            showTab('qcm');
            startMobileQCM();
        }

        function openCourse(courseId) {
            showTab('chat');
            const message = "Posez-moi vos questions sur ce cours !";
            addMobileMessage(message, 'bot');
        }

        // Initialize share link
        document.getElementById('shareLink').value = window.location.href;

        // Initial animation
        document.addEventListener('DOMContentLoaded', function() {
            document.querySelector('.app-container').style.opacity = '0';
            document.querySelector('.app-container').style.transform = 'translateY(20px)';
            
            setTimeout(() => {
                document.querySelector('.app-container').style.transition = 'all 0.5s ease';
                document.querySelector('.app-container').style.opacity = '1';
                document.querySelector('.app-container').style.transform = 'translateY(0)';
            }, 100);
        });
    </script>
</body>
</html>
