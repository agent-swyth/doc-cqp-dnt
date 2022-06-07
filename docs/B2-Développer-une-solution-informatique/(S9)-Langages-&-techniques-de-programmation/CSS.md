# Apprendre CSS

> Ce support de cours (et mémo) est inspiré directement du cours "Learn CSS" de [Codecademy](https://www.codecademy.com/learn/learn-css)
> 
## **Syntaxe et Usage**

### **Anatomie du CSS** 
Ici sont définis les termes principaux qui nous permettent de comprendre comment une règle CSS est formulée :

![CSS Anatomy](images/css-anatomy.png)

- Un **sélecteur** permet de cibler l'élément qu'on souhaite styliser
- Le **bloc de déclaration** se site entre les accolades `{}` et contient les déclarations CSS
- La **déclaration** est un groupe de propriétés et valeurs CSS qui vont s'appliquer à l'élément pour le styliser
- La **propriété** est la première partie d'une déclaration qui signifie quelle caractéristiques visuelle est modifiée
- La **valeur** est la deuxième partie de la déclaration qui signifie comment est modifiée la caractéristique visuelle

### "**Inline Styles**" & Feuille de Style **Interne** / **Externe**

Il est possible d'écrire directement dans le fichier `HTML` des règles CSS. C'est ce qu'on appelle l'**inline style**. C'est une manière rapide de styliser un élément HTML : 

```html
<p style='color: red;'>I'm learning to code!</p>
<p style='color: red; font-size: 20px;'>I'm learning to code!</p>
```

Cette manière n'est pas le meilleur moyen d'écrire des règles CSS.

HTML nous autorise à écrire du code CSS dans une section dédiée du , avec l'élément ``<style>`` inséré dans l'élément ``head`` du document ``.html``. C'est la **feuille de style interne** (**internal stylesheet**): 

```html
<head>
  <style>
    p {
      color: red;
      font-size: 20px;
    }
  </style>
</head>
```

Il vaut mieux éviter de mélanger le code HTML avec le code CSS. Pour cela, nous créons une (ou des) **feuille de style externe** (external stylesheet) avec l'extension de fichier ``.css`` : ``styles.css`` :

```css
p {
color: green;
}
```

De cette manière, nous pouvons écrire autant de code CSS sans sacrifier la **lisibilité** et la **maintenabilité** de nos fichiers ``html``

### Lien vers le fichier CSS 

En séparant notre code CSS de notre code HTML, notre fichier HTML ne sait pas où se trouve la feuille de style. Il faut lui "linker" ou lui spécifier.
Pour cela, nous utilisons l'élément HTML ``<link>`` inséré dans l'élélement ``<head>`` du fichier:

```html
<head>
    <link href='https://www.codecademy.com/stylesheets/style.css' rel='stylesheet'>
    <link href='./style.css' rel='stylesheet'>
</head>
```

- ``href`` est l'atribut qui spécifie l'adresse ou le chemin vers le fichier CSS
- ``rel`` spécifie la relation entre le fichier HTML et le fichier CSS. Vu que ce lien mène vers une feuille de style, nous spéficions ``stylesheet``

## **Sélecteurs** 

CSS peut sélectionner les éléments HTML par **[type](https://developer.mozilla.org/fr/docs/Web/CSS/Type_selectors)**, **[classe](https://developer.mozilla.org/fr/docs/Web/HTML/Global_attributes/class)**, **[ID](https://developer.mozilla.org/fr/docs/Web/API/Element/id)** et **[attribut](https://developer.mozilla.org/fr/docs/Web/CSS/Attribute_selectors)**

```css
a {
    
}

.nav-link {

}

#specific-id {

}

a[href*='florence'] {
  color: lightgreen;
}


```

Tous les éléments peuvent être sélectionnés par le [**sélecteur universel**](https://developer.mozilla.org/fr/docs/Web/CSS/Universal_selectors) 

```css
* {
    border: 1px solid red;
}
```

!!! tip

    Lors de votre développement d'interface, vous pouvez configurer cet attribut universel pour visualiser la disposition des éléments HTML. 

### **Comportement de l'élément**

Un élément peut avoir différent état en utilisant le [**sélecteur de pseudo-classe**](https://developer.mozilla.org/fr/docs/Web/CSS/Pseudo-classes)

```css
/* :hover permet de spécifier l'apparence d'un élément au moment où l'utilisateur le survole avec le pointeur, sans nécessairement l'activer */
a:hover {
    color:darkorange;
}
```

### **Classes d'élément**

Plusieurs classes CSS peuvent être appliquées à un même élément HTML

```html
<a class="article external-link third-classe ...">
```

### **ID d'élément**
Les classes peuvent être réutilisées, tandis que les ID ne peuvent utilisés qu'une seule fois

```html
<a class="article external-link third-classe ...">
    <h5 id="first-title"></h5>
<a class="article external-link third-classe ...">
    <h5 id="second-title"></h5>
```

### **Spécificité**

> [**Specificity**](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) refers to how a browser decides which styles to display when there are multiple styles defined that could apply to the same element.

Les ID sont plus spécifique que les classes. Et les classes sont plus spécifiques qu'un type d'élément. 
Les conséquences sont que **les ID peuvent écraser les styles d'une classe** et **les classe speuvent écraser les styles d'un élément**

```css
a {
    color:darkorange;
}

.external-link {
    color:red;
}

#specific-id {
    color:deeppurple;
}
```

### **Chaînage**

Plusieurs sélecteurs peuvent être **chaînés** ensemble pour sélectionner un élement. Cela augmente la spécificité mais peut être nécessaire pour le cibler précisemment.

```css
a.external-link {
    color: cadetblue,
}
```

### **Eléments imbriqués**
Les éléments imbriqués peuvent être sélectionnés en séparant les sélecteurs d'un espace : 
 
```css
a h4 {
    color: cadetblue,
}
```

### **Groupement**
Plusieurs sélecteurs (n'ayant pas forcément de lien) peuvent être groupé en les séparant d'une virgule `,`

```css
h1,
h2 {
    color: blueviolet,
}
```

## Règles visuelles

> L'objectif de CSS est d'ajouter du style aux pages Web, et chaque élément de la page peut avoir de nombreuses propriétés de style. Certaines des propriétés de base concernent la taille, le style et la couleur de l'élément.

### **Famille de police**

Vous pouvez modifier la famille de police d'un élément comme ceci : 

```css
h1 {
  font-family: Garamond;
}
```

Lorsque nous définissons une pollièce de caractères sur une page web, plusieurs points sont à retenir :

- La police spécifiée doit être installée sur l'ordinateur ou dans le navigateur (téléchargée avec le site)
- Les **polices sûres** sont un groupe de polices prises en charge sur la plupart des navigateurs et systèmes d'exploitation
- A moins d'utiliser des polices sûres, votre **police spécialement choisie** peut ne pas apparaître de la même manière sur tous les support (navigateurs, systèmes d'exploitation)
-  Lorsque le nom d'une police est composé de plusieurs mots, il est préférable de l'écrire en guillement `'` comme-suit : `font-family: 'Courier New';`

### **Taille de police**

Selon les besoins, plusieurs section d'une page peuvent 















## Affichage et Positionnement


## Couleurs

## Typographie