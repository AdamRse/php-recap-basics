# Conditions
Une condition permet l'execution d'un bloc de code, si la condition est un booléen true (vrai).
## Le If
### Le booléen
- Le if est le plus simple. Si la l'opération (ou condition) donnée est vrai (true), alors le code écrit dans le bloc du if s'execute. If veut dire "Si" en Anglais.
- Un booléen est un élément binaire : Soit true (vrai), soit false (faux), il ne peut y avoir d'autres états, ou alors ce n'est plus considéré comme un booléen.
- Attention, beaucoup d'éléments retournent un booléen exploitable par le if. Si l'élément dans le if n'est pas strictement un booléen, PHP va essayer de le traduire en booléen true/false (true par défaut).
> [!NOTE]
> Un bloc de code, c'est un code placé à l'interieur d'acolades (en Anglais : braces) { }
```php
//Je créé une variable qui contient le booléen true (vrai)
$booleen = true;

//J'affiche "Bonjour"
echo "Bonjour";

//J'aimerais qu'un code ne soit appelé uniquement si $booléen est true (vrai)
if($booleen == true){ // ""est égal à" : Le double égale vérifie si ce qu'il y a à gauche et à droite sont agaux. Le résultat sera un booléen.

    //Si la l'opération (condition) du if est true, on execute le bloc de code, ici on affichera " vous !"
    echo " vous !";
}

//Le code affichera : "Bonjour vous !"

//On peut aussi écrire le même code avec une opération plus simple :
if($booleen){
    echo "?!?";
}

//Le code affichera : "Bonjour vous !?!?"
```
### inverser un booléen
Un booléen peut être inversé avec le point d'explcamation " ! " placé avant n'importe quel booléen.
On peut même le placer dans un " == " pour dire "n'est pas égal à", ou "est différent de", il serra alors noté " != ".
```php
//Je créé une variable qui contient le booléen true (vrai)
$booleen = true;

echo "Bonjour";

//On teste si le boléen est égal à false
if($booleen == false){// Celà revient à dire, est-ce que true est égal à false ? Non, donc l'opération renverra un false (faux).

    //La condition du if est false, soyez tranquille, la string ne serra jamais affiché.
    echo "Meuh!!!";
}

//Le code affichera : "Bonjour"

//On teste l'inverse de booléen, donc l'inverse de true
if(!$booleen){// Celà revient à écrire !true, donc false

    //La condition du if est false, soyez tranquille, la string ne serra jamais affiché.
    echo "Bêêêh!!!";    
}

if($booleen != true){// Celà revient à écrire "est-ce que true est différent de true ?", Non, donc false.

    //La condition du if est false, soyez tranquille, la string ne serra jamais affiché.
    echo "Bêêêh!!!";    
}

//Le code affichera : "Bonjour"
```
### typage du booléens
Il faut savoir qu'un booléen false est un 0, et true est un 1. Ce qui les différencie des chiffres, c'est le type. false est 0 de type booléen, et le chiffre 0 est un 0 de type integer (ou int).
Pareil pour le true qui est un 1 de type booléen, et le chiffre 1 est de type int.
```php
var_dump(true == 1); // renvoie : bool(true), car true est un 1, et 1 est un 1, donc 1 est bien égal à 1.

var_dump(false == 0); // renvoie : bool(true), car false est un 0, et 0 est un 0, donc 0 est bien égal à 0.

var_dump(!false == 0); // renvoie : bool(false), car l'inverse de false est true, true est un 1, donc 1 n'est pas égal à 0.

var_dump(false != 0); // renvoie : bool(false), car false est un 0, 0 est égal à 0, donc 0 n'est pas différent de 0.
```
On pourra les différencier à l'aide du triple égale.
> [!TIP]
> Si vous n'êtes pas sûr de ce que renvoie votre opération, vous pouvez la tester dans un var_dump, ou un print_r, de la même façon que vous utilisez cette opération dans un if.
### Le triple égal
Le triple égal "===" permet de vérifier la concordance entre la valeur ET le type, là où le double égal "==" ne vérifira que la concordance de la valeur.
> [!WARNING]
> Au début il est courrant de confondre le = du == et du ===.
> - le = c'est comme un ordre : "Tu mets ce qu'il y a à droite du égal, dans ce qu'il y a à gauche, et c'est tout. Un ordre, donc ne vérifie pas de condition, il execute.
> - le == revient à poser la question "est-ce égal à", il renvera donc un true ou un false.
> - le === est comme le ==, sauf qu'il vérifie aussi que le type à droite est le même que le type à gauche. Ainsi si le résultat d'un === sera vrai, alors le == sera toujours vrai, mais pas l'inverse !
```php
var_dump(true == 1); // renvoie : bool(true)

var_dump(true === 1); // renvoie : bool(false), car true est un 1,de type booléen, 1 est un 1 de type int, donc les types de sont pas strictement égaux.

var_dump(false === 0); // renvoie : bool(false), car false est un 0 de type booléen, 0 est un 0 de type int, donc les types ne sont pas strictement égaux.

var_dump(true != 1); // renvoie : bool(false), car true est un 1, 1 est un 1, le =! ne vérifie pas le typage, donc 1 n'est pas différent de 1, donc false.

var_dump(true !== 1); // renvoie : bool(true), car true est un 1 de type booléen, 1 est un 1 de type int, ils sont bien différents, donc true.

var_dump(true == "1"); // renvoie : bool(true), car true est un 1, "1" est un 1, donc 1 est bien égal à 1

var_dump(true === "1"); // renvoie : bool(false), car true est un 1 de type booléen, "1" est un 1 de type string, leur type est différent, donc false

```
N'hésitez pas à tester bien d'autres opérations !
### Multiple opérations avec les opérateurs logique
On peut placer plusieurs opérations imbriquées dans un seul if().
Logiquement, celà revient à faire un if dans un if. Au lieu de faire ça, on peut mettre les 2 if() dans un seul.= :
- Avec le && (ET ou AND) :
```php
$nb = 7;

// && veut bien dire ET, donc il faut que les 2 opérations testées soient true pour entrer dans le bloc.
if($nb == 7 && is_int($nb)){// is_int($nb) renvoie true si $nb est un int. False si c'est autre chose.

    //Si la condition est true, on execute le bloc du if
    echo 'Le nombre testé est bien le chiffre 7';
}

//Le code affichera : "Le nombre testé est bien le chiffre 7"

//Oui bien vu, un if($nb === 7) aurait bien fait exactement la même chose, vous suivez !

$random = rand(1, 10);

if($random < 8 && $random > 2){// si $random est inférieur à 8, ET est supérieur à 2, donc si $random est entre 7 et 3

    //On execute ce code si $random est 4, 5, 6 ou 7
    echo 'Le chiffre est entre 7 et 3';
}
```
> [!NOTE]
> PHP est bien optimisé. Si la première opération d'un && renvoie false, la deuxième opération ne sara jamais calculée.
- Avec le || (OU ou OR) :
```php
$nb = 7;

// || veut dire "OU", il faut donc que l'une des 2 opérations renvoie un true. C'est le cas de la deuxième, car $nb est un int.
if($nb == false || is_int($nb)){// revient à false || true, donc true car l'une des 2 opérations du || est true.

    //Si la condition est true, on execute le bloc du if
    echo 'le nombre est false ou integer';
}

//Le code affichera : "le nombre est false ou integer"

//On génère un nombre aléatoire entre 1 et 10
$random = rand(1, 10);

// si $random est supérieur à 8, OU est inférieur à 2
if($random > 8 || $random < 2){

    //On execute ce code si $random est 1, 9 ou 10
    echo '[1 ; 2[ - [9 ; 10]';
}
```
> [!NOTE]
> De la même façon que le &&, le || ne calcule pas la 2ème opération si la première est déjà true.

