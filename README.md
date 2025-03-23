<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interaktive Symbole</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            flex-direction: column;
        }
        .circleButton {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background-color: #007bff;
            display: flex;
            align-items: center;
            justify-content: center;
            color: rgb(205, 11, 239);
            font-size: 24px;
              cursor: pointer;
            margin: 10px;
            transition: transform 1s ease;
        }
        .circleButton:hover {
            transform: rotate(360deg);
        }
        .hiddenContent {
            display: none;
            margin-top: 20px;
            font-size: 18px;
            text-align: center;
        }
        #chatContent, #videoContent, #searchContent, #kiContent {
            margin: 10px 0;
        }
        #contentArea {
            width: 80%;
            max-width: 600px;
            text-align: center;
        }
        .buttonText {
            font-size: 18px;
            color: #007bff;
            cursor: pointer;
          }
        .buttonText:hover {
            color: #0056b3;
        }
    </style>
</head>
<body>

<!-- Symbole -->
<div id="chatButton" class="circleButton" onclick="toggleContent('chat')">💬</div>
<div id="videoButton" class="circleButton" onclick="toggleContent('video')">🎥</div>
<div id="searchButton" class="circleButton" onclick="toggleContent('search')">🔍</div>
<div id="kiButton" class="circleButton" onclick="toggleContent('ki')">🤖</div>

<div id="contentArea">
    <div id="chatContent" class="hiddenContent">
        <p>Chat geöffnet! Du kannst jetzt Nachrichten senden.</p>
        <input type="text" id="chatInput" placeholder="Schreibe hier deine Nachricht..." onkeydown="sendMessage(event)">
        <div id="chatbox" style="border: 1px solid #ccc; padding: 10px; height: 150px; overflow-y: auto; background-color: #fff;"></div>
    </div>

    <div id="videoContent" class="hiddenContent">
        <p>Video-Funktion geöffnet! Poste jetzt ein Video.</p>
        <textarea id="videoInput" placeholder="Gib deinen Video-Link hier ein..."></textarea>
        <button onclick="postVideo()">Posten</button>
    </div>

    <div id="searchContent" class="hiddenContent">
        <p>Such-Funktion geöffnet! Gib etwas ein, um zu suchen.</p>
        <input type="text" id="searchInput" placeholder="Suchbegriff eingeben..." onkeydown="searchContent(event)">
    </div>

    <div id="kiContent" class="hiddenContent">
        <p>KI-Funktion geöffnet! Stelle eine Frage an die KI.</p>
        <input type="text" id="kiInput" placeholder="Stelle eine Frage..." onkeydown="askKI(event)">
    </div>
</div>

<script>
// Funktion zum Umschalten der Inhalte
function toggleContent(type) {
    // Alle Inhalte verstecken
    const contentElements = document.querySelectorAll('.hiddenContent');
    contentElements.forEach((element) => {
        element.style.display = 'none';
    });

    // Das angeklickte Symbol zeigt den entsprechenden Inhalt an
    const contentId = type + 'Content';
    document.getElementById(contentId).style.display = 'block';
}

// Chat-Funktion
function sendMessage(event) {
    if (event.key === "Enter") {
        const message = document.getElementById("chatInput").value.trim();
        if (message) {
            const chatbox = document.getElementById("chatbox");
            const newMessage = document.createElement("p");
            newMessage.textContent = `Du: ${message}`;
            chatbox.appendChild(newMessage);
            chatbox.scrollTop = chatbox.scrollHeight; // Zum neuesten Eintrag scrollen
            document.getElementById("chatInput").value = ''; // Eingabefeld leeren
        }
    }
}

// Video posten
function postVideo() {
    const videoLink = document.getElementById("videoInput").value.trim();
    if (videoLink) {
        alert(`Video-Link: ${videoLink} wurde gepostet!`);
        document.getElementById("videoInput").value = ''; // Eingabefeld leeren
    }
}

// Suchfunktion
function searchContent(event) {
    if (event.key === "Enter") {
        const query = document.getElementById("searchInput").value.trim();
        if (query) {
            alert(`Suchergebnisse für: ${query}`);
            document.getElementById("searchInput").value = ''; // Eingabefeld leeren
        }
    }
}

// KI-Fragen stellen
function askKI(event) {
    if (event.key === "Enter") {
        const question = document.getElementById("kiInput").value.trim();
        if (question) {
            alert(`Du hast gefragt: "${question}". Hier könnte deine KI-Antwort sein.`);
            document.getElementById("kiInput").value = ''; // Eingabefeld leeren
        }
    }
}
</script>

</body>
</html>
<a>Maker Daniel Polender</a>
