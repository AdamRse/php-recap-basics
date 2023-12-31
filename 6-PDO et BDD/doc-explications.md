# Qu'est-ce qu'un objet ?
Comme un type de variable qui possède des fonctions appelées **méthodes**, et des variables internes appelées **attributs** ou **propriétés**, qui sont **publique** ou **privés**.
Il est déclaré (créé) sous forme de classe :
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
## PDO
PDO est un **objet** PHP qui sert à établir une connexion à une base de données. Il possède donc de nombreux attributs qui serviront de paramètres, et méthodes qui serviront à dialoguer avec la base de données.