> [!TIP]
> On peut cumuler les && et les || en jouant avec des parenthèses :
> if( (false && false) || true) renvera true.
## If/else
Le else veut dire "sinon" en Anglais.
Un else, s'il est utilisé, est **toujours** à la suite d'un bloc de if. Un if peut donc exister sans else, mais un else ne peut pas exister sans if, car il représente une alternative au if.
Le else désigne un bloc de code qui sera executé si le bloc de code du if est ignoré, donc si la condition du if est false (faux).
```php
//On teste si la string "2" est strictement égale à l'int 2
if(2 === "2"){// false, car les types sont différents, et le tripe égal vérifie les types

    //Si la condition est true, on execute le bloc du if
    echo "2 est bien égal à 2";
}
else{

    //Si la condition est false, on execute le bloc du else
    echo "2 n'est pas égal à 2";
}

//Le code va afficher : "2 n'est pas égal à 2"

//On teste si la string "2" est égale à l'int 2
if(2 == "2"){// false, car les types sont différents, et le tripe égal vérifie les types

    //Si la condition est true, on execute le bloc du if
    echo "2 est bien égal à 2";
}
else{

    //Si la condition est false, on execute le bloc du else
    echo "2 n'est pas égal à 2";
}

//Le code (seulement le 2ème if) va afficher : "2 est bien égal à 2"
```
> [!NOTE]
> Dans un if/else, il y aura donc **toujours** l'un des 2 blocs qui sera executé. Jamais aucun, et jamais les 2.
## If/elseif/else
elseif veut dire "Ou si", on comprend donc qu'il nous faut un premier "Si" pour que ça ait un sens.
Entre le if et le else, on peut insérer une autre condition "elseif", qui de la même façon, sera liée au if. On ne peut pas l'utiliser sans if.
- elseif() est comme un if, il admet une condition d'entrée à true pour executer son bloc de code.
- elseif() est comme un else, si le if() est executé, le bloc du elseif() ne sera jamais executé.
C'est plus simple qu'il n'y parait, on voit mieux avec un exemple :
```php
//J'initialise $nb à 11
$nb = true;

if($nb === 1){// si $nb est strictement égale à l'int 1

    //Le code ne sera jamais executé
     echo "Le chiffre 1";
}
elseif($nb == 1){//si $nb est 1, true est 1, donc on execute le bloc du elseif()

    echo "Le 1";
}
else{// Si les conditions du if et du elseif sont fausse, on executera le else, c'est le "par défaut si rien ne marche"

    //Le code ne sera jamais executé.
    echo "Je ne sais pas";
}
```
L'intérêt : on peut réduire la quantités d'opérations dans un if/else, ou éviter de mettre un if à l'intérieur d'un else pour tester d'autres conditions.
```php
$nb = rand(0, 10);

if($nb < 2){// si $nb est strictement inferieur à 2

    //Le code sera executé pour $nb = O ou 1
    echo "Le nombre est inférieur à 2";
}
elseif($nb < 5){//si $nb est strictement inférieur à 5

    //A cause du if on sait que $nb ne sera pas inférieur à 2, sinon ce code ne serait pas executé
    //Le code sera executé pour $nb = 2, 3 ou 4
    echo "Le nombre est entre 2 et 4";
}
elseif($nb < 8){//si $nb est strictement inférieur à 8

    //A cause du if on sait que $nb ne sera pas inférieur à 5, sinon ce code ne serait pas executé
    //Le code sera executé pour $nb = 5, 6 ou 7
    echo "Le nombre est entre 5 et 7";
}
else{// Si les conditions du if et des elseif sont fausse, on executera le else, donc $nb est strictement supérieur à 7

    //Le code sera executé pour $nb = 8, 9 ou 10
    echo "Le nombre est 8 ou supérieur";
}
```
## Bonus, le Switch
Le switch est plus rarement utilisé, je le ferai pls tard
