> [!NOTE]
> Tableau se dit Array en Anglais, terme important pour les recherches dans la doc.

## Intro
- Il y a 2 types de tableaux sur php, qui se ressemblent beaucoup. Les tableaux scalaires et les tableaux associatifs.
- Ils se différencient de par leur type d'index.
    - L'index (ou clé) permet d'accéder à divers contenu du tableau. Comme si le tableau était une banque, on a des clés, pour aller chercher le contenu des coffres de la banque (valeur).
- On utilise les crochets [ ] pour accéder au contenu du tableau (au coffres de la banque)

## TABLEAU SCALAIRE
Les index sont toujours des nombres (intege, int), la plupart du temps ces nombres se suivent à partir de 0, mais ce n'est pas une obligation.
```php
//Je déclare un tableau avec 3 valeurs
$animaux = array("chat", "chien", "souris"); 
```

Un tableau $banque s'est initialisé avec 3 clés automatiques, qui contiennent les valeurs "chat", "chien", et "souris".
> Comment on sait quelle est le nom des clés qui ont été créées pour quelle valeur ?
C'est toujours dans le même ordre. La première valeur ("chat") prend la clé O, la deuxième valeur ("chien") prend la clé 1, la 3ème prend la clé 2, et ainsi de suite pour chaque valeur.
On peu vérifier le contenu avec un var_dump() du tableau nous affichera les clés entre crochet, et les valeurs qu'elles contiennent.

### ACCES AU VALEURS
```php
//Je créé une variable chat qui va contenir la valeur de l'index 0 du tableau $animaux, donc "chat"
//C'est une copie, le chat n'est pas effacé du tableau
$chat = $animaux[0];

//Je remplace la valeur de l'index 2 dans le tableau $animaux. Après ça "souris" n'existe plus dans le tableau $animaux, il y a "Elephant" à la place.
$animaux[2]="Elephant";

//Le tableau $animaux contient maintenant [0]=>"chat", [1]=>"chien", [2]=>"Elephant"

//J'ajoute une valeur au tableau
$animaux[]="poule" //Les crochets vide signifie que php va créer un index à la suite du dernier index. Si le dernier index du tableau est 2 comme ici, l'index de "poule" sera 3.
```

## TABLEAU ASSOCIATIF
Même principe que le tableau scalaire, mais les index (clés) peut être des "chaines de caractère (string)".
```php
//On déclare un tableau associatif, on doit donc utiliser une syntaxe pour créer les index, vu que ce ne sont plus forcément des nombres (int), ça peut être ce qu'on veut.
$tableauAssoc("cle1" => "valeur de cle1", "cle2" => "valeur de cle2");

//Si la clé n'est pas un nombre (int), alors ce sera TOUJOURS une string.
//Je peux accéder à la valeur du tableau associatif comme ceci :
$valeur = $tableauAssoc["cle1"]; // $valeur contiendra "valeur de cle1";

//Donc on modifie la valeur comme ceci :
$tableauAssoc["cle1"] = "Une autre valeur";

//$tableauAssoc contient donc maintenant ["cle1"]=>"Une autre valeur", ["cle2"]=>"valeur de cle2"

//J'ajoute une clé et sa valeur au tableau
$tableauAssoc["cle368"]="Ceci est la clé 368";

//$tableauAssoc contient donc maintenant ["cle1"]=>"Une autre valeur", ["cle2"]=>"valeur de cle2", $tableauAssoc["cle368"]="Ceci est la clé 368"
```
> [!NOTE]
> Note : On parcourira les tableaux quand on fera les boucles, il faut que cette partie soit intégrée à 100%