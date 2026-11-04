# Installer Hermes Agent : le guide en français

Hermes Agent est un agent IA open source de [Nous Research](https://github.com/NousResearch/hermes-agent), sous licence MIT. Il tourne sur votre machine ou sur un serveur, se connecte à un modèle d'IA et vous répond dans votre messagerie (Telegram, Discord, Slack, WhatsApp, Signal ou e-mail).

Ce guide résume les étapes d'installation en français. Il ne remplace pas la [documentation officielle](https://hermes-agent.nousresearch.com/docs/), qui fait foi et qui évolue plus vite que ce dépôt.

## Sommaire

1. [Ce qu'il vous faut](#1-ce-quil-vous-faut)
2. [Installer Hermes Agent](#2-installer-hermes-agent)
3. [Choisir le modèle d'IA](#3-choisir-le-modèle-dia)
4. [Le relier à votre messagerie](#4-le-relier-à-votre-messagerie)
5. [Le faire tourner en continu sur un serveur](#5-le-faire-tourner-en-continu-sur-un-serveur)
6. [Sécurité : les bons réflexes](#6-sécurité--les-bons-réflexes)
7. [Ce que coûte un agent](#7-ce-que-coûte-un-agent)

## 1. Ce qu'il vous faut

- **Un système compatible :** Linux, macOS ou Windows avec WSL2. Windows natif (PowerShell) et Android (Termux) ont aussi leur installateur.
- **Un accès à un modèle d'IA :** Nous Portal, OpenRouter, OpenAI ou votre propre point d'accès compatible.
- **Une messagerie** si vous voulez lui écrire depuis votre téléphone.
- **Un serveur (VPS)** si l'agent doit travailler quand votre ordinateur est éteint.

## 2. Installer Hermes Agent

Sur Linux, macOS ou WSL2 :

```bash
curl -fsSL https://hermes-agent.nousresearch.com/install.sh | bash
```

Sur Windows natif, dans PowerShell :

```powershell
iex (irm https://hermes-agent.nousresearch.com/install.ps1)
```

Rechargez ensuite votre terminal, puis lancez Hermes :

```bash
source ~/.bashrc    # ou : source ~/.zshrc
hermes
```

Avant de lancer un script téléchargé, vérifiez toujours qu'il vient bien du domaine officiel `hermes-agent.nousresearch.com`.

## 3. Choisir le modèle d'IA

```bash
hermes setup          # assistant de configuration complet
hermes model          # choisir le fournisseur et le modèle
```

Avec Nous Portal, une seule commande suffit après une installation neuve :

```bash
hermes setup --portal
```

Pendant une conversation, `/model fournisseur:modèle` change de modèle. Pour une valeur précise, utilisez `hermes config set`.

## 4. Le relier à votre messagerie

Une seule passerelle gère toutes les messageries prises en charge :

```bash
hermes gateway setup
hermes gateway start
```

Envoyez ensuite un message à votre bot. Les jetons à créer dépendent de chaque messagerie (BotFather pour Telegram, portail développeur pour Discord, etc.) : suivez le guide « Messaging Gateway » de la documentation officielle.

## 5. Le faire tourner en continu sur un serveur

Sur un ordinateur personnel, l'agent s'arrête quand la machine s'éteint. Pour un agent qui travaille chaque jour, installez-le sur un petit serveur Linux (VPS) :

1. Créez le serveur chez l'hébergeur de votre choix, **à votre nom**.
2. Connectez-vous en SSH avec une clé, pas avec un mot de passe.
3. Mettez le système à jour, puis installez Hermes comme à l'étape 2.
4. Lancez la passerelle comme un service qui redémarre tout seul (voir la documentation officielle pour la méthode recommandée).

## 6. Sécurité : les bons réflexes

- Ne publiez jamais vos clés d'API, jetons de bot ou fichiers `.env`, ni sur GitHub ni ailleurs.
- Donnez à l'agent uniquement les accès dont sa tâche a besoin.
- Gardez une validation humaine pour tout ce qui part à l'extérieur : e-mails, publications, paiements.
- Mettez à jour Hermes et le serveur régulièrement.

## 7. Ce que coûte un agent

| Élément | Coût |
|---|---|
| Hermes Agent | Gratuit, open source (licence MIT) |
| Serveur | Abonnement mensuel, payé à l'hébergeur |
| Accès à l'IA | Selon votre compte ou votre consommation d'API |

## Se faire accompagner

Si vous préférez ne pas gérer le serveur, la sécurité et la configuration vous-même, [NaoAI](https://naoai.fr) installe des agents Hermes prêts à l'emploi (prospection, contenu, veille, SEO/GEO) sur vos comptes. Détails sur la page [Installer Hermes Agent](https://naoai.fr/installer-hermes-agent).

## Sources

- Dépôt officiel : https://github.com/NousResearch/hermes-agent
- Documentation officielle : https://hermes-agent.nousresearch.com/docs/

Ce guide est indépendant et n'est pas affilié à Nous Research. Une erreur ou une commande qui a changé ? Ouvrez une issue.
