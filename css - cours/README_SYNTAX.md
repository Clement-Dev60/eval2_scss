# 📖 README_SYNTAX — La syntaxe Markdown expliquée

> Tout ce dont tu as besoin pour mettre en forme tes fichiers README comme un pro.

---

## Titres

```md
# Titre niveau 1
## Titre niveau 2
### Titre niveau 3
#### Titre niveau 4
```

---

## Texte

```md
**Texte en gras**
*Texte en italique*
~~Texte barré~~
`code inline`
```

**Rendu :**
**Texte en gras** | *Texte en italique* | ~~Texte barré~~ | `code inline`

---

## Listes

```md
- Élément
- Élément
  - Sous-élément (2 espaces)

1. Premier
2. Deuxième
3. Troisième
```

---

## Bloc de code

<pre>
```scss
$ma-variable: 16px;
```

```html
<div class="card"></div>
```

```bash
npm install sass
```
</pre>

> Remplace `scss`, `html`, `bash` par le langage que tu veux pour la coloration syntaxique.

---

## Liens cliquables

```md
[Texte du lien](https://example.com)
```

**Vers un autre fichier README dans le même dossier :**

```md
[Voir les exemples](./EXEMPLES.md)
[Voir le chapitre variables](./chapitres/variables.md)
```

**Vers une section dans le même fichier :**

```md
[Aller à la section Variables](#les-variables)
```

> ⚠️ Pour les ancres, tout en minuscules, les espaces remplacés par `-`, les accents et caractères spéciaux supprimés.
> Exemple : `## Les Mixins` → `#les-mixins`

---

## Images

```md
![Texte alternatif](./images/mon-image.png)
```

**Avec une taille personnalisée** *(HTML dans le Markdown)* :

```md
<img src="./images/mon-image.png" alt="Description" width="600" />
```

> 💡 Pour capturer ton code proprement → [CodeSnap](https://marketplace.visualstudio.com/items?itemName=adpyke.codesnap) (extension VS Code)
> 💡 Pour créer des schémas → [Excalidraw](https://excalidraw.com) puis export en `.png`

---

## Tableaux

```md
| Colonne 1 | Colonne 2 | Colonne 3 |
|---|---|---|
| Valeur A | Valeur B | Valeur C |
| Valeur D | Valeur E | Valeur F |
```

**Rendu :**

| Colonne 1 | Colonne 2 | Colonne 3 |
|---|---|---|
| Valeur A | Valeur B | Valeur C |
| Valeur D | Valeur E | Valeur F |

**Alignement :**

```md
| Gauche | Centre | Droite |
|:---|:---:|---:|
| texte | texte | texte |
```

---

## Bloc citation / note

```md
> Ceci est une citation ou une note importante.
> Elle peut s'étendre sur plusieurs lignes.
```

**Rendu :**
> Ceci est une citation ou une note importante.

---

## Séparateur horizontal

```md
---
```

---

## Organiser en plusieurs fichiers

Tu peux découper ton tuto en plusieurs fichiers et les relier entre eux :

```
mon-tuto/
├── README.md           ← page d'accueil / sommaire
├── 01-bem.md
├── 02-variables.md
├── 03-mixins.md
└── images/
    ├── schema-bem.png
    └── archi-7-1.png
```

**Dans ton README.md (sommaire) :**

```md
## Sommaire

1. [La méthode BEM](./01-bem.md)
2. [Les variables](./02-variables.md)
3. [Les mixins](./03-mixins.md)
```

**En bas de chaque fichier pour naviguer :**

```md
---
[⬅ Précédent : BEM](./01-bem.md) | [Suivant : Mixins ➡](./03-mixins.md)
```

---

## Checkbox (liste de tâches)

```md
- [x] Tâche faite
- [ ] Tâche à faire
```

---

## Emoji

Colle directement un emoji dans ton texte, ça marche dans les README :

```md
💡 Astuce : ...
⚠️ Attention : ...
✅ Bonne pratique
❌ À éviter
```

---

*Bonne rédaction ! 🚀*
