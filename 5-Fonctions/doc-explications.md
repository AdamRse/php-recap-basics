# Fonctions
- Une fonction est un bloc de code qu'on peut réutiliser.
- C'est un peu assimilable à une boîte noire avec des entrée (paramètres) et une sortie (valeur de retour).
- On untilise les fonctions pour appeler un code redondant, au lieu de l'écrire plusieurs fois, on érit une fonction qu'on apelle plusieurs fois.
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
## La portée
- Comme pour les boucles, les variables créées dans le fonction, ainsi que les paramètres d'entrée, n'existent **QUE** dans le bloc de la fonction.
```php
//J'initialise $a à 0;
$a = 0;

// Je créé une fonction qui aura un paramètre d'entré aussi appelé $a.
function fctA($a){
    
    //J'initialise une variable $b qu vaut $a
    $b=$a;
}

//J'appelle fctA() en lui passant 3 en paramètre, $a sera donc 3 dans la fonction fctA()
fctA(3);

echo $a; // Affiche : 0
echo $b; // Affichera une erreur php, la variable $b n'existe pas, car elle a été créé dans la fonction fctA(), elle n'a aucune existence en dehors.
```
## Récursivité
Une fonction peut s'appeler elle même, ça sapelle une fonction récusrive.
Attention, La récursivité consomme de la mémoire, il y a donc une limite par défaut du nombre d'appel récursif. Un nombre trop élevée peut renvoyer une erreur.
Typiquement, on l'utilise par exemple pour lister des fichiers ou des dossiers dans une arboresence :
```php
//Création de la fonction listeFichiers, elle retournera une liste de tous les fichiers de tous les répertoires qui se trouvent dans $cheminRepetroire
function listeFichiers($cheminRepetroire){

    // scandir() est une fonction native de php qui permet de lister tous les fichiers et dossiers, ils sont retournés dans un tableau.
    // $listeRepetroire contient donc un tableau scalaire dont chaque valeur est le nom d'un dossier ou d'un fichier.
    $listeRepetroire = scandir($cheminRepetroire);

    //Je parcours le tableau $listeRepertoire. La variable $nomFichierOuDossier contiendra donc le nom de dossier ou fichier trouvé.
    foreach($listeRepertoire as $nomFichierOuDossier){

        // On initialise une variable avec le chemin complet qui pointe vers le dossier ou le fichier qui est actuellement parcouri par le foreach
        $cheminComplet = $cheminRepetroire.'/'$nomFichierOuDossier;

        //Si le nom pointe sur un dossier, alors il faut aussi le parcourir
        if(is_dir($cheminComplet)){//is_dir() renvoie true si le chemin donné point sur un dossier, false s'il pointe sur un fichier.

            //On parcours le dossier trouvé en appelant la même fonction dans laquelle on est. Elle vérifiera donc à son tour s'il y a des dossiers dans le nouveau répertoire, et ainsi de suite.
            listeFichiers($cheminComplet);
        }
        else{ // $cheminComplet pointe donc sur un fichier, car is_dir() a renvoyé false.

            // On cherche à afficher le nom des fichiers, et on a le nom et de chemin d'un fichier, on l'affiche donc
            echo "<p>$cheminComplet</p>";

        }
    }
}

// Je donne le chemin du dossier à scanner dans $scannerIci
$scannerIci = "/home/Garage404";

//J'ai créé la fonction listeFichiers() qui va m'afficher tous les fichiers du répertoire, je peux donc l'appeler.
listeFichiers($scannerIci);
```