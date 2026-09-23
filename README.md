<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Special Question For You</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&family=Sacramento&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 99%, #fecfef 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            position: relative;
        }

        /* Floating Hearts Background */
        .hearts-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: 0;
            pointer-events: none;
        }

        .heart {
            position: absolute;
            width: 20px;
            height: 20px;
            background: rgba(255, 255, 255, 0.4);
            transform: rotate(45deg);
            animation: floatUp 6s linear infinite;
        }

        .heart::before,
        .heart::after {
            content: '';
            position: absolute;
            width: 20px;
            height: 20px;
            background: rgba(255, 255, 255, 0.4);
            border-radius: 50%;
        }

        .heart::before {
            top: -10px;
            left: 0;
        }

        .heart::after {
            top: 0;
            left: -10px;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(100vh) rotate(45deg) scale(0.5);
                opacity: 0;
            }
            50% {
                opacity: 0.8;
            }
            100% {
                transform: translateY(-10vh) rotate(45deg) scale(1.2);
                opacity: 0;
            }
        }

        /* Main Card Container */
        .card {
            position: relative;
            z-index: 10;
            background: rgba(255, 255, 255, 0.9);
            padding: 40px 30px;
            border-radius: 24px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
            text-align: center;
            max-width: 420px;
            width: 90%;
            backdrop-filter: blur(10px);
            transition: all 0.5s ease;
        }

        h1 {
            font-family: 'Sacramento', cursive;
            font-size: 3.2rem;
            color: #d63384;
            margin-bottom: 30px;
            line-height: 1.2;
        }

        /* Buttons Section */
        .buttons-container {
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            margin-top: 20px;
            min-height: 80px;
        }

        .btn {
            padding: 12px 30px;
            font-size: 1.1rem;
            font-weight: 600;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: transform 0.2s ease, background 0.2s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }

        #yes-btn {
            background-color: #ff4d6d;
            color: white;
            z-index: 2;
        }

        #yes-btn:hover {
            background-color: #e63956;
            transform: scale(1.05);
        }

        #no-btn {
            background-color: #adb5bd;
            color: white;
            position: absolute;
            transition: 0.15s ease-out;
            z-index: 1;
        }

        /* Page 2 Celebration Screen */
        .hidden {
            display: none !important;
        }

        .celebration-content img {
            width: 100%;
            max-height: 250px;
            object-fit: cover;
            border-radius: 16px;
            margin-bottom: 20px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.15);
        }

        .celebration-content p {
            font-size: 1.1rem;
            color: #495057;
            margin-bottom: 25px;
            line-height: 1.6;
        }

        .back-btn {
            background: #ff758c;
            color: white;
            padding: 10px 20px;
            border-radius: 20px;
            border: none;
            cursor: pointer;
            font-size: 0.9rem;
            font-weight: 600;
        }

        /* Admin Settings Gear */
        .admin-gear {
            position: fixed;
            top: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.8);
            border: none;
            border-radius: 50%;
            width: 45px;
            height: 45px;
            cursor: pointer;
            font-size: 1.3rem;
            z-index: 100;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: transform 0.2s;
        }

        .admin-gear:hover {
            transform: rotate(45deg);
        }

        /* Admin Modal */
        .admin-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }

        .admin-box {
            background: white;
            padding: 30px;
            border-radius: 20px;
            width: 90%;
            max-width: 400px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            text-align: left;
        }

        .admin-box h2 {
            margin-bottom: 15px;
            color: #d63384;
            font-size: 1.5rem;
        }

        .admin-box label {
            display: block;
            margin-top: 12px;
            margin-bottom: 5px;
            font-weight: 600;
            font-size: 0.9rem;
            color: #333;
        }

        .admin-box input[type="text"],
        .admin-box textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ced4da;
            border-radius: 8px;
            font-size: 0.95rem;
            font-family: inherit;
        }

        .admin-box textarea {
            resize: vertical;
            height: 80px;
        }

        .admin-box input[type="file"] {
            margin-top: 5px;
            font-size: 0.9rem;
        }

        .admin-buttons {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }

        .admin-buttons button {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
        }

        .save-btn {
            background: #ff4d6d;
            color: white;
        }

        .close-btn {
            background: #ced4da;
            color: #333;
        }
    </style>
