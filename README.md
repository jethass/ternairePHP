L'opérateur NULL coalecing  est une des nouvelles fonctionnalités disponibles depuis PHP 7.0 
Principe de fonctionnement, Concrètement, voici de quoi il s'agit :

$userRole = $_SESSION['user_role'] ?? 'unautenticated'
==> Si la variable $_SESSION['user_role'] n'est pas définie ou est égale à NULL, la valeur utilisée est donc la valeur de substitution fournie,
ici 'unautenticated'

Comparaison avec l'opérateur ternaire
Ça n'a l'air de rien mais avant il fallait utiliser un opérateur ternaire pour faire la même chose avec une syntaxe plus chargée :

$username = isset($_SESSION['user_role']) ? $_SESSION['user_role'] : 'unautenticated';


Il exite une forme plus simple et plus compacte pour l'opérateur ternaire qui ressemble beaucoup au NULL coalescing operator :
$userRole = $_SESSION['user_role'] ?: 'unautenticated';
Cependant celui-ci dispose d'un petit défaut bien embêtant : si la variable à gauche de l'opérateur n'est pas définie 
(en clair si la clef "user_role" n'existe pas dans l'array $_SESSION), PHP va produire une erreur de type notice.
On est donc contraint d'utiliser la première forme de l'opérateur ternaire et de protéger en utilisant un isset(_SESSION['user_role']) évitant ainsi l'erreur PHP.

L'opérateur NULL coalescent quant à lui n'a pas ce problème et utiliser une variable non définie ne lui posera aucun souci. 
C'est là un grand avantage par rapport à son cousin l'opérateur ternaire.
