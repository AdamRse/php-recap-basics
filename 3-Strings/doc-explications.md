# Strings
Une string est une chaîne de caractère en français.

## Déclarer une string dans une variable
```php
//Avec les doubles quotes
$texte = " String ";

//Avec les simples quotes
$texte = ' String ';

//Avec les backticks
$texte = ` String `;
```
On n'utilisera pas la forme avec les backticks.

### Quelle différence entre simple et double quotes ?
On choisis l'un ou l'autre en fonction de ce qu'on va mettre dedans en général. La raison principale :
- Les simple quotes interprettent tous les caractère comme des caractères.
- Les double quotes peuvent interpréter des variables.
```php
//Je créé une vriable qui contient la string "Bonjour";
$variable = "Bonjour";

//Je l'utilise dans les double quotes
$texte = "$variable tout le monde"; // contient la string "Bonjour tout le monde"

//Dans les simple quotes, la variable n'est pas interprétée comme une variable, juste des caractères.
$texte = '$variable tout le monde'; // contient la string '$variable tout le monde'
```
## Utilisation des strings :|
En PHP, on utilise echo pour afficher **UNE** string, et **UNE SEULE**.
Pour afficher plusieurs string, il faut donc les **CONCATENER**, ou autrement dit, les attacher, les coller ensemble pour qu'elles ne fassent plus qu'une, et soit lisible par echo. On utilise le point pour concaténer.
```php
//On concatène comme ceci
echo "String 1".'String 2'; // Affiche : "String 1String 2"

//ça marche aussi pour les variables qui contiennent une string
$string1 = "String 1";
$string2 = 'string 2';

echo $string1.$scring2; // Affiche : "String 1String 2"

//Avec les double quotes, elles interprettent les variables, donc on nest pas obligé de les concaténer. Ainsi on peut mettre un espace entre les 2
echo "$String1 $String2"; // Affiche : "String 1 String 2"

//Pour mettre un espace entre les 2 variables avec de simples quotes, on est obligé de concatenner une autre string contenant un espace :
echo $string1.' '.$string2; // Affiche : "String 1 String 2"
```
### Avec les tableaux
Pour concaténer des valeurs de tableaux, la syntaxe n'est pas la même :
```php
//Je créée un tablau scalaire à 2 valeurs
$tableau = array("chat", "chien"); // [0]=>"chat" [1]=>"chien"

//Avec double quotes, on utilise les braces pour interpréter la variable { }
echo "{$tableau[0]} et {$tableau[1]}"; // Affiche "chat et chien"

//Avec les simple quotes, on concatène avec les points
echo $tableau[0].' et '.$tableau[1]; // Affiche "chat et chien"
```
> [!CAUTION]
> Utiliser un tableau dans une string renverra une erreur. Il faut bien utiliser la **valeur** du tableau, en utilisant son index (0 ou 1 dans l'exemple) comme l'exemple au dessus.

On peut aussi concaténer des nombres (int) et des calculs entre parenthèses
```php
echo 10; // Affiche : 10

echo (6+4) // Affiche 10

//On doit toujours concatenner des parenthèses, que ce soit avec les simples ou double quotes.
echo "2 + 3 = ".(2+3)." !"; // Affiche "2 + 3 = 5 !"
```
### Echapper un caractère
En PHP on peut échapper certains caractères, en signalant à php qu'on veut les utiliser en tant que caractère, et non interprétés en tant que code.
Pour ça, on utilise l'antislash \
```php
$v = 15;

//On échappe le premier $, car on ne veut pas utiliser la variable $v, mais écrire $v textuellement. le $ ne sera pas donc interprété comme une variable.
echo "La variable \$v contient $v"; // Affiche "La variable $v contient 15"

//On échappe les quotes, car on veut les utiliser dans la string. Si on ne les échappe pas avec \, php va fermer la string.
echo "<p id=\"paragraphe\">"; //Affiche : <p id="paragraphe"> 
```
## Affichage en html
Il est possible de séparer le code html du code php en fermant la balise php quand on écrit du html, et en la rouvrant en écrivant du php.
Ca permet d'avoir un code plus lidible, et d'utiliser l'inteliscence html quand on écrit du html.
```php
<?php
$titre = "Un titre";
$texte = "Un texte";
$condition = true;
?>


<?php
if($condition){
    ?>
    <div>
        <h1><?php echo $titre ?></h1>
        <p><?php echo $texte ?></p>
    </div>
    <?php
}
?>
```
> [!TIP]
> Si on a besoin d'ouvrir des balises php seulement pour un echo, on peut utiliser les balises <?= "String" ?> au lieu de <?php echo "string" ?>
## Optionel, mais efficace
On utilise souvent des conditions pour afficher une string ou une autre (dans un if ou un if/else).
Il existe un moyen de faire une condition en ligne pour l'utiliser dans une sring :
```php
//Je créée une variable avec un chiffre aléatoire, soit 0 soit 1
$condition = rand(0,1);

//Je créée une string qui va afficher un résultat différent en fonction de $condition
echo ($condition == 1)?"Condition est de 1":"Condition est de 0"; // Si $condition est 1, affiche : Condition est de 1, sinon Condition est de 0.

//On peut l'utiliser au milieu d'une string en concaténant la condition en ligne dans des parenthèses
echo "La variable contition contient ".(($condition == 1)?"1":"0")." !"; // Si $condition est 1, affiche : "La variable contition contient 1 !", sinon "La variable contition contient 0 !"
```