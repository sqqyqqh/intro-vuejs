# Initiation au framework Vue.js

_Vue.js est l'un des frameworks JavaScript les plus populaires pour créer des applications web interactives. Dans ce tutoriel, nous allons couvrir les bases de Vue.js, en partant des prérequis nécessaires pour l'utiliser jusqu'à la création d'une application web complète. Chaque jour, nous couvrirons un nouveau sujet et inclurons des exemples pratiques pour vous aider à comprendre comment Vue.js fonctionne._

Vue.js est un framework JavaScript qui a été développé pour créer des interfaces utilisateur interactives et réactives. Il utilise un modèle de composant qui facilite la création d'applications modulaires. Les composants sont des blocs autonomes de code qui peuvent être facilement réutilisés dans différentes parties de votre application.

Vue.js est souvent comparé à d'autres frameworks JavaScript populaires comme React et Angular. Contrairement à React, Vue.js a une courbe d'apprentissage plus douce et offre des fonctionnalités intégrées pour la gestion de l'état et la gestion des événements. Contrairement à Angular, Vue.js est plus léger et plus facile à utiliser.
Jour 3 : Installation de Vue.js

Il existe plusieurs façons d'installer Vue.js dans votre projet. La méthode la plus simple consiste à utiliser un CDN (Content Delivery Network) pour charger la bibliothèque Vue.js depuis un serveur tiers. Voici un exemple de code HTML pour charger Vue.js depuis un CDN :

``` html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Ma première application Vue.js</title>
  </head>
  <body>
    <div id="app">
      {{ message }}
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    <script>
      var app = new Vue({
        el: '#app',
        data: {
          message: 'Bonjour Vue !'
        }
      })
    </script>
  </body>
</html>
```

Cela chargera la bibliothèque Vue.js depuis un serveur tiers et initialisera une instance Vue qui affiche un message dans la balise div avec l'ID app.

Alternativement, vous pouvez installer Vue.js à l'aide de Node.js et npm (Node Package Manager). Cela vous permettra de gérer les dépendances de votre projet et de créer des applications plus avancées à l'aide d'outils tels que webpack. Voici comment installer Vue.js à l'aide de npm :

```bash
npm install vue
```

## Création de votre première instance Vue

Pour créer une instance Vue, vous devez appeler la fonction Vue() et passer un objet de configuration. Voici un exemple de code pour créer une instance Vue de base JavaScript :

```javascript
var app = new Vue({
  el: '#app',
  data: {
    message: 'Bonjour Vue !'
  }
})
```

Dans cet exemple, nous créons une instance Vue et la connectons à l'élément avec l'ID app. Le data est un objet qui contient les données que nous souhaitons rendre réactives dans notre application. Ici, nous avons défini une propriété message qui contient la chaîne de caractères "Bonjour Vue !".

Nous pouvons ensuite afficher cette donnée dans notre HTML en utilisant une syntaxe de balisage appelée "interpolation". Voici comment afficher le message dans notre HTML :

```html
<div id="app">
  {{ message }}
</div>
```

Lorsque Vue.js crée l'instance, il recherche l'élément avec l'ID app et remplace son contenu par la valeur de message. Si vous ouvrez cette page dans votre navigateur, vous devriez voir "Bonjour Vue !" affiché dans la fenêtre du navigateur.

## Directives Vue.js

Les directives Vue.js sont des attributs spéciaux que vous pouvez ajouter à vos éléments HTML pour leur donner des comportements réactifs. Les directives commencent toutes par le préfixe "v-". Voici quelques exemples de directives Vue.js courantes :

- v-if : affiche un élément HTML uniquement si une condition est vraie
- v-for : itère sur une liste d'éléments et crée des éléments HTML pour chacun d'eux
- v-bind : lie une propriété de l'instance Vue à un attribut HTML
- v-on : écoute un événement HTML et appelle une méthode de l'instance Vue

Voici un exemple d'utilisation de la directive v-if :

```html
<div id="app">
  <p v-if="showMessage">Bonjour Vue !</p>
  <button v-on:click="toggleMessage">Afficher / Masquer le message</button>
</div>
```

