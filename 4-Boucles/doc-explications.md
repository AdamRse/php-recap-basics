# Les boucles
Une boucle est un bloc de code qui est voué à se répéter tqnt que la condition de sortie de la boucle n'est pas respectée.
On l'utilise souvent pour parcourir les valeurs d'un tableau une à une, mais pas que.
> [!WARNING]
> Attention ! Les boucles peuvent fair planter le code ! Si la condition de sortie est mal définie, la coucle tourne à l'infini, et donc paralyse le script.
> Votre code s'arrête et le navigateur continue de charger la page ? C'est parfois à cause d'une boucle infinie.
> Une boucle infinie consomm beaucoup de ressources, et peut parfois faire planter la machine entière.
### Boucle while()
La boucle while est la plus simple. **tant que** la condition est vrai (true), on reste dans la boucle. La condition devra toujours renvoyer un booléen.
> [!NOTE]
> Comme pour le if(), si PHP reçoit autre chose qu'un booléen (true/false) dans la boucle, il va tenter de le traduire en booléen (true par défaut). S'il n'y arrive pas, il renverra une erreur.
La forme la plus courrante du while :
```php
//On initialise une variable de condition à vrai.
$condition = true;

//La boucle while : TANT QUE $condition est true, on fais un nouveau cycle.
while($condition){

    //code
    //ATTENTION : si le code de la boucle ne met jamais la condition à false, on aura une boucle infinie, et le code va planter en plus de consommer beaucoup de ressources.
}

//On créé une variable aléatoire
$i = 1;
while($i < 5){//Le calcul renvoie un booléen, false ou true selon la valeur de $i.

    //On affiche la valeur de $i
    echo $i.' ';

    //On incrémente $i (incrémentation = ajouter +1)
    $i++;
}
// Le while va afficher : "1 2 3 4 "
```
Dans le while standard, on teste la condition de sortie **avant** d'éxécuter le code de la boucle. Donc si la condition n'est pas respectée la première fois qu'on entre dans le while, le bloc de code du while ne sera jamais exécuté.
```php
//On initialise une variable qu'on ne connaît pas à l'avance. On sait seulement que ce sera un int entre 1 et 10 inclus.
$random = rand(1, 10);

while($random != 5){ // Tant que $random est différent de 5 (donc si c'est 5 on sort de la boucle)

    //On affiche le nombre
    echo "Le nombre random est de $random !<br/>";

    //On remplace le bombre random par un nouveau. Si il tombe sur 5, on sortira de la boucle et on n'affichera pas le echo.
    $random = rand(1, 10);
}
```
Le problème, c'est qu'on aimerait au moins afficher une fois le echo dans la boucle while pour savoir sur quel nombre on est tombé.
Or si l'initialisation de la variable $random tombe sur 5, on n'irra jamais dans la boucle while, et on n'affichera jamais le nombre.
Pour ça il existe une autre boucle qu'on apelle "do-while".
Avec un do-while, on vérifie la condition qu'à la fin de la boucle, elle sera donc toujours exécutée au moins une fois :
```php
do{ // do veux dire "faire", donc on commence par éxecuter le code de la boucle sans tester aucune condition.

    //On initialise la variable random à l'intérieur de la boucle, car on sait qu'elle sera toujours appelée au moins une fois.
    $random = rand(1, 10);

    //On affiche le nombre
    echo "Le nombre random est de $random !<br/>";
}
while($random != 5);// On teste la condition ici, après la boucle. Si $rand est de 5, on sort de la boucle.
```
>[!TIP]
>On peut initialiser la variable de condition **dans** la parenthèse du while. On l'utilise en général pour fetcher un tableau (le fetch lis la première valeur, puis la supprime du tableau, et ainsi de suite).
> Par exemple avec PDO quand on retourne plusieurs lignes avec un select on peut faire un while($ligne=requetePDO->fetch(PDO::FETCH_ASSOC))
> Une fois que fetch a vidé le tableau, $ligne sera vide (null), et "vide" sera converti en false par PHP, donc on sort de la boucle.

### Boucle for()
- La boucle for est une boucle qui permet de gérer plus facilement un compteur. Grace à ce compteur, on peut voir plus facilement dans quel cycle de la boucle on est.
- Elle admet 3 paramètres pour fonctionner :
    1) Implémentation du **compteur**
    2) Condition pour rester dans la boucle (le "**tant que**"). C'est toujours un booléen (vrai ou faux).
    3) **Incrémentation** du compteur à chaque cycle de la boucle (On rajoute souvent +1, mais ce n'est pas une obligation)
> [!WARNING]
> On sépare les paramètre d'une boucle for avec un point-virgule ";", c'est spécifique à la boucle for.

```php
// Compteur à 0 ; Condition TANT QUE ; incrémentation du compteur
for($i = 0; $i < 10; $i++){
    //Code
    echo "!";
}
//Ici le code s'executera donc 10 fois.
//La boucle affichera : "!!!!!!!!!!"
```
Pour parcourir un tableau, comme en javascript, on doit récupérer la taille du tableau :
```php
//J'initialise un tableau scalaire contenant les valeurs "un", "deux", "trois", et "quatre"
$tableau = array("un", "deux", "trois", "quatre");

//je récupère la taille du tableau
//ATTENTION, les index du tableau sont bien 0, 1, 2, 3 > donc il y a bien 4 index dans le tableau, sizeof() renverra donc bien 4, et non 3.
$tailleTableau = sizeof($tableau);

//Je créé ma boucle for pour parcourir le tableau en me servant de ses index
for($i = 0; $i < $tailleTableau; $i++){

    //J'affiche la valeur du compteur dans le cycle
    echo $i.'-';

    //J'affiche la valeur de l'index donné par le compteur
    echo $tableau[$i].' ';

    //La boucle va recommencer, mais avec $i +1, comme indiqué dans le 3ème paramètre de la boucle for.
}

//La boucle affichera : "0-un 1-deux 2-trois 3-quatre ";
```
> [!WARNING]
> Attention, parcourir un tableau avec une boucle for ne peut se faire qu'avec un tableau associatif où **tous les index se suivent**. Sinon on préférera le foreach.
### Boucle foreach()
La boucle foreach est designée pour parcourir un tableau, associatif ou scalaire. "For each" en Anglais veut litérallement dire "Pour chaque", donc, pour chaque index d'un tableau.
Il existe en 2 formes très proches. La première où, pour chaque index on demmande au foreach de nous passer la valeur dans une variable : 
```php
//tableau associatif
$tableau = array("animal" => "chat", "poisson" => "requin", "insecte" => "fourmi");

//Pour chaque index du tableau associatif, on affiche la valeur correspondante
foreach($tableau as $valeur){//On peut changer le nom de la variable $valeur comme on le souhaite dans la syntaxe. Le foreach mettrea les valeurs du tableau dedans, une par une.

    //On affiche la valeur de l'index
    echo "$valeur ";
}

// le foreach affichera : "chat requin fourmi "
```
Dans la deuxième forme, on demmande au foreach de nous donner aussi une variable qui contiendra l'index (ou la clé) :
```php
//tableau associatif
$tableau = array("animal" => "chat", "poisson" => "requin", "insecte" => "fourmi");

//Pour chaque index du tableau associatif, on affiche l'index et la valeur correspondante
foreach($tableau as $index => $valeur){

    //On affiche l'index la valeur de l'index
    echo "$index=$valeur ";
}

// le foreach affichera : "animal=chat poisson=requin insecte=fourmi "
```