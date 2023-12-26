# Fonctions
- Une fonction est un bloc de code qu'on peut réutiliser.
- C'est un peu assimilable à une boîte noire avec des entrée (paramètres) et une sortie (valeur de retour).
## Déclaration
On déclare une fonction sous la forme suivante
```php
function nomDeLaFunction(){
    //Code de la fonction
    //On peut retourner un résultat si on le souhaite.
}
```
La fonction n'est pas appelée de cette façon, elle est juste déclarée, elle ne s'exécute pas.
Pour éxécuter la fonction, il faut l'appeler par son nom :
```php
nomDeLaFunction();
```
## Entrées / Sortie
- Les fonctions peuvent avoir de multiples paramètres d'entrée, mais un seul retour.
- Les paramètres d'entrée et le retour peuvent être de tout types.
- Une fonction ne retourne pas forcément quelque chose.
```php
function nomDeLaFunction($parametre1, $paramètre2){
    //Je peux coder avec les paramètres que j'ai reçu, ils peuvent changer à chaque appel de la fonction, c'est pourquoi on utilise des variables.
    //C'est à l'appel de la fonction qu'on décide la valeur des paramètres d'entrée.
    //Une fonction avec 2 paramètre d'entrée comme ici devra toujours être appelée en lui donnant 2 valeurs en entrée.

    //Je peux envoyer quelque chose au code qui a appelé la fonction avec un return quelque chose
    return $parametre1 + $parametre2;
}

//Appel de la fonction avec 2 paramètres d'entrée. On additionne les 2 dans la fonction, et on retourne le résultat à la place de la fontion.
$addition = nomDeLaFunction(2, 8);// C'est comme si on avait fait : $addition = 2+8
```
Si les paramètres ont une valeur par défaut, on n'est pas obligé de rentrer le paramètre à l'utilisation.
Exemple :
```php
function nomDeLaFunction($parametre1, $paramètre2 = 10){

    //On retourne l'addition des 2 paramètres
    return $parametre1 + $parametre2;

}

//On a déclaré la fonction avec 2 paramètres, mais le 2ème vaut 10 si on n'envoie qu'un paramètre.
$addition = nomDeLaFunction(2); // $addition = 2 + 10

//On peut tout de mème envoyer le 2ème paramètre, il remplacera la valeur par défaut qui est 10.
$addition = nomDeLaFunction(2, 3); // $addition = 2 + 3
```

> [!CAUTION]
> Si on n'envoie qu'un seul paramètre quand 2 sont attendu sans valeur par défaut, php renvoie une erreur de script
Exemple d'utilisation en passant un tableau en paramètre, c'est un cas classique :
```php
function retournePremierIndex($tableau){

    return $tableau[0];
}
//On créé un tableau dont le premier index est choux, et le 2ème est chèvre
$ferme = array("choux", "chèvre");

echo retournePremierIndex($ferme); // Affiche : choux

//On a déclaré la fonction avec 2 paramètres, mais le 2ème vaut 10 si on n'envoie qu'un paramètre.
$addition = nomDeLaFunction(2); // $addition = 2 + 10

//On peut tout de mème envoyer le 2ème paramètre, il remplacera la valeur par défaut qui est 10.
$addition = nomDeLaFunction(2, 3); // $addition = 2 + 3
```
## Le return
Un return renvoie quelque chose, mais il arrête l'execution de la fonction du même coup. S'il reste du code dans la fonction après le return, il ne sera pas exécuté.
```php
function fonctionRetourner2parametres(){

    $a = "choux";
    //on renvoie "choux" au code qui a appelé la fonction
    return $a;

    //Ce code ne sera JAMAIS éxécuté, car la fonction a déjà retourné quelque chose plus haut.
    $b = "chèvre";
    return $b;
}

$ferme = fonctionRetourner2parametres(); // $ferme = "choux"
```
Si on veut retourner 2 variables par exemple, ici la string "chèvre" et la string "choux", on doit les mettre dans un tableau :
```php
function fonctionRetourner2parametres(){

    $a = "choux";
    $b = "chèvre";

    $tableau = array($a, $b);
    return $tableau;
}

$ferme = fonctionRetourner2parametres(); // $ferme = array(2){ [0]=>"choux", [1]=>"chèvre" }
```
Si on retourne une variable concaténable, on peut concaténer une fonction :
```php
function fonctionRetourner2parametres(){

    $a = "choux";
    $b = "chèvre";

    return 'Le '.$a.', la '.$b; // On retourn donc la string "Le choux, la chèvre"
}

echo fonctionRetourner2parametres().' et le loup'; // $Affiche : Le choux, la chèvre et le loup
```