# Calculatrice vocale

<p>
  <img alt="voix" src="https://img.shields.io/badge/voix-Web%20Speech%20API-ffd43b?labelColor=30363d">
  <img alt="page unique" src="https://img.shields.io/badge/page-unique-2ea043?labelColor=30363d">
  <img alt="mobile" src="https://img.shields.io/badge/format-mobile%20fixe-1f6feb?labelColor=30363d">
  <br>
  <img alt="aucune dependance" src="https://img.shields.io/badge/d%C3%A9pendances-aucune-3fb950?labelColor=30363d">
  <img alt="aucun compte" src="https://img.shields.io/badge/compte-aucun-3fb950?labelColor=30363d">
  <img alt="licence MIT" src="https://img.shields.io/badge/licence-MIT-2ea043?labelColor=30363d">
  <img alt="gratuit" src="https://img.shields.io/badge/prix-gratuit-2ea043?labelColor=30363d">
</p>

**Tu dictes, elle calcule.** Une calculatrice de telephone, ecran unique et sans menu : tu dis le calcul a voix haute, le resultat s'affiche, puis tout s'efface pour le suivant. Le projet entier tient dans un seul fichier HTML.

<h3 align="center">
  <a href="https://github.com/moonspiid/calculatrice-vocale/blob/main/index.html" target="_blank" rel="noopener noreferrer">⬆ Voir le fichier</a>
</h3>

<p align="center">
  Pas de compte, pas de serveur, pas de build, pas de dependance — un fichier <code>index.html</code>, tu l'ouvres et tu parles.
  <br>
  Rien ne quitte le navigateur : aucune donnee envoyee, aucune cle, aucune requete vers un serveur a nous.
</p>

## Sommaire

- [Pourquoi](#pourquoi)
- [Fonctionnalites](#fonctionnalit%C3%A9s)
- [Demarrage rapide](#d%C3%A9marrage-rapide)
- [Comment ca marche](#comment-%C3%A7a-marche)
- [Bon a savoir](#bon-%C3%A0-savoir)
- [Soutenir ce projet](#soutenir-ce-projet)
- [Licence](#licence)

## Pourquoi

Taper un calcul sur un clavier de telephone prend du temps, et il faut deja les deux mains. Une calculatrice qui ecoute evite le detour : on dit « deux plus trois fois quatre », on continue ce qu'on faisait, le resultat est la. Pas d'application a installer, pas de compte, pas de menus — juste un ecran de calculatrice et un gros bouton.

## Fonctionnalites

- **Design fixe de calculatrice mobile** — ecran unique sans menu, affichage en haut, clavier 4×5 en bas, plein ecran sur telephone et centre comme un appareil sur ordinateur.
- **Clavier tactile standard** — `AC`, `⌫`, `%`, `±`, `÷ × − +`, virgule, `=`, avec un retour visuel a chaque appui et des tailles qui restent lisibles du petit telephone au desktop.
- **Un gros bouton de commande vocale** sous le clavier — il pulse en rouge pendant l'ecoute et affiche la phrase reconnue en direct.
- **La parole devient une equation** — nombres en toutes lettres (jusqu'aux millions), `virgule` pour les decimales, `plus`, `moins`, `fois`, `multiplie par`, `divise par`, `sur`, `pour cent` ; « deux plus trois fois quatre » devient `2+3*4` = `14`, priorites respectees.
- **Resultat puis remise a zero** — l'equation s'affiche au-dessus du resultat, puis la calculatrice se reinitialise seule apres 2,8 s pour le calcul suivant.
- **Calcul protege** — seuls les chiffres et les operateurs autorises sont evalues (`0-9 + - * / % ( ) .`), le resultat est arrondi a 10 decimales, un calcul incomplet n'affiche jamais de valeur fausse.
- **Tout en francais** — reconnaissance reglee sur `fr-FR`, nombres et operateurs dictes comme on parle.

## Demarrage rapide

1. Telecharge `index.html` — c'est tout le projet.
2. Sers le fichier depuis `localhost` (le micro est bloque sur `file://`) : `python3 -m http.server 8000`, puis ouvre `http://localhost:8000`.
3. Touche le gros bouton, autorise le microphone, et dicte par exemple **« douze divise par quatre »**.
4. L'equation et le resultat s'affichent, la calculatrice se remet a zero toute seule.

## Comment ca marche

- `index.html` — la feuille de style, le clavier, le bouton vocal et la logique, dans un seul fichier.
- La reconnaissance passe par `SpeechRecognition` / `webkitSpeechRecognition` en `fr-FR`, avec les resultats intermediaires affiches pendant que tu parles.
- `speechToEquation()` nettoie la phrase (accents, tirets de « dix-sept », « virgule »), remplace les mots operateurs, convertit les nombres en lettres en chiffres, puis ne garde que les caracteres mathematiques.
- `safeEval()` evalue l'expression obtenue et arrondit a 10 decimales ; en cas d'expression vide ou invalide, rien n'est affiche.
- `resetAll()` efface l'equation, la transcription et le resultat pour le calcul suivant.

## Bon a savoir

- **HTTPS ou localhost obligatoire** pour le microphone — c'est une regle du navigateur. Ouvert directement en `file://`, le bouton affiche un message a la place.
- **Chrome, Edge et Safari recent** gerent l'API Web Speech. Firefox ne la gere pas : le bouton explique alors qu'il faut changer de navigateur.
- La dictee est reglee sur le francais (`fr-FR`) ; les nombres en lettres sont compris jusqu'aux millions, « deux virgule cinq » est accepte.
- Aucun historique n'est conserve : le calcul vit en memoire le temps de l'affichage, puis disparait.

## Soutenir ce projet

L'app est gratuite, sans compte, sans publicite et sans tracking, et il n'y a pas d'offre payante. Si elle te fait gagner du temps, un don paie les heures derriere et les prochaines fonctionnalites.

**Don en USDT →** une seule adresse crypto, pas de carte, pas de compte, pas de processeur de paiement entre les deux.

<p align="center">
  <img src="https://raw.githubusercontent.com/moonspiid/ai-agent-multi-model/master/donate-usdt-qr.png" alt="QR code de l'adresse de don EVM" width="200">
  <br>
  <sub>Scanne avec n'importe quel wallet</sub>
</p>

```
0xA2700896E16BE762467D458F2B45260f8FAC9F3E
```

C'est une adresse EVM classique, donc **la meme adresse fonctionne sur tous les reseaux EVM**. Envoie de l'USDT sur celui que tu preferes :

| Reseau | Jeton |
| --- | --- |
| BNB Smart Chain (BEP20) | USDT |
| Ethereum (ERC20) | USDT |
| Polygon | USDT |
| Arbitrum One | USDT |
| Base | USDT |
| Optimism | USDT |

Deux regles : envoie **uniquement de l'USDT** (un autre jeton envoye a cette adresse ne peut pas etre recupere), et garde un peu de la monnaie du reseau (BNB, ETH, POL) dans ton wallet pour payer les frais. Un reseau non EVM comme Tron (TRC20) utilise un autre format d'adresse : rien de ce qui y est envoye n'arrive ici.

## Licence

MIT © 2026 moonspiid — utilise-la, modifie-la, diffuse-la.
