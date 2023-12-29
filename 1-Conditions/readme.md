# Exercices sur les conditions
> [!NOTE]
> Vous pouvez vous référer à la doc dans ce répertoire : doc-explications.md
> Si vous n'avec pas devilbox ou apache, testez votre code sur https://extendsclass.com/fr/php.html

1)
- Créer une variable $nb qui vaut 4.
- Afficher la variable **si** elle est **strictement supérieure** à **3**

2)
- Reprendre le code de l'exercice 1, afficher la variable si elle est strictement supérieure à 3.
- A la suite (en dehors du bloc précédent) : Afficher la variable Si elle est inférieure ou égale à 3 (sans else)
- Tester. Si ça fonctionne, changez la valeur de $nb pour 2 et re-tester.

3)
- Créer une variable qui vaut un chiffre nombre entre 1 et 10.
- **Si** La variable est **égale** à 5, afficher : "La variable vaut 5".
- **Sinon** afficher : "La variable est différente de 5"
- Vous pouvez executer plusieurs fois le code pour voir s'il affiche bien les 2 conditions.

4)
- Reprendre le code de l'exercice précédent, mais inverser la première condition, et changez les affichages en conséquence :
- **Si** la variable n'est **pas égale** (ou **différente**) de 5, afficher : "La variable est différente de 5".
- **Sinon** afficher : "La variable vaut 5".
- Vous pouvez executer plusieurs fois le code pour voir s'il affiche bien les 2 conditions.

5)
> [!NOTE]
> Utilisez les opérateurs logique && ou ||

- Créer une variable $nb aléatoire entre 0 et 20.
- Afficher la string "Votre notation : "
- **Si** la variable $nb est inférieure à 5, afficher "Médiocre :("
- **Ou si** la variable vaute entre 5 et 9, afficher "Pas top..."
- **Ou si** la variable vaut entre 10 et 14, afficher "Bien !"
- **Sinon** afficher "Fantastique !"
- Faire un var_dump() de $nb à la fin (hors des blocs) qui s'affichera dans tous les cas.

6)
- Même exercice que le précédent, mais n'utilisez aucun opérateur logique && ou || (Indice dans la doc doc-explications.md)

7)
- initialiser une variable $nb avec un chiffre aléatoire entre 0 et 1
- si $nb est différent de faux, afficher : "C'est vrai !"
- Sinon afficher "C'es faux !";
- A la suite, dans tous les cas faire un var_dump() de $nb.
- Indice : Mieux vaut ne pas vérifier le typage, $nb n'est pas strictement un booléen vrai ou faux, mais un équivalent int...

8)
- Initialiser une variable $txt avec la string "les petits poissons"
- Initialiser une variable $trouve avec la string "pois"
- $trouve existe dans la variable $txt, afficher : "Trouvé !";
> [!TIP]
> Pour trouver si un caractère ou une chaîne de caractères (donc une string), est présent dans une autre string, utilisez strpos().
> strpos() est une fonction php qui vous renvoie où se trouve la string recherchée.
> Exmple : strpo("Chaîne de caractère", "de") renverra 7. Si la string à trouver n'existe pas, la fonction renvoie false.
> https://www.php.net/manual/fr/function.strpos.php
- Une fois que le code fonctionne, changer le contenu de la variable $trouve. Maintenant $trouve contient "les". Si le code ne marche plus, n'hésitez pas à var_dump() votre fonction strpos() !