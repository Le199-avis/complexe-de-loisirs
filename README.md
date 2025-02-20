<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laissez un Avis & Recevez une Récompense</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; padding: 20px; }
        .container { max-width: 500px; margin: auto; }
        button { background-color: #4285F4; color: white; padding: 10px 20px; border: none; cursor: pointer; }
        form { margin-top: 20px; }
        .wheel-container { margin-top: 30px; }
        canvas { border: 2px solid #000; }
    </style>
</head>
<body>
    <div class="container">
        <h2>Obtenez une récompense en laissant un avis !</h2>
        <p>Cliquez sur le bouton ci-dessous pour laisser un avis sur notre fiche Google.</p>
        
        <a href="https://g.page/r/CVe-BrIZHpMMEAE/review" target="_blank">
            <button>Laisser un Avis sur Google</button>
        </a>

        <form action="submit.php" method="post" enctype="multipart/form-data" onsubmit="event.preventDefault(); showWheel();">
            <h3>Confirmez votre avis</h3>
            <label for="name">Nom utilisé pour l'avis :</label>
            <input type="text" id="name" name="name" required><br><br>
            
            <label for="screenshot">Capture d'écran de votre avis :</label>
            <input type="file" id="screenshot" name="screenshot" accept="image/*" required><br><br>
            
            <label for="email">Votre Email (pour la récompense) :</label>
            <input type="email" id="email" name="email" required><br><br>
            
            <button type="submit">Envoyer et Recevoir la Récompense</button>
        </form>

        <div class="wheel-container" id="wheelSection" style="display: none;">
            <h3>Tournez la roue pour découvrir votre récompense !</h3>
            <canvas id="wheelCanvas" width="300" height="300"></canvas><br>
            <button onclick="spinWheel()">Tourner la roue</button>
            <p id="rewardResult"></p>
        </div>
    </div>

    <script>
        let rewards = ["5% de réduction", "10% de réduction", "Livraison offerte", "Cadeau surprise", "Aucune récompense", "15% de réduction", "Un bracelet", "Une heure offerte", "Perdu", "Perdu", "Perdu", "Un gobelet"];
        let spinning = false;

        function showWheel() {
            document.getElementById("wheelSection").style.display = "block";
        }

        function spinWheel() {
            if (spinning) return;
            spinning = true;

            let randomIndex = Math.floor(Math.random() * rewards.length);
            let reward = rewards[randomIndex];

            setTimeout(() => {
                document.getElementById("rewardResult").innerText = "Vous avez gagné : " + reward + " !";
                spinning = false;
            }, 3000);
        }
    </script>
</body>
</html>
