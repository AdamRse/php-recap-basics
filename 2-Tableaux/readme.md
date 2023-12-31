> [!NOTE]
> "..." signifie qu'il faut décommenter et compléter la ligne, c'est pour aider. Aidez vous du doc-explications.md de ce répertoire, et de la doc officielle
Pour coder les exercices, utilisez un compilateur php local (devilbox, php), ou sur un site comme https://extendsclass.com/fr/php.html

1)
Créer un tableau (une variable de type tableau)

```php
//$tableau = ...

echo "<pre>";
var_dump($tableau);
echo "</pre>";

  //Sortie du var_dump() attendue :
  //array(0) { } 
```

2)
Créer un tableau scalaire avec les valeurs "Oui", "non", et "Peut-être". Les index de ces valeurs doivent être créés automatiquement par php.

```php
//$scalaire = ...

echo "<pre>";
var_dump($scalaire);
echo "</pre>";

      //Sortie du var_dump() attendue :
      //array(3) { [0]=> string(3) "oui" [1]=> string(3) "non" [2]=> string(10) "peut-être" }
```

3)
Créer un tableau associatif avec les valeurs avec les clés "pays", "ville", et leur valeurs associées "Slovénie", "Ljubljana".

```php
//$assoc = ...

echo "<pre>";
var_dump($assoc);
echo "</pre>";

      //Sortie du var_dump() attendue :
      //array(2) { ["pays"]=> string(9) "Slovénie" ["ville"]=> string(9) "Ljubljana" } 
```


4)
Ajouter la valeur "En fait non" à la suite dans le tableau $scalaire

```php
//$scalaire...

echo "<pre>";
var_dump($scalaire);
echo "</pre>";

      //Sortie du var_dump() attendue :
      //array(4) { [0]=> string(3) "Oui" [1]=> string(3) "Non" [2]=> string(10) "Peut-être" [3]=> string(11) "En fait non" }
```

5)
Attention, concentration !
Mettre la valeur de la clé "pays" du tableau $assoc, DANS le tableau $scalaire (à la suite des autres clés).

```php
//$scalaire...

echo "<pre>";
var_dump($scalaire);
echo "</pre>";

      //Sortie du var_dump() attendue :
      //array(5) { [0]=> string(3) "Oui" [1]=> string(3) "Non" [2]=> string(10) "Peut-être" [3]=> string(11) "En fait non" [4]=> string(9) "Slovénie" } 
```

6)
Ajoutez la valeur de l'index 2 de $scalaire, dans le tableau $assoc, avec un index appelé "assoc"

```php
//$assoc...

echo "<pre>";
var_dump($assoc);
echo "</pre>";

      //Sortie du var_dump() attendue :
      //array(3) { ["pays"]=> string(9) "Slovénie" ["ville"]=> string(9) "Ljubljana" ["assoc"]=> string(10) "Peut-être" } 
```

7)
Ajoutez le tableau $assoc au tableau $scalaire, dans l'index 11 (du tableau $scalaire).

```php
//$scalaire...

echo "<pre>";
var_dump($scalaire);
echo "</pre>";

      //Sortie du var_dump() attendue :
      //array(6) { [0]=> string(3) "Oui" [1]=> string(3) "Non" [2]=> string(10) "Peut-être" [3]=> string(11) "En fait non" [4]=> string(9) "Slovénie" [11]=> array(3) { ["pays"]=> string(9) "Slovénie" ["ville"]=> string(9) "Ljubljana" ["assoc"]=> string(10) "Peut-être" } } 
```