> [!NOTE]
> Aidez vous du doc-explications.md de ce répertoire, et de la doc officielle
Pour coder les exercices, utilisez un compilateur php local (devilbox, php avec apache), ou sur un site comme https://extendsclass.com/fr/php.html

> [!TIP]
> **sizeof()** est une fonction native de php, elle est très utile car elle permet de savoir combien de clés possède un tableau (entre autres).
> On l'utilise souvent pour savoir combien de cycle une boucle doit effectuer pour parcourir tous les clés d'un tableau.

1)
- Afficher les chiffres de 0 à 9 grâce à une boucle.
- Vous n'avez pas le droit d'écrire un chiffre "en dur" dans un echo, seulement d'appeler une variable.

2)
- Même exercice que le précédent, mais il faut utiliser un autre type de boucle.

3)
- Prenez le tableau de l'exemple, afficher toutes les **valeurs** qu'il contient, avec un espace entre 2 valeurs.
- Utiliser une boucle.
```php
$tableau = array('ce', "tableau", 'contient', "une", 'phrase');
```

4)
- Même exercice, mais utiliser un autre type de boucle.

5)
- Même exercice, mais utiliser un 3ème type de boucle (dernière fois promis).

6)
- Afficher les **clés** (index) et les valeurs de ce tableau, avex un espace entre chaque clés et chaque valeurs.
- A chaque cycle de la boucle, il faut afficher la valeur en premier, puis la clé ;
```php
$tableau = array(
    "tableau" => "ce"
    , "une" => "contient"
    , "phrase" => "autre"
);
```

7)
- Simuler un chargement.
- Pour chaque pourcent, vous devez afficher l'état du chargement tous les 10%, de 0% à 100%.
Par exemple : Chargement 0%
Chargement 10%
Chargement 20%
... etc
- Attention, vous n'avez pas le droit de créer ou de modifier un variable dans le bloc de code de la boucle. Seulement d'en afficher avec echo.

8)
- Réparer ce tableau scalaire dans lequel il manque des index, car ils ne se suivent plus.
- Ajouter au tableau, grâce à une boucle, les index et les valeurs manquantes.
- Etudier le tableau pour en déduire la valeur à ajouter pour chaque index manquant.
- Le tableau possède 10 index une fois réparé.
- Remettre les index dans l'ordre numérique du plus petit au plus grand.
> [!TIP]
> la fonction native "isset()" a l'air bien utile ici pour éviter des erreurs de script

> [!TIP]
> la fonction native "asort()" remet les index en ordre
```php
$tableau = array(
    0 => "1"
    ,1 => "2"
    ,2 => "3"
    ,4 => "5"
    ,8 => "9"
    ,9 => "10"
);
//Réparer le tableau avec une boucle.


//Pour voir ce qu'il contient :
echo "<pre>"; // On rajoute une balise <pre> autour du var_dump pour qu'il soit plus facilement lisible.
var_dump($tableau);
echo "</pre>";
```

9)
- Avec le tableau précédent **réparé**
- Sans effacer la valeur, ajouter "key" devant chaque valeur (par exemple, la valeur de l'index [0] => "1" deviendra [0] => "key1").
- Sans créer de deuxième tableau, inverser les valeurs et les clés de $tableau. Par exemple le premier index sera ["keyO"] => 1

> [!TIP]
> la fonction native "unset()" peut supprimer proprement la clé d'un tableau.