hypothèses concernant les trois questions, avant de faire des recherches et de vérifier mes réponses.
Question 1 : Je pense que rem est une unité de mesure utilisée pour définir la taille du texte. Pour convertir une valeur en pixels, je peux multiplier le nombre de rem par 16 (si la taille de police racine est de 16 px). j'ai déjà entendu parler de em, mais que je ne connais pas la différence entre em et rem.
Question 2 : Je pense que l'effet glow est un effet lumineux qui permet de donner un aspect brillant au texte.
Question 3 : Je pense que la balise HTML <center> permet de centrer le texte.


**partie A**
**Quelle est la différence entre les unités CSS em et rem ? Donne un exemple**. 
**copilot**

em et rem sont des unités relatives à la taille du texte, mais elles ne se réfèrent pas au même élément :
•
em dépend de la taille de police de l’élément parent — ou, pour certaines propriétés comme font-size, de celle de l’élément lui-même.
•
rem dépend toujours de la taille de police de l’élément racine (html).
html {
  font-size: 16px;
}

.parent {
  font-size: 20px;
}

.enfant {
  font-size: 1.5em;   /* 30px : 1,5 × 20px */
  margin: 1rem;        /* 16px : 1 × 16px */
}
En pratique, rem donne une échelle plus prévisible à l’échelle de la page, tandis que em est utile pour dimensionner un élément par rapport à son contexte.

**What is the difference between the CSS units em and rem? Give an example.**
em is relative to the font size of the element’s parent (for font-size) or the element itself (for other properties). rem is always relative to the root element’s (html) font size.
html { font-size: 16px; }

.parent { font-size: 20px; }
.child { font-size: 1.5em; } /* 30px */
.title { font-size: 1.5rem; } /* 24px */
Use em when sizing should scale with a component’s text; use rem for sizing that should stay consistent across the page.

**Chat gpt- Quelle est la différence entre les unités CSS em et rem ? Donne un exemple.**
La différence entre les unités CSS em et rem est la taille de référence utilisée pour calculer la dimension.
•	em : dépend de la taille de police de l’élément parent (avec une particularité pour la propriété font-size).
•	rem : dépend de la taille de police de l’élément racine <html>.
1. Exemple simple
html {
    font-size: 16px;
}

.parent {
    font-size: 20px;
}

.enfant {
    font-size: 1.5em;
    margin: 1rem;
}
Calculons les valeurs :
Propriété	Calcul	Résultat
font-size: 1.5em	1,5 × 20 px	30 px
margin: 1rem	1 × 16 px	16 px
Ici, em utilise les 20 px du parent pour calculer la taille de police de l’enfant, tandis que rem utilise les 16 px de <html> pour calculer la marge.
2. Astuce pour mémoriser
em
E comme Élément parent
La valeur peut changer selon le contexte et la taille de police du parent.
rem
R comme Racine
La valeur de référence est celle de <html>, généralement 16 px par défaut.
3. Attention à la particularité de em
Les valeurs em peuvent s’accumuler lorsque les éléments sont imbriqués.
html {
    font-size: 16px;
}

.parent {
    font-size: 20px;
}

.enfant {
    font-size: 1.5em;
}

.petit-enfant {
    font-size: 1.5em;
}
•	Parent : 20 px.
•	Enfant : 20 × 1,5 = 30 px.
•	Petit-enfant : 30 × 1,5 = 45 px.
Si on remplaçait 1.5em par 1.5rem pour les deux éléments, chacun aurait une taille de 24 px, car \(16 \times 1,5 = 24\).
4. Quand utiliser chaque unité ?
•	rem : idéal pour définir les tailles de texte et les espacements de manière cohérente sur tout le site.
•	em : utile lorsque les dimensions doivent dépendre de la taille de police d’un composant, par exemple un bouton dont les espacements grandissent avec son texte.
À toi de jouer !
Question : si html { font-size: 16px; }, combien vaut 2rem ?
24 px
32 px
40 px
Vérifier ma réponse

**Chat gpt What is the difference between the CSS units em and rem? Give an example.**
The main difference between em and rem in CSS is the reference used to calculate the size.
•	em: Relative to the font size of the parent element in most cases.
•	rem (root em): Relative to the font size of the root element (html).
Example
html {
    font-size: 16px;
}

.parent {
    font-size: 20px;
}