</head>
<body>

    <!-- Floating Background Hearts -->
    <div class="hearts-bg" id="hearts-bg"></div>

    <!-- Admin Gear Button -->
    <button class="admin-gear" id="gear-btn" title="Admin Settings">⚙️</button>

    <!-- Main Card -->
    <div class="card" id="main-card">
        <!-- Page 1: Question -->
        <div id="page-1">
            <h1 id="question-text">Will you be my Valentine? 💕</h1>
            <div class="buttons-container">
                <button class="btn" id="yes-btn">Yes!</button>
                <button class="btn" id="no-btn">No</button>
            </div>
        </div>

        <!-- Page 2: Celebration / Message -->
        <div id="page-2" class="hidden celebration-content">
            <h1 style="font-size: 2.8rem; margin-bottom: 15px;">Yay! 🎉💖</h1>
            <img id="display-img" src="https://images.unsplash.com/photo-1518199266791-5375a83190b7?auto=format&fit=crop&w=600&q=80" alt="Our Photo">
            <p id="display-msg">I knew you would say yes! You make me the happiest person in the world. 🥰</p>
            <button class="back-btn" id="reset-btn">Back</button>
        </div>
    </div>

    <!-- Admin Modal -->
    <div class="admin-modal hidden" id="admin-modal">
        <div class="admin-box">
            <h2>Admin Settings</h2>
            <label for="input-question">Question:</label>
            <input type="text" id="input-question" value="Will you be my Valentine? 💕">

            <label for="input-msg">Celebration Message:</label>
            <textarea id="input-msg">I knew you would say yes! You make me the happiest person in the world. 🥰</textarea>

            <label for="input-photo">Upload Photo:</label>
            <input type="file" id="input-photo" accept="image/*">

            <div class="admin-buttons">
                <button class="close-btn" id="admin-close">Cancel</button>
                <button class="save-btn" id="admin-save">Save Changes</button>
            </div>
        </div>
    </div>

    <script>
        // Generate floating hearts background
        const heartsBg = document.getElementById('hearts-bg');
        for (let i = 0; i < 20; i++) {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.style.left = Math.random() * 100 + '%';
            heart.style.top = Math.random() * 100 + '%';
            heart.style.animationDuration = (Math.random() * 4 + 4) + 's';
            heart.style.animationDelay = (Math.random() * 5) + 's';
            heartsBg.appendChild(heart);
        }

        // Elements
        const yesBtn = document.getElementById('yes-btn');
        const noBtn = document.getElementById('no-btn');
        const page1 = document.getElementById('page-1');
        const page2 = document.getElementById('page-2');
        const questionText = document.getElementById('question-text');
        const displayMsg = document.getElementById('display-msg');
        const displayImg = document.getElementById('display-img');
        const resetBtn = document.getElementById('reset-btn');

        const gearBtn = document.getElementById('gear-btn');
        const adminModal = document.getElementById('admin-modal');
        const adminClose = document.getElementById('admin-close');
        const adminSave = document.getElementById('admin-save');
        const inputQuestion = document.getElementById('input-question');
        const inputMsg = document.getElementById('input-msg');
        const inputPhoto = document.getElementById('input-photo');

        let customPhotoBase64 = "";

        // Runaway "No" button logic
        const noTexts = [
            "No", "Are you sure?", "Think again!", "Last chance!", 
            "Surely not?", "You might regret this!", "Give it another thought!", 
            "Are you absolutely sure?", "Have a heart!"
        ];
        let textIndex = 0;

        function moveNoButton() {
            const cardRect = document.getElementById('main-card').getBoundingClientRect();
            const btnRect = noBtn.getBoundingClientRect();

            // Calculate random positions within safe bounds inside the screen/card
            const maxX = window.innerWidth - btnRect.width - 40;
            const maxY = window.innerHeight - btnRect.height - 40;
            const minX = 20;
            const minY = 20;

            const randomX = Math.floor(Math.random() * (maxX - minX)) + minX;
            const randomY = Math.floor(Math.random() * (maxY - minY)) + minY;

            noBtn.style.position = 'fixed';
            noBtn.style.left = randomX + 'px';
            noBtn.style.top = randomY + 'px';

            textIndex = (textIndex + 1) % noTexts.length;
            noBtn.innerText = noTexts[textIndex];
        }

        noBtn.addEventListener('mouseover', moveNoButton);
        noBtn.addEventListener('click', moveNoButton);
        noBtn.addEventListener('touchstart', (e) => {
            e.preventDefault();
            moveNoButton();
        });

        // Yes button click action
        yesBtn.addEventListener('click', () => {
            page1.classList.add('hidden');
            page2.classList.remove('hidden');
        });

        // Reset back button
        resetBtn.addEventListener('click', () => {
            page2.classList.add('hidden');
            page1.classList.remove('hidden');
            noBtn.style.position = 'absolute';
            noBtn.style.left = 'auto';
            noBtn.style.top = 'auto';
            noBtn.innerText = 'No';
        });

        // Admin Modal Controls
        gearBtn.addEventListener('click', () => {
            adminModal.classList.remove('hidden');
        });

        adminClose.addEventListener('click', () => {
            adminModal.classList.add('hidden');
        });

        inputPhoto.addEventListener('change', function(e) {
            const file = e.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(uploadEvent) {
                    customPhotoBase64 = uploadEvent.target.result;
                };
                reader.readAsDataURL(file);
            }
        });

        adminSave.addEventListener('click', () => {
            if (inputQuestion.value.trim() !== "") {
                questionText.innerText = inputQuestion.value;
            }
            if (inputMsg.value.trim() !== "") {
                displayMsg.innerText = inputMsg.value;
            }
            if (customPhotoBase64 !== "") {
                displayImg.src = customPhotoBase64;
            }
            adminModal.classList.add('hidden');
        });
    </script>
</body>
</html>