Dans cet exemple, nous avons ajouté une nouvelle propriété showMessage à notre objet data, qui est initialisée à true. Nous avons également ajouté un bouton qui appelle une méthode toggleMessage lorsqu'il est cliqué. Cette méthode inverse la valeur de showMessage, ce qui rendra l'élément p visible ou invisible en fonction de sa valeur.

Pour écouter un événement HTML, nous avons utilisé la directive v-on. Dans cet exemple, nous écoutons l'événement click sur le bouton et appelons la méthode toggleMessage.

## Calcul des propriétés

Vous pouvez utiliser des fonctions pour calculer des valeurs dérivées à partir des données de l'application. Dans Vue.js, vous pouvez définir ces fonctions en tant que propriétés calculées. Les propriétés calculées sont mises à jour automatiquement lorsque les données sous-jacentes changent.

Voici un exemple de propriété calculée :

```javascript
var app = new Vue({
  el: '#app',
  data: {
    message: 'Bonjour Vue !',
    nom: 'John',
    prenom: 'Doe'
  },
  computed: {
    nomComplet: function () {
      return this.nom + ' ' + this.prenom
    }
  }
})
```

Dans cet exemple, nous avons ajouté une nouvelle propriété nomComplet à notre instance Vue. Cette propriété est définie comme une fonction qui renvoie la concaténation de nom et prenom. Nous pouvons maintenant utiliser cette propriété calculée dans notre HTML :

```html
<div id="app">
  <p>{{ message }}, {{ nomComplet }} !</p>
</div>
```

Ici, nous avons ajouté la propriété calculée nomComplet à notre interpolation. Lorsque Vue.js crée l'instance, il exécute la fonction nomComplet pour la première fois et stocke sa valeur dans la propriété nomComplet. À partir de ce moment-là, chaque fois que nom ou prenom est mis à jour, Vue.js réexécute automatiquement la fonction nomComplet pour mettre à jour sa valeur.

## Composants Vue.js

Les composants Vue.js vous permettent de définir des éléments HTML réutilisables et personnalisés. Les composants peuvent contenir leur propre état et comportement, ainsi que des modèles HTML, des styles et des scripts. Les composants peuvent être imbriqués les uns dans les autres pour créer des interfaces utilisateur complexes.

Voici un exemple de composant Vue.js :

```javascript

Vue.component('mon-composant', {
  props: ['nom'],
  template: '<p>Bonjour, {{ nom }}!</p>'
})
```

Nous avons défini un nouveau composant Vue appelé "mon-composant". Ce composant a une propriété nom qui est passée en tant que prop. Nous avons également défini un modèle HTML simple qui affiche un message de salutation personnalisé en fonction de la valeur de nom.

Nous pouvons maintenant utiliser ce composant dans notre application en l'ajoutant à notre instance Vue :

```javascript
var app = new Vue({
  el: '#app',
  data: {
    nom: 'John'
  }
})
```

```html
<div id="app">
  <mon-composant v-bind:nom="nom"></mon-composant>
</div>
```

Nous venons d'ajouter ici notre composant Vue à notre instance Vue. Nous avons également passé la valeur de nom en tant que prop en utilisant la directive v-bind. Le composant affichera maintenant "Bonjour, John!" dans notre application.

##Les directives personnalisées

Les directives personnalisées sont une fonctionnalité avancée de Vue.js qui vous permet de créer vos propres directives. Les directives personnalisées
Sayah El Yatim
continue

peuvent être utilisées pour ajouter des fonctionnalités personnalisées à votre application qui ne sont pas disponibles dans les directives intégrées de Vue.js.

Voici un exemple de directive personnalisée :

```javascript
Vue.directive('mon-directive', {
  bind: function (el, binding) {
    el.style.color = binding.value
  }
})
```

Dans cet exemple, nous avons créé une nouvelle directive appelée mon-directive. Cette directive change la couleur du texte d'un élément HTML en fonction de la valeur de l'argument de liaison.

Nous pouvons ensuite utiliser cette directive dans notre HTML :

```html
<div id="app">
  <p v-mon-directive="'red'">Ce texte sera rouge.</p>
</div>
```

Dans cet exemple, nous avons ajouté la directive v-mon-directive à notre élément <p>. Nous avons également passé l'argument de liaison "red" à la directive, ce qui signifie que le texte sera rouge.