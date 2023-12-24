"..." signifie qu'il faut décommenter et compléter la ligne, c'est pour aider. Aidez vous du doc-explications.md de ce répertoire, et de la doc officielle
Por coder les exercices, utilisez un compilateur php local (devilbox, php), ou sur un site comme https://extendsclass.com/fr/php.html

1)
Créer une variable $nom et $prenom avec un nom et un prénom dedans. L'afficher ensuite dans un echo avec un espace entre les 2, et en **double quote**.
```php
//$nom...
//$prenom...

//echo
```

2)
Même exercice mais l'echo doit afficher une string en **simple quote**.
```php
//$nom...
//$prenom...

//echo...
```

3)
Créer un tableau **scalaire** $reponse avec les valeurs "chat" et "chien".
afficher les faleurs dans un echo, avec un espace entre les 2.
Le echo est en **simple quote**.
```php
//$reponse...

//echo...
```

4)
Même exercice mais l'echo doit afficher une string en **double quote**.
Attention, vous devez utiliser les braces { } dans la syntaxe.
```php
//$reponse...

//echo...
```

5)
Créer un tableau **associatif** $visage, avec un index "yeux" qui contient la valeur "marron", et l'index "cheveux" qui constient la valeur "brun".
Afficher les valeurs "marron" et "brun" du tableau, séparées par une virgule, et dans un echo. Simples ou doubles quotes au choix.
```php
//$visage...

//echo...
//Affichage attendu : marron,brun
```

6)
Avec le tableau $visage de l'exercice 5, afficher un echo qui affiche "Vous avez les yeux "marron" et les cheveux "brun" !". Attention, il faut bien que marron et brun soient dans des double quotes dans le texte de echo !
Toujours en utilisant les valeurs du tableau.
Le echo doit afficher une string en **double quote**.
```php
//$visage...

//echo...
//Affichage attendu : Vous avez les yeux "marron" et les cheveux "brun" !
```

7)
Initialisez 2 variables $a et $b toutes 2 égales à 1.
Sans stocker de résultant dans une autre variable, afficher dans un echo la string suivante :
"L'addition des variables $a et $b = 2", en utilisant les **double quote**.
ATTENTION : $a et $b doivent litérallement s'afficher, et non afficher 1.
ATTENTION : vous n'avez pas le droit d'écrire le chiffre 2 dans la string de echo (faites un calcul).
```php
//$a...
//$b...

//echo...
//Affichage attendu : L'addition des variables $a et $b = 2
```

###Bonus

8)
initialisez une variable $nb avec un chiffre aléatoire entre 1 et 10.
Si $nb est inférieur ou égal à 5, echo affiche "petit". Sinon, il affichera "grand, suivi d'une string "nombre".
ATTENTION : interdiction d'utiliser les mot-clés if et else, il faut que echo affiche le résultat d'une condition en ligne.
ATTENTION : vous n'avez le droit d'écrire "nombre" qu'une seule fois dans cet exercice.
```php
//$nb...

//echo...
//Affichage attendu : petit nombre || grand nombre
```