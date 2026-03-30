# 1. Informations

## SCSS, qu'est-ce que c'est ?

SCSS ou SASS sont des préprocesseurs. C'est comme du css classique, à quelques différences près. En SCSS on va avoir des options en plus du css normal, on va avoir des variables, des mixins, des fonctions, des list/map, boucles etc.

## Pourquoi l'utiliser ?

Le SCSS, l'utiliser c'est l'adopter. Il nous simplifie la vie par plusieurs choses :

- L'imbrication du code :
  - Plutôt que de devoir répéter à chaque fois les mêmes classes/type de section, on peut directement l'imbriquer dans la grande section.

  - Cela permet également une plus grande lisibilité du code (possibilité de réduire directement toute la classe plutôt que de devoir réduire un à un les morceaux de code)

```scss
.nav {
	position: fixed;
	&__links {
		text-decoration: none;
	}
}
```

- Gain de temps garanti :
  - Avec les variables, mixins, fonctions et autres fonctionnalités du SCSS, on gagne un temps fou à ne pas être obligé de changer chaque couleur, chaque typo, chaque taille de texte (ou même un bloc de code complet) à la main, on change une seule fois et le tour est joué. (Exemples à suivre dans les différentes parties)

# 2. Méthode BEM

## Qu'est-ce que la méthode BEM ?

La méthode BEM (Bloc\_\_Element--Modifier) est une convention de nommage en SCSS.
En effet, elle demande aux développeurs qui l'utilisent de suivre une certaine façon de coder. Un bloc sera une "section", une nav par exemple, puis un element sera une partie de cette nav, un lien par exemple, et enfin le modifier sera quelque chose qui permet de savoir si l'élément/le bloc est modifié d'une quelconque manière, par exemple --active pour une card ou autre chose du style.

```scss
.nav {
	position: fixed;

	&__link {
		text-decoration: none;
	}
}

.card {
	display: none;

	&--active {
		display: block;
	}
}
```

## Pourquoi l'utiliser ?