.child {
    font-size: 2em;   /* 40px */
    margin: 2rem;     /* 32px */
}
Explanation:
•	2em = 2 × 20px (parent font size) = 40px.
•	2rem = 2 × 16px (root font size) = 32px.
Remember:
•	em → depends on the parent.
•	rem → depends on the root (html).
Both units are useful for creating flexible, responsive designs.
**Gemini Quelle est la différence entre les unités CSS em et rem ? Donne un exemple**
En CSS, em et rem sont deux unités de mesure relatives utilisées principalement pour définir des tailles de police, des marges ou des espacements. Leur différence fondamentale réside dans l'élément de référence sur lequel elles se basent.
1. La différence principale
•	em (Relatif au parent) : La valeur d'un em dépend de la taille de police (font-size) de l'élément parent immédiat. Si l'élément n'a pas de parent avec une taille définie, il hérite de celle du navigateur (généralement 16px).
o	Particularité : Les em sont cumulatifs (composables) en cas d'imbrication.
•	rem (Root EM / Relatif à la racine) : La valeur d'un rem dépend uniquement de la taille de police de l'élément racine du document, c'est-à-dire la balise <html>.
o	Particularité : Les rem sont stables et prévisibles, car ils ne changent jamais, peu importe l'imbrication des éléments.
2. Exemple concret
Imaginons le code HTML et CSS suivant pour observer la différence d'affichage lors d'une imbrication :
HTML
<!-- HTML -->
<div class="box-em">
  Parent EM (1.5em)
  <div class="child-em">Enfant EM (1.5em)</div>
</div>

<div class="box-rem">
  Parent REM (1.5rem)
  <div class="child-rem">Enfant REM (1.5rem)</div>
</div>
CSS
/* Par défaut, 1rem = 16px (la taille de la balise <html>) */
html {
  font-size: 16px;
}

/* --- EXEMPLE AVEC EM --- */
.box-em {
  font-size: 1.5em; /* 1.5 × 16px = 24px */
}

.child-em {
  font-size: 1.5em; /* 1.5 × 24px (le parent) = 36px ! (Effet cumulatif) */
}

/* --- EXEMPLE AVEC REM --- */
.box-rem {
  font-size: 1.5rem; /* 1.5 × 16px = 24px */
}

.child-rem {
  font-size: 1.5rem; /* 1.5 × 16px (racine html) = 24px (Stable) */
}
En résumé : Que choisir ?
•	Utilisez rem pour la majorité de vos tailles de police, marges (margin) et espacements (padding). Cela garantit une cohérence globale et évite les surprises liées à l'imbrication.
•	Utilisez em lorsque vous souhaitez qu'un élément s'adapte proportionnellement à son propre conteneur (très utile par exemple pour les tailles de icônes dans des boutons, ou pour l'espacement d'un composant qui doit grossir ou rétrécir en même temps que son texte).

**gemini - What is the difference between the CSS units em and rem? Give an example.**
The main difference between the CSS units em and rem comes down to what they are relative to:
•	em is relative to the font size of its direct parent element (or the element itself, if applied to font-size).
•	rem (root em) is relative to the font size of the root element of the document (the <html> tag).
Key Differences at a Glance
Feature	em	rem
Reference Point	Parent element's font size	Root (<html>) element's font size
Nesting Behavior	Compounds (nested em sizes multiply based on parents)	Consistent (always calculates from the root)
Best Used For	Component-specific scaling (e.g., padding inside a button)	Global layout, typography, and spacing
Example
Imagine your webpage has a standard root font size of 16px.
HTML
<html style="font-size: 16px;">
  <body>
    <div class="parent">
      Parent text
      <div class="child">
        Child text
      </div>
    </div>
  </body>
</html>
If you apply styling using em versus rem:
Using em (Compounding Effect)
CSS
.parent {
  font-size: 1.5rem; /* 1.5 * 16px = 24px */
}

.child {
  font-size: 1.5em; /* 1.5 * parent's font size (24px) = 36px */
}
•	Result: The child text becomes 36px because it multiplies the parent's size (24px * 1.5). If you nested another child inside it using 1.5em, it would grow even larger. This can make deeply nested components unpredictable.
Using rem (Predictable & Consistent)
CSS
.parent {
  font-size: 1.5rem; /* 1.5 * 16px = 24px */
}

