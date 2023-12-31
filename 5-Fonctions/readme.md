> [!NOTE]
> Aidez vous du doc-explications.md de ce répertoire, et de la doc officielle
Pour coder les exercices, utilisez un compilateur php local (devilbox, php), ou sur un site comme https://extendsclass.com/fr/php.html

1)
- Créer une fonction qui **retourne** la string "Bonjour"
- Faire un echo qui affichera "Bonjour, Bonjour !", mais au lieu d'écrire "Bonjour", vous appelez la fonction que vous avez créée.

2)
- Créer une fonction qui prend en compte un **paramète**. Le paramètre sera une string.
- La fonction doit renvoyer le paramètre d'entrée entre <b></b>. Par exemple si on passe la string "Manger", la fonction doit retourner "<b>Manger</b>"
- Dans un echo, faites une phrase en appelant la fonction 3 fois, avec le paramètre de votre choix.

3)
- Créer une fontion qui accepte un **paramètre** en entrée.
- Ce paramètre sera un tableau scalaire, il contiendra une liste d'ingrédient.
- Coder le bloc de la fonction pour qu'il retourne une liste d'ingrédients de la forme suivante
```html
<ul>
    <li>Ingrédient 1</li>
    <li>Ingrédient 2</li>
    <li>Ingrédient 3</li>
    ...
</ul>
```
- Appeler la fonction dans un echo, après la string "</p>Liste des ingrédients :</p>"
- Servez-vous de cd tableau à envoyer en paramètre d'entrée de la fonction :
```php
$ingredients=array("4 Oeufs", "300g de farine", "O.5L de lait", "100g de beurre", "500g de chocolat");
```
> [!TIP]
> Il est conseillé d'utiliser la concaténation de string " .= ", pour ajouter une string à une variable string.

4)
- On va créer un petit jeu de dés avec 2 joueurs.
- créer une fonction "jetDeDes()" qui retournera un nombre aléatoire entre 2 et 12 (comme si on tirait 2 dés de 6)
- retourner le résultat de la fonction dans une variable $joueur1, et dans $joueur2 (La fonction doit être appelée pour chaque variable).
- Dans une string, afficher un essage de victoire avec le joueur qui a gagné.

5)
- Créer une fonction calculHypotenuse. Elle servira à calculer l'hypoténuse (le plus grand côté) d'un triangle rectangle.
- La fonction accepte 2 paramètre d'entrée qui représentent la longueur des 2 plus petit côtés d'un triangle rectangle.
- la formule du calcul : Hypoténuse  = racine carré de (coté 1² + coté 2²) https://www.letudiant.fr/college/methodologie-college/article/theoreme-de-pythagore-3-minutes-pour-comprendre.html#:~:text=En%20d%27autres%20termes%2C%20si,que%20a%C2%B2%20%2B%20b%C2%B2%20%3D%20c%C2%B2.
- Afficher l'hypoténuse pour 3 triangles de taille différentes :
    - triangle 1 : petit côté 1 = 4 ; petit côté 2 = 5 ; Retour de la fonction attendu : 6.4031
    - triangle 2 : petit côté 1 = 2 ; petit côté 2 = 6 ; Retour de la fonction attendu : 6.3246
    - triangle 3 : petit côté 1 = 5 ; petit côté 2 = 5 ; Retour de la fonction attendu : 7.0711

6)
- Créer une fonction qui accepte en entrée une chaîne de caractère.
- La fonction doit retourner cette chaîne de caractère inversée.
- strrev() est une fonction native de php qui permet de retourner une chaîne de caractère dans l'ordre inverse. Il ne faut pas l'utiliser :)