Cette méthode est très utile pour les projets à plusieurs, en suivant cette **convention de nommage**, on est sûrs que tout le monde va se repérer de la même manière dans le code et que par conséquent ça limitra le manque de compréhension entre chaque partie (et ça évite également d'écraser du code existant car en suivant cette méthode il ne peut pas y avoir deux éléments avec exactement les mêmes classes/id)

# 3. Préprocesseurs

## Qu'est-ce qu'un préprocesseur ?

Un préprocesseur (comme SCSS ou SASS) c'est un peu comme du css mais avec des super-pouvoirs, c'est globalement du css mais avec des mixins, fonctions, boucles etc (comme dit dans la partie Informations).

Le plus important à retenir c'est qu'un navigateur ne **peut pas** interpréter du SCSS, c'est pour cela que le préprocesseur va derrière compiler le SCSS en CSS classique pour que le navigateur puisse le lire et l'ajouter à la page.

# 4. Installation

## NPM

Pour installer un préprocesseur comme SASS il vous suffit de taper quelques commandes dans le terminal de votre projet.

### Tout d'abord vérifier que vous avez node et npm d'installer

```bash
node -v
npm -v
```

Si ils ne sont pas installés, allez sur le site officiel de node.js pour installer tout ça.

### Ensuite, une fois dans le dossier de votre projet, vous allez faire quelques commandes pour initialiser npm

```bash
npm init -y
# ou
npm init
```

Le -y sert uniquement à passer les demandes dans le terminal pour les valeurs (name etc)

### Pour finir, on installe sass localement pour le projet

```bash
npm i sass
```

## Package manager

Suite à l'installation, vous aurez un fichier package.json.

Rendez vous dans ce fichier et modifier cette ligne :

```json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```

Par :

```json
"scripts": {
    "build": "sass --watch assets/sass:assets/css"
  },
```

Ainsi, quand vous lancerez la commande :

```bash
npm run build
```

Votre SCSS se compilera tout seul à chaque changement en CSS.

Vous pouvez également le faire à la main à chaque changement avec la commande :

```bash
sass assets/scss:assets/css
```

Mais ça prendra plus de temps que de le faire automatiquement.

# 5. Architecture 7-1

Pour que la dernière partie fonctionne il va falloir suivre cette architecture comme elle suit.

```
mon-projet/
└── assets/
    └── sass/
        ├── base/
        ├── utils/
        ├── layout/
        ├── components/
        ├── pages/
        ├── themes/
        └── vendors/
        main.scss
```

Si vous changez le nom du dossier sass par autre chose, il faut le changer également dans le package.json à la ligne build :

```json
"scripts": {
    "build": "sass --watch assets/sass:assets/css"
  },
```

Vous l'aurez compris, 7-1 veut dire 7 dossiers - 1 fichier principal.

# 6. Syntaxe SCSS

La syntaxe SCSS est assez simple, elle ne change pas beaucoup de celle du CSS classique.

Les points importants à noter sont :

- Ne pas oublier les @ devant les directives.
  - @use, @for (pareil pour les autres boucles), @mixin etc.
- Ne pas oublier les $ devant les variables, sinon ça ne marche pas.
- Ne pas oublier les & devant les \_\_ ou -- etc des appels imbriqués (exemple dans la partie 2. Méthode BEM)

# 7. Les variables

## Qu'est-ce qu'une variable ?

Une variable, que ce soit en SCSS ou dans n'importe quel langage de code, est une valeur que l'on place dans un "contenant" nommé comme on le souhaite qui, comme son nom l'indique, peut varier.

Il faut noter une chose importante :

- La variable **DOIT** être précédé d'un $.

```scss
$rouge: red;

.error {
	color: $rouge;
}
```

## Mais à quoi ça sert ?

Les variables servent à plusieurs choses, dedans on peut stocker plus ou moins ce qu'on veut :

- Couleur
- Taille de police
- Épaisseur de police

Et bien d'autres encore.

L'utilité derrière les variables c'est que, si un jour on veut changer toute la DA du site, plutôt que de devoir changer ligne par ligne là où on a nos couleurs, on doit juste changer la couleur de la variable ce qui prend quelques secondes là où tout changer à la main peut prendre des heures entières (si le site est très connue genre amazon on atteint vite des milliers/dizaines de milliers de lignes de code).

# 8. Les mixins

## Qu'est-ce qu'un mixin ?

Un mixin en SCSS c'est l'équivalent d'un "template" de code.

C'est un patern qu'on va créer avec un nom qui nous permet de l'appeler quand on veut pour éviter d'écrire plusieurs fois les mêmes lignes et gagner du temps/des lignes de code.

En général il est utilisé pour des paterns communs (centrer un élément, faire des cards identiques à peu de choses près etc)

Pour créer un mixin on utilise le @mixin, et pour l'appeler on utilise le @include.

```scss
@mixin flex-center {
	display: flex;
	justify-content: center;
	align-items: center;
}

.cards {
	@include flex-center;
}
```

Il y a quand même une petite particularité avec les mixins, on peut leur donner des paramètres pour changer quelques éléments facilement (une couleur, une direction d'éléments, une typo etc)

```scss
@mixin flex-center($direction) {
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: $direction;
}

.cards {
	@include flex-center(column);
}
```

Ici par exemple, nos cards seront en colones grâce à cet argument.

Voici un exemple concret de l'utilisation des mixins (qui ici ne sert à rien car toutes de la même couleur)

[image code cards](./code.png)

# 9. Les fonctions

## Qu'est-ce qu'une fonction ?

En SCSS une fonction n'est pas bien différente des autres langages, elle renvoie une valeur.

Sa syntaxe est assez simple, elle commence par @function puis on lui donne un nom est un/des paramètre(s) et enfin on écrit à l'intérieur des accolades la fonction sans oublier le @return qui est très important.

Pour l'appeler ce n'est pas plus compliqué, on appelle le nom de la fonction et entre parenthèses son/ses paramètre(s).

```scss
@function double($n) {
	@return $n * 2;
}
.box {
	width: double(10px);
} 
```

**ATTENTION !**  Il ne faut pas confondre fonction et mixin, une fonction renvoie une valeur et une mixin injecte du code.

# 10. Les collections

## Qu'est-ce qu'une Collection ?

Une collection c'est un ensemble de plusieurs valeurs stocké dans une seule variable.

Et en SCSS il y a deux principaux types de collections, les listes et les maps.

### C'est quoi une liste ?

Une liste c'est une suite de valeur sans clé, juste stockée comme ça.

L'ordre est donc important pour s'y retrouver !

Et pour y accéder on utilise nth().

```scss
$colors: red, blue, green;

.sky {
    background: nth($colors, 2);
}
```

Ce code va mettre le background de la classe sky en bleu (car oui, les listes en scss commencent à 1 pas à 0).

Et on peut combiner les listes avec les variables !

```scss
$blue: blue;
$red: red;
$green: green;

$colors: $red, $blue, $green;

.sky {
    background: nth($colors, 2);
}
```

### C'est quoi une map ?

Une map c'est une suite avec clé et valeur, ce qui ressemble beaucoup à un dictionnaire.

On y accède avec map-get()

```scss
$colors: (primary: blue, secondary: red);

.sky {
    background: map-get($colors, primary);
}
```

Ce code va mettre le background de la classe sky en bleu car on appelle la clé primary dont la valeur est "blue".

Et on peut combiner les map avec les variables aussi !

```scss
$blue: blue;
$red: red;
$green: green;

$colors: (primary: $blue, secondary: $red);

.sky {
    background: map-get($colors, primary);
}
```

On peut également combiner les collections avec des boucles ce qui permet par exemple, comme tout à l'heure, de changer les couleurs des cards au fur et à mesure de la boucle qui parcourt la map/list.

# 11. Les boucles

## Qu'est-ce qu'une boucle ?

Les boucles en SCSS permettent de générer du CSS automatiquement. @for est utilisé pour un nombre précis, @each pour parcourir une liste ou une map, et @while pour une condition.

### @for (boucle avec compteur)

Quand on connait le nombre de répétitions, on utilise le @for

```scss
@for $i from 1 through 3 {
  .box-#{$i} {
    width: 10px * $i;
  }
}


.box-1 { width: 10px; }
.box-2 { width: 20px; }
.box-3 { width: 30px; }
```

On peut aussi utiliser to au lieu de through, to exclut la fin et through l'inclus (ici c'est de 1 à 3 inclus)

### @each (boucle sur collection)

On l'utilise quand on parcourt une collection

Avec liste

```scss
$colors: red, blue, green;

@each $color in $colors {
  .text-#{$color} {
    color: $color;
  }
}
```

Avec map

```scss
$colors: (
  primary: blue,
  danger: red
);

@each $name, $color in $colors {
  .btn-#{$name} {
    background: $color;
  }
}
```

Quand on utilise les listes on fait une seule variable et quand on utilise une map on fait clé + valeur.

### @while (boucle condition)

On l'utilise pour boucler quand une condition est toujours vraie

```scss
$i: 1;

@while $i <= 3 {
  .item-#{$i} {
    width: 10px * $i;
  }
  $i: $i + 1;
}
```

Ici, tant que la variable i est inférieur ou égale à 3, on fait une interpolation sur la classe item (on crée le scss pour la classe item-1, item-2 et item-3) et pour éviter la boucle infinie, on incrémente i de 1 à chaque exécution.

# 12. Multi-fichiers

## Qu'est-ce que les multi-fichiers ?

Le système multi-fichiers permet d’organiser le code SCSS en plusieurs fichiers partiels. On utilise @use pour importer un fichier et @forward pour regrouper plusieurs fichiers dans un seul point d’entrée.

Si tout est dans le même fichier, c'est illisible alors que si on découpe c'est beaucoup plus clair et compréhensible.

### @use

Par exemple, dans style.scss :

```scss
@use 'index';

.button {
  color: index.$primary;
}
```

Ici on peut donc utiliser la variable $primary qui se trouve dans le fichier index.

### @forward

Par exemple dans _index.scss : 

```scss
@forward 'variables';
@forward 'mixins';
```

Ici on regroupe les fichiers variables et mixins dans le fichier index (donc la variable récupérée par le @use juste avant est récupérée de index qui lui même la récupère dans variables)

# 13. Conditions

## Qu'est-ce que les conditions ?

Une condition en SCSS est basée sur le même principe que les conditions dans les autres langages. Elle renvoie si elle est vraie ou fausse et en fonction, elle exécute le code qu'elle contient ou elle passe à la condition suivante/le code qui suit s'il n'y a pas d'autre condition.

```scss
@mixin theme($mode) {
  @if $mode == 'dark' {
    background: #1a1a1a;
    color: white;
  } @else if $mode == 'light' {
    background: white;
    color: #1a1a1a;
  } @else {
    background: grey;
  }
}
```

Ici on a un exemple de chaque condition, le @if qui vérifie donc juste si la variable $mode est égale à 'dark', si c'est vrai le background passe en noir et la couleur du texte en blanc.

Le @else if c'est si la première condition n'est pas vraie on vérifie celle ci (ça évite la répétition de if consécutifs), donc si la variable $mode est égale à 'light' on passe le background en blanc et le texte en noir.

Enfin, le @else dit, si aucune des autre conditions n'est vraie on met le background en gris.