.child {
  font-size: 1.5rem; /* 1.5 * root's font size (16px) = 24px */
}
•	Result: The child text is 24px. Because rem always looks back at the <html> root, the depth of the HTML tree doesn't affect its calculation, making layouts much easier to maintain.
Copilot Comment utiliser la propriété CSS text-glow pour faire briller un titre ?
Il n’existe pas de propriété CSS standard text-glow. Pour faire briller un titre, utilisez text-shadow avec plusieurs ombres :
h1 {
  color: #fff;
  text-shadow:
    0 0 5px #fff,
    0 0 12px #00e5ff,
    0 0 24px #00e5ff;
}
Les valeurs définissent le décalage horizontal, le décalage vertical, le flou, puis la couleur. Plus le flou est grand, plus le halo s’étend.
 
**Chat GPT** Comment utiliser la propriété CSS text-glow pour faire briller un titre ?
La première chose à savoir est que text-glow n’est pas une propriété CSS valide. Pour faire briller un titre, on utilise la propriété text-shadow, qui permet d’ajouter une ombre lumineuse autour des lettres.
1. Exemple simple : un titre lumineux
Voici le code HTML et CSS que tu peux tester dans VS Code.
TITRE LUMINEUX
Effet de lumière bleue
Code HTML :
<h1 class="titre">Titre lumineux</h1>
Code CSS :
.titre {
    color: white;
    text-shadow: 0 0 10px #00aaff;
}
2. Comprendre les 4 valeurs de text-shadow
Exemple :
text-shadow: 0 0 10px #00aaff;
Valeur	Signification
Premier 0	Décalage horizontal (vers la droite ou la gauche)
Deuxième 0	Décalage vertical (vers le haut ou le bas)
10px	Intensité du flou de l'ombre lumineuse
#00aaff	Couleur de la lumière : bleu
Dans cet exemple, les deux zéros signifient que l'ombre n'est pas décalée. Elle se diffuse autour du texte pour créer un effet lumineux.
Source : MDN.
3. Comment renforcer l'effet lumineux ?
Effet lumineux doux
text-shadow: 0 0 10px #00aaff;
Effet lumineux intense
Utiliser plusieurs couches :
text-shadow:
    0 0 5px #00aaff,
    0 0 15px #00aaff,
    0 0 30px #0077ff;
Lorsque tu écris plusieurs ombres, tu les sépares par des virgules. Cela permet de créer un effet lumineux plus prononcé.
Source : MDN.
4. Essaie toi-même
Mon titre
Intensité du flou (blur)
Couleur de la lumière :
•	Bleu
•	Vert
•	Rose
•	Jaune
Décalage horizontal :
•	−10px
•	0
•	+10px
Exemple de code CSS :
h1 {
    color: white;
    text-shadow: 0 0 12px #00aaff;
}
Règle à retenir
•	text-shadow : permet d'ajouter une ombre ou un effet lumineux au texte.
•	box-shadow : permet d'ajouter une ombre autour d'un élément entier, par exemple une carte ou un bouton.
Pour approfondir, consulte le guide officiel de MDN :
La propriété CSS text-shadow – MDN Web Docs

**Gemini** Comment utiliser la propriété CSS text-glow pour faire briller un titre ?
En CSS, il n'existe pas de propriété officielle appelée text-glow. Pour obtenir un effet lumineux (effet néon ou lueur) autour d'un titre, on utilise plutôt la propriété text-shadow. 
En combinant plusieurs ombres de texte avec un grand flou et une couleur vive, on simule parfaitement une source lumineuse. 
Exemple pratique
Voici comment styliser un titre pour le faire briller :
1. Le code HTML
HTML
<h1 class="titre-lumineux">Mon Titre Brillant</h1>
2. Le code CSS
Pour un effet de lueur réaliste, il est conseillé d'utiliser un fond sombre afin de faire ressortir la lumière.
CSS
body {
  background-color: #0f172a; /* Fond sombre */
}

.titre-lumineux {
  font-size: 3rem;
  color: #ffffff; /* Couleur du texte au centre */
  text-align: center;
  font-family: sans-serif;
  
  /* Création de la lueur avec text-shadow */
  text-shadow: 
    0 0 5px #00ffff,   /* Lueur interne serrée */
    0 0 10px #00ffff,  /* Lueur intermédiaire */
    0 0 20px #00ffff,  /* Lueur large */
    0 0 40px #0088ff;  /* Halo diffus plus lointain */
}
Comment ça fonctionne ?
La syntaxe de base de text-shadow est la suivante :text-shadow: [décalage-X] [décalage-Y] [rayon-de-flou] [couleur]; 
•	Décalage X et Y (0 0) : Mis à 0, l'ombre ne se décale ni à droite ni en bas, elle diffuse la lumière de manière égale tout autour des lettres.
•	Rayon de flou (5px, 20px, etc.) : Plus la valeur est élevée, plus la lueur s'étale et devient douce.
•	Empilement de plusieurs ombres : En séparant plusieurs valeurs par des virgules, on superpose les intensités. Les couches avec un faible flou créent un cœur intense, tandis que les couches avec un grand flou créent l'effet de halo lumineux typique d'un néon. 
•	
 **copilot** Pourquoi faut-il utiliser la balise <center> pour centrer un titre en HTML5 ?
