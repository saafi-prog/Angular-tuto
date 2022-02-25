# Angular-tuto
*les components composent les blocs d'une application en angular.
*@ component() est composé: 
    *d'un component.html (templateUrl: './product-list.component.html') --> chemin vers le fichier html, il permet de generer le contenue de l'element html dans le DOM.
    *un component.css (selector: 'app-product-list')--> le sélecteur CSS  permettra de lier le tag HTML de l'élément et le code du composant
    *un component.ts ( ts pour type script).
*Tout componet comprend un template HTML qui va déterminer le redu du component.
*@component est un decorateur pour une classe dans angular.
*ng : pour dire qu'il s'agit d'angular. c'est les préfixe de Next generation (lien:https://www.quora.com/What-does-ng-stands-for-in-all-directives-of-AngularJs).
on peut trouver ng new : pour créer un nouvel espace de travail par exemple.
*ngFor: permet de boucler sur une array et d 'injecter les élélments dans le DOM.
*{{}}: est une interpolation qui permet de rendre une valeur ex: {{product.name}}
* Dans product-list.component.html :<a [title="product.name + `details`"]>{{product.name}}</a> : permet  d'avoir le nom du produit comme un lien cliaquable
[] permet de lier, par son attribut, le nom et son detail dans une expression modèle --> un pop qui apparait en passant la souris au dessus du nom du produit.
*ngIf utilisé dans dans le 'product-list.component.html', est une directive (dans ce cas une condition if) utilisé dans un element Html  exemple: 
  <p *ngIf="product.description"> 
    Description: {{ product.description }}
  </p> et permet de créer cette balise que si une description existe.

**Attribution des écouteurs d 'évenement** 
*Avec la methode share(), on peut créer un bouton et lui attacher un évement "click" qui permet de partager un produit.
=> Tous nos produit auront un bouton share car ils se trouvent dans la div ou  la boucle ngFor est appliqué.

*ng genertor component produit-alerts: est une commande qu'on rentre das le termial et permet de créer: 
    un produit-alerts.components.ts,
    un produit-alerts.components.html, 
    un produit-alerts.components.css
*@angular/core : c'est le code interne et il comporte un ensemble de fonctionnalités: c'est l'operating systeme
*product-alerts.component.ts :contient des imports à partir de angular/core  et de products ainsi que des exports qui permet de partager des propriétes entre les components parent et components enfants en utilisant les input() decoradors et les output()decoradors.
*Le generateur rajoute automatiquement le produitAlertComponent au appModule pour qu'il soit disponible aux autres components de l 'appication.
*Oninit : methode de cycle de vie.
*Assigner au dcorador @Output notify l'evenment EventEmitter() pour emettre l'evenement quant la valeur de la propriéte notify change
*component, Output, input, Oninit,EventEmitter: ce sont des imports à partir de la bibliothèque @angular/core'
Parallememnt, il faut lier l'évement emitter au bouton par la méthode 
notify.emit().
*pour définir le  comportement attendu quant un utilisateur clique sur un bouton, le parent productListComponent  réagit à l'évenement cliquable de l'enfant. On définit la méthode 
onNotify() comparable à share() dans le product.component-list.ts avec une alert window qui apparaitra au déclenchement du clique sur le bouton "Notify Me"
*Pour mettre à jour le productListCmponent à partir de productAlertComponent, on attribut à  l'élment <app-product-alerts> </app-product-alerts> la methode onNotify().

**Adding Navigation**
*Toujours par la meme ligne de commande: ng generate component product-details --> généreune nouveau component product-details.
*Dans app.module.ts, on rajoute des route avec des "path" (chemin).
*dans le product-list.component.html: ajouter dans l'ancre un attribut [routerLink] qui permet de costomiser l'ancre.Il est composé d 'un segment fixe et d'un segment variable avec un id.==> apparition d 'un menu reherche
*le router angular affiche les componenet en fonction de l'url et des routes prédéfinie.
*Afin de visualiser nos prduits: Importer 'activatedRoute' depuis 'angular/router' et les produits depuis produits et l'implementer dans 'product-details.component.ts', puis définir le propriétes en créant une 'export class ProductDetailsComponent implements OnInit{}' et implementer un construcetur au seind de cette classe.
*activatedRoute est spécéfique à chaque component dont il fait appel.Injecter activatedRoute permet de configurer le component et utilser un service.
*La méthode ngOnInit() permet d'extrairele productId à partir des  parametre route attribué précédemment dans l'ancre situé  dans product-list.component.html, et retrouver dans le tableau de liste de produit le produit correspondant.
*Dans le product-details component.ts: on récupère le  produit par la méthode get("productId"), puis rechercher le prduit qui correspond au l'Id par la méthode find() qui renvoie la valeur du prmier élement trouver. (source:https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/find ).
*route.snapshot : permet d 'acceder au parametre route
*Implemener un template avec les details valeur: du nom du produit , prix avec devise (currency pipes qui transforme le  prix en nombre en prix en une chaine de caractère) et produit avec description. on remarque l'utilisation de la condition ngIf afin d'afficher ou non le produit s'il existe.
*pipes : est une fonction simple qui prend une certaine valeur input et rend en une valeur transformé. elle s'applique au date et au chaie de caractère par exemeple.

**Managing DATA**

