# 📋 EXEMPLES — Référence syntaxe SCSS

> Ce fichier contient uniquement des syntaxes de référence.

## Fonctions

```scss
@function rem($px) {
  @return $px / 16px * 1rem;
}

// Fonction native
color: lighten(#3498db, 10%);
color: darken(#3498db, 10%);
color: rgba(#3498db, 0.5);
```

---

## Collections

### List

```scss
$tailles: 8px, 16px, 24px, 32px;

// Accès par index (commence à 1)
$premiere: nth($tailles, 1); // 8px
$longueur: length($tailles); // 4
```

### Map

```scss
$couleurs: (
  'primaire': #3498db,
  'secondaire': #2ecc71,
  'danger': #e74c3c,
);

// Accès
$c: map-get($couleurs, 'primaire');
```

---

## Boucles

### @for

```scss
// De 1 à 4 (inclus)
@for $i from 1 through 4 {
  .col-#{$i} {
    width: 25% * $i;
  }
}
```

### @each

```scss
// Sur une liste
$couleurs: rouge, bleu, vert;

@each $couleur in $couleurs {
  .texte-#{$couleur} {
    color: $couleur;
  }
}

// Sur une map
$icones: (
  'home': '🏠',
  'user': '👤',
);

@each $nom, $icone in $icones {
  .icon-#{$nom}::before {
    content: $icone;
  }
}
```

---

## Conditions

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