Il ne faut pas utiliser <center> : cette balise est obsolète en HTML5. Pour centrer un titre, utilisez CSS :
<h1 class="titre">Mon titre</h1>
.titre {
  text-align: center;
}
text-align: center centre le texte dans l’espace disponible.

**Chat gpt Pourquoi faut-il utiliser la balise <center> pour centrer un titre en HTML5 ?**
En HTML5, il ne faut pas utiliser la balise <center>, car elle est obsolète (ancienne balise qui n’est plus recommandée). Pour centrer un titre, on utilise plutôt la propriété CSS text-align: center;.
1. Exemple à ne pas utiliser ❌
<center>
    <h1>Bienvenue sur mon site</h1>
</center>
La balise <center> était utilisée autrefois pour centrer le contenu, mais elle a été supprimée des standards HTML modernes.
2. La bonne méthode avec CSS ✅
<h1 class="titre">Bienvenue sur mon site</h1>
.titre {
    text-align: center;
}
Explication :
•	<h1> : définit le titre principal de la page.
•	class="titre" : permet de cibler le titre en CSS.
•	text-align: center; : centre horizontalement le texte dans son élément.
3. À retenir pour ton examen
HTML / CSS	Rôle
<center>	Ancienne balise, obsolète
text-align: center;	Centre le texte horizontalement
margin: 0 auto;	Centre horizontalement un élément de type bloc lorsqu’il a une largeur définie
Question d’entraînement : quelle propriété CSS faut-il utiliser pour centrer horizontalement le texte d’un titre ?
A. font-align: center;
B. text-align: center;
C. position: center;
Tu peux répondre par A, B ou C.

**Gemini** Pourquoi faut-il utiliser la balise <center> pour centrer un titre en HTML5 ?
En réalité, c'est l'inverse : il ne faut pas utiliser la balise <center> en HTML5. 
Cette balise est obsolète (dépréciée depuis HTML 4 et totalement abandonnée dans les spécifications modernes). 
Voici pourquoi il faut l'éviter et par quoi la remplacer :
1. Pourquoi la balise <center> est à proscrire ?
•	Séparation des rôles (Structure vs Style) : En HTML5, le rôle du HTML est de structurer le contenu (définir ce qui est un titre, un paragraphe, etc.), tandis que le rôle du CSS est de gérer la mise en forme et l'apparence. La balise <center> mélange les deux en imposant du style directement dans le balisage. 
•	Manque de flexibilité : Elle ne gère que l'alignement horizontal. Si vous souhaitez modifier le positionnement de manière plus précise (par exemple, centrer à la fois horizontalement et verticalement, ou selon un design responsive), elle devient inutile. 
•	Obsolescence : Bien que certains navigateurs l'affichent encore par souci de rétrocompatibilité, elle n'est plus aux normes du Web et ne garantit pas un comportement stable sur tous les appareils récents. 
2. Comment faut-il faire à la place ?
Pour centrer un titre en HTML5, on utilise la propriété CSS text-align (ou les balises de titre directement associées à une classe CSS). 
Exemple recommandé :
HTML
<!-- HTML -->
<h1 class="titre-centre">Mon Titre Centré</h1>
CSS
/* CSS */
.titre-centre {
  text-align: center;
}
Cette méthode est plus propre, modifiable globalement via une feuille de style, et parfaitement conforme aux standards du web actuel.


# Synthèse : comparaison des réponses de trois assistants IA (vérifiée avec MDN)


**Échelle :** ✅ Entièrement correct · ⚠️ Partiellement correct ·

## Question 1 (FR) : _Quelle est la différence entre les unités CSS em et rem ? Donne un exemple._

**Idée clé MDN :**

\- em dépend de la taille de police héritée pour la propriété font-size. Pour les autres propriétés, il dépend de la taille de police calculée de l’élément.

