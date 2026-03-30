# 1. Informations

## SCSS, qu'est-ce que c'est ?

SCSS ou SASS sont des préprocesseurs. C'est comme du css classique, à quelques différences près. En SCSS on va avoir des options en plus du css normal, on va avoir des variables, des mixins, des fonctions, des list/map, boucles etc.

## Pourquoi l'utiliser ?

Le SCSS, l'utiliser c'est l'adopter. Il nous simplifie la vie par plusieurs choses :

- L'imbrication du code :
- Plutôt que de devoir répéter à chaque fois les mêmes classes/type de section, on peut directement l'imbriquer dans la grande section.
<pre>

```scss
.nav {
	position: fixed;
	&__links {
		text-decoration: none;
	}
}
```

 </pre>

- Cela permet également une plus grande lisibilité du code (possibilité de réduire directement toute la classe plutôt que de devoir réduire un à un les morceaux de code)

- Gain de temps garanti :
- Avec les variables, mixins, fonctions et autres fonctionnalités du SCSS, on gagne un temps fou à ne pas être obligé de changer chaque couleur, chaque typo, chaque taille de texte (ou même un bloc de code complet) à la main, on change une seule fois et le tour est joué. (Exemples à suivre dans les différentes parties)

# 2. Méthode BEM

## Qu'est-ce que la méthode BEM ?

La méthode BEM (Bloc\_\_Element--Modifier) est une convention de nommage en SCSS.
En effet, elle demande aux développeurs qui l'utilisent de suivre une certaine façon de coder. Un bloc sera une "section", une nav par exemple, puis un element sera une partie de cette nav, un lien par exemple, et enfin le modifier sera quelque chose qui permet de savoir si l'élément/le bloc est modifié d'une quelconque manière, par exemple --active pour une card ou autre chose du style.

<pre>
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
</pre>

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

<pre>
``` bash
node -v
npm -v
```
</pre>

Si ils ne sont pas installés, allez sur le site officiel de node.js pour installer tout ça.

### Ensuite, une fois dans le dossier de votre projet, vous allez faire quelques commandes pour initialiser npm

<pre>
``` bash
npm init -y
ou
npm init
```
</pre>

Le -y sert uniquement à passer les demandes dans le terminal pour les valeurs (name etc)


### Pour finir, on installe sass localement pour le projet

<pre>
``` bash
npm i sass
```
</pre>

## Package manager

Suite à l'installation, vous aurez un fichier package.json.

Rendez vous dans ce fichier et modifier cette ligne :

<pre>
```json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
```
</pre>

Par :

<pre>
```json
"scripts": {
    "build": "sass --watch assets/scss:assets/css"
  },
```
</pre>

Ainsi, quand vous lancerez la commande :

<pre>
```bash
npm run build
```
</pre>

Votre SCSS se compilera tout seul à chaque changement en CSS.

Vous pouvez également le faire à la main à chaque changement avec la commande :

<pre>
```bash
sass assets/scss:assets/css
```
</pre>

Mais ça prendra plus de temps que de le faire automatiquement.