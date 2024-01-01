# Qu'est-ce qu'un objet ?
Comme un type de variable qui possède des fonctions appelées **méthodes**, et des variables internes appelées **attributs** ou **propriétés**, qui sont **publique** ou **privés**.
Il est déclaré (créé) sous forme de **classe**, la classe est comme un modèle pour instancier un objet.
> [!IMPORTANT]
> Il faut retenir que la **classe** est le **modèle**, tandis que l'**objet** est la variable **instanciée** (new) de la classe, qu'on utilise concrètement dans le code.
```php
//Créer une classe Humain qui nous permettra d'instancier un objet. C'est comme un modèle de ce que sera l'objet instancié depuis cette classe.
class Humain
{
    //Attribut de type publique, donc accessible dirrectement après avoir instancié l'objet.
    public $_nom = "Zelda"

    //Attribut de type privé, donc accessible uniquement à l'intreieur de la classe, donc via une méthode
    private $_compteEnBanque = "RIB FR00078973"

    //Méthode de type publique, c'est une sorte de fonction que l'objet peut appeler.
    public function AfficherCompteEnBanque(){

        //On affiche le contenu de l'attribut $_compteEnBanque
        echo "Mon rib est secret, c'est le No : ".$this->_compteEnBanque;// $this fait référence à la classe dans laquelle on est. -> est la syntaxe pour appeler un attribut A L'INTERIEUR d'une classe. Donc : cette classe->le nom de l'attribut attribut
    }
}

//Instanciation de la classe Humain, on créée un objet de type Humain :
$humain = new Humain();// Le new créée un objet de la classe, ici de la classe Humain.


//Dans l'objet humain, j'appelle l'attribut _nom
echo $humain->_nom // Affichera : "Zelda"

//Dans l'objet humain, j'appelle l'attribut $_compteEnBanque
echo $humain->_compteEnBanque // ERREUR : On essaye d'accéder directement à un attribut privé (private), l'attribut ne s'affichera pas.

//Dans l'objet humain, j'appelle la méthode AfficherCompteEnBanque() (une méthode est très similaire à une fonction)
//L'attribut $_compteEnBanque est privé, mais il est appelé à l'intérieur d'une méthode de l'objet $humain, donc la méthode a le droit d'y accéder
$humain->AfficherCompteEnBanque(); // Affichera : "Mon rib est secret, c'est le No : RIB FR00078973"
```
## Le constructeur
Le constructeur fait partie des **fonctions magiques**. Les méthodes magiques sont des méthodes qui sont liés à des événements de l'objet.
Le constructeur est appelé lorsqu'on instancie un objet (avec **new**).
```php
class Parler
{
    
    // initialisation d'un constructeur, il sera appelé quand on instancie un objet Parler
    public function __construct($string){// La méthode admet un paramètre d'entrée, mais comme une fonction, ce n'est pas obligatoire. 
        echo "Je suis instancié ! $string";
    }
}
// J'instancie un nouvel objet
$objetParle = new Parler("Je passe une string !"); // Affiche : "Je suis instancié ! Je passe une string !"
```
Voilà ce qu'on avait besoin des objets pour comprendre le fonctionnement de PDO.
## PDO
PDO est un **objet** qui sert à établir une **connexion** à une base de données. Il possède donc de nombreux attributs qui serviront de paramètres, et méthodes qui serviront à dialoguer avec la base de données via des requêtes SQL.
### Le constructeur de PDO
Le constructeur de PDO attend une châine de connexion (connection string) qui indique à PDO où et comment se connecter à la base de données.
La chaîne de connexion peut-être de différentes formes et le constructeur peut accepter plusieurs paramètre optionels, on va donc se cocnentrer sur une forme standard.
```php
//Je créée ma connexion à la base de données sur l'ordinateur local
//Premier paramètre : La chaîne de connexion = [sgbd]:host=[AdresseDeLaBdd];dbname=[NomDeLaBdd]
//2ème et 3ème paramètres, identifiant et mot de passe du compte qui souhaite se connecter.
$objetPDO = new PDO('mysql:host=127.0.0.1;dbname=MaBdd', "utilisateur", "mot de passe");

// On peut préférer de passer des variables à PDO, pour simplifier le changement de Bdd ou d'utilisateur
// Exemple :

$sgbd = "mysql";
$adresse = "127.0.0.1";
$nomBdd = "MaBdd";
$utilisateur = "utilisateur";
$mdp = "mot de passe";

$objetPDO = new PDO($sgbd.':host='.$adresse.';dbname='$nomBdd, $utilisateur, $mdp);
```
Nous sommes connectés, maintenant on peut utiliser les **méthodes** de PDO pour envoyer des requêtes.
### Méthode query
La méthode la plus simple pour envoyer une requête à la base de données, c'est query().
Attention, cette méthode n'est pas toujours conseillée car elle est vulnérable aux injections SQL.
> [!NOTE]
> L'injection SQL est l'écriture de code SQL par l'utilisateur là où on ne l'attends pas. Par exemple si je rentre (drop table user) quand on me demmande mon nom dans un formulaire, s'il existe la table user, elle va se vider car le code SQL va être interprété par la base de données.
Cependant dans le cadre d'exercice, la méthode query est parfaite pour travailler les requêtes avec la Bdd, pour comprendre le contexte, car elle execute la requête directement.
Elle renvoie un false si elle n'a pas réussi à éxécuter la requête.
```php
// J'instancie un objet PDO avec les paramètres de connexion.
$objetPDO = new PDO('mysql:host=127.0.0.1;dbname=MaBdd', "utilisateur", "mot de passe");

// J'utilise la méthode query de $objetPDO, dans laquelle je passe une requête SQL sous forme de string
$objetPDO->query("INSERT INTO table1 VALUES('colonne1', 'colonne2')");

// Comme pour le constructeur, on préfére générallement initialiser une variable avec la requête SQL.
// Exemple avec une autre méthode :

//Je créé la variable qui contiendra la requêtes SQL, c'est plus lisible.
$sql = "INSERT INTO table1 VALUES('colonne1', 'colonne2')";

// J'execute la requête avec la méthode query de l'objet PDO
$objetPDO->query($sql);

// Si la requête échoue, on peut le savoir, car query() renvoie un false dans ce cas. Ne pas oublier le ! pour inverser la condition
if(!$objetPDO->query($sql)){

    // Si la méthode query renvoie une erreur, on affiche :
    echo "<p>La requête <b>$sql</b> a échoué</p>";

    // La méthode errorInfo() renvoie un tableau avec le retour de l'erreur SQL, avec un code et une description (comme sur phpmyadmin)
    echo "<pre>".print_r($objetPDO->errorInfo())."</pre>";

}
```
### Valeur de retour de la méthode query
Quand on fait un UPDATE, INSRT INTO, OU DELETE, on n'a pas besoin de récupérer une réponse de la base de données.
En revanche si on fait un SELECT, on attend des données en retour.
La méthode query() dans ce cas va renvoyer **un autre objet** (PDOStatement https://www.php.net/manual/fr/class.pdostatement.php) contenant ces valeurs, et des **méthodes** pour transposer ces valeurs en une variable plus lisible (en tableau générallement).

Avec la méthode fetch() :
```php
// J'instancie un objet PDO pour me connecter à la Bdd
$objetPDO = new PDO('mysql:host=127.0.0.1;dbname=MaBdd', "utilisateur", "mot de passe");

// Je construit une requête
$sql = "SELECT * FROM uneTable";

// J'execute la requête SQL via la méthode query, et je récupère le résultat dans une variable. Si query() réussit à faire sa requete, ce sera un objet, sinon ce sera false
$objetDeDonnees = $objetPDO->query($sql);

// Si la requête renvoie un objet, la requête a fonctionné.
if($objetDeDonnees){ // l'objet sera considéré come true par php dans une condition, car ce qui n'est pas un booléen et true par défaut.

    // fetch() va créer un tableau pour chaque LIGNE de la table, on le récupère dans $tableauLigne, et on le lit dans un while.
    // Quand il n'y aura plus de ligne à lire, fetch() va renvoyer null (vide) à $tableauLigne, et le while va considérer null comme false, donc sortir de la boucle.
    while($tableauLigne = $objetDeDonnees->fetch(PDO::FETCH_ASSOC)){//PDO::FETCH_ASSOC : on veut un tablau associatif avec le nom des cononnes en tant qu'index.

        //On affiche la valeur. Pour la ligne donnée par fetch(), on a la colonne dans l'index du tableau $tableauLigne.
        echo "<p>".$tableauLigne["NomColonne"]."</p>";
    }
}
else{// Si $objetDonnees est false, on rentrera ici

    echo "<p>Erreur de requête : </p><pre>".print_r($objetPDO->errorInfo())."</pre>";
}
```