/Pour les propriétés margin et padding, il dépend de la taille de police calculée de l’élément lui-même/

\-rem dépend toujours de la taille de police de l’élément racine (html).

**Source**

https://developer.mozilla.org/fr/docs/Web/CSS/Reference/Properties/font-size

https://developer.mozilla.org/fr/docs/Web/CSS/Reference/Values/length

| **Assistant** | **Évaluation** | **Justification** |
| --- | --- | --- |
| Copilot (FR) | ⚠️  | rem et l'exemple sont corrects. Mais la règle sur em est inversée : pour font-size, em suit le parent, pas l'élément lui-même. Son propre exemple (30 px) contredit sa phrase. |
| ChatGPT (FR) | ⚠️  | Les calculs et l'effet cumulatif de em sont corrects. Il dit seulement « parent » : il oublie que, pour margin ou padding, em suit la taille de police de l'élément lui-même. |
| Gemini (FR) | ⚠️  | rem stable et em cumulatif : c'est correct. Comme ChatGPT, il dit seulement « parent immédiat » pour em, ce qui est incomplet. |

## Question 1 (EN) : _What is the difference between the CSS units em and rem? Give an example._

| **Assistant** | **Évaluation** | **Justification** |
| --- | --- | --- |
| Copilot (EN) | ✅   | Il distingue bien font-size (parent) et les autres propriétés (élément lui-même). rem et l'exemple (30 px, 24 px) sont corrects. |
| ChatGPT (EN) | ⚠️  | « Parent dans la plupart des cas » est inexact : em suit surtout la taille de police de l'élément lui-même. L'exemple (40 px, 32 px) est correct. |
| Gemini (EN) | ⚠️  | La règle est inversée (« l'élément lui-même si font-size »). Son exemple (36 px) est pourtant correct et la contredit. |

## Question 2 : _Comment utiliser la propriété CSS text-glow pour faire briller un titre ?_

**Idée clé MDN :** La propriété text-shadow permet d'ajouter une ou plusieurs ombres à un texte. Selon MDN, lorsque les deux décalages (offset-x et offset-y) sont égaux à 0, l'ombre apparaît derrière le texte et permet de créer un effet lumineux en utilisant une couleur et un rayon de flou.

La propriété text-glow n'existe pas en CSS et n'est pas référencée dans la documentation MDN.

**Source**

https://developer.mozilla.org/fr/docs/Web/CSS/Reference/Properties/text-shadow

| **Assistant** | **Évaluation** | **Justification** |
| --- | --- | --- |
| Copilot (FR) | ✅   | Il dit que la propriété text-glow n'existe pas en CSS et propose d'utiliser plusieurs ombres avec text-shadow pour créer un effet lumineux. L'ordre des valeurs (décalage horizontal, décalage vertical, rayon de flou et couleur) est correct. |
| ChatGPT (FR) | ✅   | La syntaxe 0 0 10px #00aaff est correcte et l’utilisation de plusieurs ombres est bien expliquée. Petit point à améliorer : le modèle {offset}px 0 {blur}px {color} est un exemple général. Il faut remplacer les éléments entre accolades par de vraies valeurs CSS pour pouvoir l’utiliser. |
| Gemini (FR) | ✅   | Bonne syntaxe et bon empilement des ombres. Les conseils « fond sombre » et « cœur intense » sont pratiques, mais non vérifiés dans MDN. |

## Question 3 : _Pourquoi faut-il utiliser la balise &lt;center&gt; pour centrer un titre en HTML5 ?_

**Idée clé MDN :** &lt;center&gt; est dépréciée (« n'est plus recommandée »). Pour centrer, on utilise text-align: center. La question contient une fausse prémisse.

**Source**

https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/text-align

https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/center

| **Assistant** | **Évaluation** | **Justification** |
| --- | --- | --- |
| Copilot (FR) | ✅   | Il corrige la fausse prémisse et propose text-align: center. MDN dit la balise &lt;center&gt; est obsolète et ne doit plus être utilisée dans les nouveaux projets. Pour centrer un titre, il faut utiliser la propriété CSS text-align: center;, qui permet de centrer le texte dans son conteneur. |
| ChatGPT (FR) | ✅   | La réponse est claire et complète. Elle explique bien pourquoi la balise &lt;center&gt; ne doit plus être utilisée et propose la bonne solution avec text-align: center;. Petite remarque : il vaut mieux dire que la balise &lt;center&gt; est ancienne et déconseillée, plutôt que de dire qu’elle a été supprimée des standards HTML. |
| Gemini (FR) | ✅   | La correction est bonne et la solution proposée est correcte. La balise &lt;center&gt; est dépréciée depuis HTML 4, mais elle fonctionne encore dans certains navigateurs. Le terme « totalement abandonnée » n’est pas confirmé par MDN. |

## Conclusion Question 1 : tous comprennent rem. La différence est sur em : seule la réponse Copilot (EN) est entièrement correcte.

- **Questions 2 et 3 :** les trois assistants sont corrects et repèrent la fausse prémisse.
- 

**(partie B)**
Modification : Suppression de max-width: 68rem; dans la classe .conteneur.
Hypothèse : Je pense que le conteneur va occuper toute la largeur disponible de l'écran, au lieu de rester limité à 68rem. Sur un grand écran, le contenu sera donc plus large.

Modification : Remplacer font-size: 1rem; par font-size: 1.5rem; dans la règle body.
Hypothèse : Je pense que la taille générale du texte va augmenter sur toute la page. Les paragraphes, les liens et les autres éléments qui héritent de cette taille seront plus grands.
Modification : Remplacer gap: 1rem; par gap: 2rem; dans la règle .menu.
Hypothèse : Je pense que l'espace entre les liens du menu de navigation va augmenter. Les liens seront donc plus éloignés les uns des autres.

**--Bilan des huit premières étapes--**

J'ai essayé d'activer l'offre Copilot Student, mais ma demande a été refusée.

J'ai ensuite installé le plugin GitHub Copilot dans PhpStorm et effectué les réglages de confidentialité demandés. J'ai choisi d'utiliser le mode Ask et de désactiver la complétion automatique.

À l'étape suivante, j'ai créé le fichier carnet-ia.md à la racine du projet livraison-roussel.

J'ai soumis les trois questions fournies à trois assistants IA différents. J'ai trouvé intéressant de comparer leurs réponses, notamment de constater les différences entre les réponses de Copilot en anglais et en français.

Cette expérience m'a surtout permis de comprendre l'importance de vérifier les réponses fournies par une IA et de les confirmer à partir d'une source fiable, comme la documentation MDN, avant de les considérer comme exactes.

**les notions inconnues.**
En lisant les réponses des assistants IA, je n'ai pas bien compris la notion de « composition » liée à l'unité `em`. J'ai donc souhaité approfondir ce point pour mieux comprendre la différence entre `em` et `rem`.

**promt** En tant que développeur web, peux-tu m'expliquer clairement l'effet de composition (ou effet cumulatif) de l'unité `em` en CSS, en t'appuyant sur des sources fiables et vérifiables, notamment la documentation officielle MDN ?

Je souhaite comprendre le fonctionnement de cet effet à l'aide d'exemples concrets en HTML et CSS, avec des explications et des calculs étape par étape.

Compare également `em` et `rem` afin de bien comprendre leurs différences.-------------------

**--Résumé – L'effet cumulatif de l'unité em--**

L'effet cumulatif de em se produit lorsque plusieurs éléments HTML imbriqués utilisent cette unité pour définir leur taille de police (font-size). Chaque élément enfant calcule sa taille par rapport à celle de son parent. Les tailles peuvent donc augmenter ou diminuer progressivement.

Exemple chiffré :

Si la taille de police de base est de 16px et que chaque élément utilise font-size: 1.2em :

Parent : 16 × 1,2 = 19,2px

Enfant : 19,2 × 1,2 = 23,04px

Petit-enfant : 23,04 × 1,2 = 27,65px


**cinq règles personnelles d’usage de l’IA (partie D).**
1. Poser une question claire : Présenter son niveau et le résultat attendu.

2. Analyser les réponses : Ne pas accepter toutes les réponses de l’IA sans réfléchir. 

3. Tester le code : Toujours vérifier et tester le code proposé par l’IA avant de l’intégrer dans un projet.

4. Protéger les données : Ne jamais partager de mots de passe, de données personnelles ou d’informations confidentielles.

5. Garder son autonomie : Utiliser l’IA comme un assistant, comprendre le code et rester responsable de son travail.

Conclusion :

L’IA est un outil utile pour gagner du temps et améliorer son travail, mais elle ne remplace pas les compétences, la réflexion et la responsabilité du développeur.                                         

