Tutoriel d'utilisation
Installer python si c'est pas déjà fait (si vous l'installez maintenant, quand vous allez ouvrir l'installateur, n'oubliez pas de cocher "add to PATH" en bas c'est important). Python 3.11 est préférable, je sais pas si les autres versions marchent.
dans une console, faites `pip install python-dotenv google-generativeai discord.py-self` pour installer les librairies python nécessaires
récupérer main.py et mettez le de préférence dans un dossier à part
dans le même dossier, créez un fichier ".env" (sans les ") et à l'intérieur mettez ça
```
GEMINI_API_KEY=votre_api_key
DISCORD_USER_TOKEN=votre_token
CONTROLLER_ID=votre_id
CONTROLLER_CHANNEL_ID=votre_id_de_salon
```

Il va falloir remplacer les valeurs par défauts:
- Pour GEMINI_API_KEY, créez et récupérez une clé d'api pour AiStudio de google à https://aistudio.google.com/app/apikey (gratuit)
- Pour DISCORD_USER_TOKEN c'est ça la partie contraignate du script. Pour pouvoir récupérez automatiquement des messages sans pouvoir ajouter de vrai bot discord, on va devoir faire ce qui s'appelle **self-bot** ce qui est **interdit par les ToS de discord et si mal utilisé peut faire bannir votre compte**. Ici, on ne fait que récupérer ou envoyer des messages normaux, donc le risque ne devrait pas être énorme, mais je recommand quand même fortement d'utiliser un double compte. Ensuite pour ce double compte, il faut aller chercher votre token discord. Il y a plein de tutoriels sur youtube, c'est rapide, en voici un par exemple : https://www.youtube.com/watch?v=LnBnm_tZlyU . **ne partagez jamais le token discord à qui que se soit car on peut l'utiliser pour se connecter au comtpe discord et aussi bypass la 2FA**. Une fois le token de votre double compte copié, mettez le dans la config, sans les "" au début et à la fin
- Pour CONTROLLER_ID, comme j'assume que le compte est un double compte, vous pouvez ici mettre le user id de votre vrai compte au moins vous pourrez envoyer des commandes au self-bot depuis votre compte principal.
- Pour CONTROLLER_CHANNEL_ID, mettez l'id d'un salon où vous aller utiliser les commandes du script. C'est pour éviter d'activer le self-bot dans le mauvais salon.

- Ensuite, juste lancez le script (dans une console dans le même dossier, `python main.py`), et avec un compte autoriser (le compte dont vous avez mis le token ou le compte de COLTROLLER_ID) et vous pourrez envoyer vos commandes et avoir vos réponses dans le salon de CONTROLLER_CHANNEL_ID :
- - "$summarize" est la seule commande disponible pour l'instant et résume les messages des 7 derniers jours avec les 14 derniers jours en contexte. (Pour changer cela, allez dans main.py et recherchez `hours_to_summarize` (heures à résumer) vous trouverez `hours_to_summarize = un_nombre` et vous pourrez changer ce nombre. Juste en dessous il y a aussi le nombre d'heures en contexte, `context_hours`)
