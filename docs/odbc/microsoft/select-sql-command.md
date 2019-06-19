---
title: SELECT, commande SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- select [ODBC]
ms.assetid: 2149c3ca-3a71-446d-8d53-3d056e2f301a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0c2d991afa179fdfbb536853e302b33de8bf12e1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63127877"
---
# <a name="select---sql-command"></a>SELECT, commande SQL
Récupère les données à partir d’une ou plusieurs tables.  
  
 Le pilote ODBC Visual FoxPro prend en charge la syntaxe du langage Visual FoxPro native pour cette commande. Pour plus d’informations spécifiques au pilote, consultez **pilote notes**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [ALL | DISTINCT]  
   [Alias.] Select_Item [AS Column_Name]  
   [, [Alias.] Select_Item [AS Column_Name] ...]   
FROM [DatabaseName!]Table [Local_Alias]  
   [, [DatabaseName!]Table [Local_Alias] ...]   
[WHERE JoinCondition [AND JoinCondition  
...]  
   [AND | OR FilterCondition [AND | OR FilterCondition ...]]]  
[GROUP BY GroupColumn [, GroupColumn ...]]  
[HAVING FilterCondition]  
[UNION [ALL] SELECTCommand]  
[ORDER BY Order_Item [ASC | DESC] [, Order_Item [ASC | DESC] ...]]  
```  
  
## <a name="arguments"></a>Arguments  
  
> [!NOTE]  
>  Un *sous-requête*, fait référence dans les arguments suivants, est une instruction SELECT dans une instruction SELECT et doivent être placés entre parenthèses. Vous pouvez avoir jusqu'à deux sous-requêtes au même niveau (non imbriqué) dans la clause WHERE. (Voir la section des arguments). Sous-requêtes peuvent contenir plusieurs conditions de jointure.  
  
 [ALL &#124; DISTINCT]   [*Alias*.] *Select_Item* [AS *Column_Name*]    [, [*Alias*.] *Select_Item* [AS *Column_Name*] ...]  
 La clause SELECT spécifie les champs, les constantes et les expressions qui sont affichées dans les résultats de requête.  
  
 Par défaut, tous les affiche toutes les lignes dans les résultats de requête.  
  
 DISTINCT exclut les doublons de toutes les lignes de résultats de la requête.  
  
> [!NOTE]  
>  Vous pouvez utiliser DISTINCT qu’une seule fois par la clause SELECT.  
  
 *Alias*. qualifie les noms d’éléments correspondants. Chaque élément que vous spécifiez avec *Select_Item* génère une colonne de résultats de la requête. Si deux ou plusieurs éléments ont le même nom, inclure l’alias de table et un point avant le nom d’élément pour empêcher des colonnes d’être dupliquée.  
  
 *Select_Item* spécifie un élément à inclure dans les résultats de requête. Un élément peut être une des opérations suivantes :  
  
-   Le nom d’un champ d’une table dans la clause FROM.  
  
-   Constante spécifiant que la même valeur de constante doit s’afficher dans chaque ligne de résultats de la requête.  
  
-   Une expression qui peut être le nom d’une fonction définie par l’utilisateur.  
  
 **Fonctions définies par l’utilisateur avec SELECT**  
  
 Bien que l’utilisation de fonctions définies par l’utilisateur dans la clause SELECT présente des avantages évidents, vous devez également envisager les restrictions suivantes :  
  
-   La vitesse des opérations effectuées avec SELECT peut être limitée par la vitesse à laquelle ces fonctions définies par l’utilisateur sont exécutées. Manipulations de haut volume impliquant des fonctions définies par l’utilisateur peuvent mieux faire à l’aide des API et des fonctions définies par l’utilisateur écrites en C ou en langage assembleur.  
  
-   La seule méthode fiable pour transmettre des valeurs aux fonctions définies par l’utilisateur appelées à partir de SELECT consiste à la liste d’arguments passée à la fonction lorsqu’elle est appelée.  
  
-   Même si vous faire des essais et découvrez une manipulation censé être interdite qui fonctionne correctement dans une version spécifique de FoxPro, il n’existe aucune garantie qu’il continue de fonctionner dans les versions ultérieures.  
  
 En dehors de ces restrictions, les fonctions définies par l’utilisateur sont acceptables dans la clause SELECT. Toutefois, n’oubliez pas que l’utilisation de SELECT peut ralentir les performances.  
  
 Les fonctions de champ suivantes sont disponibles pour une utilisation avec un élément sélectionné est un champ ou une expression impliquant un champ :  
  
-   AVG (*Select_Item*)-moyenne d’une colonne de données numériques.  
  
-   NOMBRE (*Select_Item*)-compte le nombre de sélectionner des éléments dans une colonne. Count compte le nombre de lignes dans la sortie de requête.  
  
-   MIN (*Select_Item*)-détermine la plus petite valeur de *Select_Item* dans une colonne.  
  
-   MAX (*Select_Item*)-détermine la plus grande valeur de *Select_Item* dans une colonne.  
  
-   Somme (*Select_Item*)-additionne une colonne de données numériques.  
  
 Vous ne pouvez pas imbriquer des fonctions de champ.  
  
 AS *Column_Name*  
 Spécifie l’en-tête pour une colonne dans la sortie de requête. Cela est utile quand *Select_Item* est une expression ou contient un champ (fonction) et que vous souhaitez donner un nom explicite à la colonne. *Column_Name* peut être une expression, mais ne peut pas contenir de caractères (par exemple, les espaces) qui ne sont pas autorisées dans les noms de champ de table.  
  
 FROM [*DatabaseName*!]*Table* [*Local_Alias*]   [, [*DatabaseName*!]*Table* [*Local_Alias*] ...]  
 Répertorie les tables qui contiennent les données que la requête récupère. Si aucune table n’est ouvert, Visual FoxPro affiche le **ouvrir** afin que vous pouvez spécifier l’emplacement du fichier de boîte de dialogue. Une fois qu’il a été ouvert, la table reste ouverte après que la requête est terminée.  
  
 *DatabaseName*! Spécifie le nom d’une base de données autre que celui spécifié avec la source de données. Vous devez inclure le nom de la base de données qui contient la table si la base de données n’est pas spécifié avec la source de données. Inclure le séparateur de point d’exclamation ( !) après le nom de la base de données et avant le nom de table.  
  
 *Local_Alias* spécifie un nom temporaire pour la table nommée dans *Table*. Si vous spécifiez un alias local, vous devez utiliser l’alias local au lieu du nom de table tout au long de l’instruction SELECT. L’alias local n’affecte pas l’environnement Visual FoxPro.  
  
 OÙ *JoinCondition* [AND *JoinCondition* ...]    [AND &#124; ou *FilterCondition* [AND &#124; ou *FilterCondition* ...]]  
 Indique à Visual FoxPro pour inclure uniquement certains enregistrements dans les résultats de requête. OÙ est nécessaire pour récupérer des données provenant de plusieurs tables.  
  
 *JoinCondition* spécifie les champs qui lient les tables dans la clause FROM. Si vous incluez plusieurs tables dans une requête, vous devez spécifier une condition de jointure pour chaque table après le premier.  
  
> [!IMPORTANT]  
>  Lorsque vous créez des conditions de jointure, tenez compte des informations suivantes :  
  
-   Si vous incluez des deux tables dans une requête et que vous ne spécifiez pas une condition de jointure, chaque enregistrement de la première table est jointe à chaque enregistrement dans la seconde table tant que les conditions du filtre. Une telle requête peut produire des résultats relativement longue.  
  
-   Soyez prudent lorsque vous joignez des tables avec des champs vides, car Visual FoxPro correspond aux champs vides. Par exemple, si vous joindre sur la table CUSTOMER. ZIP et facture. Code postal et si le client contient 100 codes postaux vides et facture contient des codes postaux vides 400, la sortie de requête contient 40 000 enregistrements supplémentaires résultant à partir des champs vides. Utilisez le **vide ()** (fonction) pour éliminer les enregistrements vides à partir de la sortie de requête.  
  
-   Vous devez utiliser l’opérateur AND pour connecter plusieurs conditions de jointure. Chaque condition de jointure a la forme suivante :  
  
     *FieldName1 FieldName2 de comparaison*  
  
     *FieldName1* est le nom d’un champ d’une table, *FieldName2* est le nom d’un champ à partir d’une autre table, et *comparaison* est un des opérateurs décrits dans le tableau suivant.  
  
|Opérateur|Comparaison|  
|--------------|----------------|  
|=|Égal à|  
|==|Exactement égal à|  
|LIKE|SIMILAIRE À SQL|  
|<>, !=, #|Non égal|  
|>|Plus de|  
|>=|Supérieur ou égal à|  
|<|Inférieur à|  
|<=|Inférieur ou égal à|  
  
 Lorsque vous utilisez l’opérateur = avec des chaînes, il se comporte différemment, selon le paramètre de SET ANSI. Lorsque SET ANSI est définie sur OFF, Visual FoxPro traite les comparaisons de chaînes de manière familière aux utilisateurs de Xbase. Lorsque SET ANSI est définie sur ON, Visual FoxPro suit les normes ANSI pour les comparaisons de chaînes. Consultez [SET ANSI](../../odbc/microsoft/set-ansi-command.md) et [SET EXACT](../../odbc/microsoft/set-exact-command.md) pour plus d’informations sur la façon dont Visual FoxPro effectue des comparaisons de chaînes.  
  
 *FilterCondition* spécifie les critères que les enregistrements doivent satisfaire pour être inclus dans les résultats de requête. Vous pouvez inclure autant de conditions dans une requête de filtre que vous le souhaitez, connectant à l’opération AND ou opérateur OR. Vous pouvez également utiliser l’opérateur NOT pour inverser la valeur d’une expression logique, ou vous pouvez utiliser **() vide** à vérifier pour un champ vide. *FilterCondition* peut prendre une des formes dans les exemples suivants :  
  
 **Exemple 1** *FieldName1 FieldName2 de comparaison*  
  
 `customer.cust_id = orders.cust_id`  
  
 **Exemple 2** *Expression de comparaison de FieldName*  
  
 `payments.amount >= 1000`  
  
 **Exemple 3** *FieldName comparaison* toutes les (*sous-requête*)  
  
 `company < ALL ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 Lorsque la condition de filtre inclut tous, le champ doit respecter la condition de comparaison pour toutes les valeurs générées par la sous-requête avant son enregistrement est inclus dans les résultats de requête.  
  
 **Exemple 4** *FieldName comparaison* ANY &#124; certains (*sous-requête*)  
  
 `company < ANY ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 Lorsque la condition de filtre inclut tout ou partie, le champ doit respecter la condition de comparaison pour au moins une des valeurs générées par la sous-requête.  
  
 L’exemple suivant vérifie si les valeurs dans le champ sont dans une plage spécifiée de valeurs :  
  
 **Exemple 5** *FieldName* [NOT] entre *Start_Range* AND *End_Range*  
  
 `customer.postalcode BETWEEN 90000 AND 99999`  
  
 L’exemple suivant vérifie si au moins une ligne répond aux critères de la sous-requête. Lorsque la condition de filtre inclut EXISTS, la condition de filtre a la valeur True (. T.), sauf si la sous-requête renvoie le jeu vide.  
  
 **Exemple 6** [NOT] existe (*sous-requête*)  
  
 `EXISTS ;`  
  
 `(SELECT * FROM orders WHERE customer.postalcode =`  
  
 `orders.postalcode)`  
  
 **Exemple 7** *FieldName* [NOT] IN *Value_Set*  
  
 `customer.postalcode NOT IN ("98052","98072","98034")`  
  
 Lorsque la condition de filtre inclut IN, le champ doit contenir une des valeurs avant son enregistrement est inclus dans les résultats de requête.  
  
 **Exemple 8** *FieldName* [NOT] IN (*sous-requête*)  
  
 `customer.cust_id IN ;`  
  
 `(SELECT orders.cust_id FROM orders WHERE orders.city="Seattle")`  
  
 Ici, le champ doit contenir une des valeurs retournées par la sous-requête avant son enregistrement est inclus dans les résultats de requête.  
  
 **Exemple 9** *FieldName* [NOT] comme *cExpression*  
  
 `customer.country NOT LIKE "USA"`  
  
 Cette condition de filtre recherche chaque champ qui correspond à *cExpression*. Vous pouvez utiliser le symbole de pourcentage (%) et des caractères génériques de trait de soulignement (_) dans le cadre de *cExpression*. Le trait de soulignement représente un seul caractère inconnu dans la chaîne.  
  
 GROUP BY *GroupColumn* [, *GroupColumn* ...]  
 Groupes de lignes dans la requête en fonction des valeurs dans une ou plusieurs colonnes. *GroupColumn* peut prendre l’une des opérations suivantes :  
  
-   Le nom d’un champ de table standard.  
  
-   Un champ qui inclut une fonction de champ SQL.  
  
-   Une expression numérique qui indique l’emplacement de la colonne dans la table de résultats. (Le numéro de colonne à l’extrême gauche est 1.)  
  
 AVOIR *FilterCondition*  
 Spécifie une condition de filtre que les groupes doivent satisfaire pour être inclus dans les résultats de requête. HAVING doit être utilisé avec GROUP BY et peuvent inclure autant de conditions de filtre que vous le souhaitez, connectés par AND ou opérateur OR. Vous pouvez également utiliser ne pas pour inverser la valeur d’une expression logique.  
  
 *FilterCondition* ne peut pas contenir de sous-requête.  
  
 Une clause HAVING sans une clause GROUP BY se comporte comme une clause WHERE. Vous pouvez utiliser des alias locales et les fonctions de champ dans la clause HAVING. Utilisez une clause WHERE pour accélérer les performances si votre clause HAVING ne contient aucune fonction de champ.  
  
 [UNION [ALL] *SELECTCommand*]  
 Combine les résultats finaux d’un sélectionner avec les résultats finaux de sélectionner un autre. Par défaut, UNION vérifie les résultats combinés et élimine les lignes en double. Utilisez des parenthèses pour combiner plusieurs clauses UNION.  
  
 UNION tous les empêche d’élimination des doublons des résultats combinés.  
  
 Clauses UNION suivent ces règles :  
  
-   Vous ne pouvez pas utiliser UNION pour combiner des sous-requêtes.  
  
-   Les deux commandes de sélection doivent avoir le même nombre de colonnes dans la sortie de la requête.  
  
-   Chaque colonne dans les résultats de requête de, un sélectionnez doit avoir le même type de données et la largeur que la colonne correspondante dans l’autre instruction SELECT.  
  
-   Uniquement l’instruction SELECT finale peut avoir une clause ORDER BY, lequel doit faire référence aux colonnes de sortie en nombre. Si une clause ORDER BY est incluse, elle affecte le résultat complet.  
  
 Vous pouvez également utiliser la clause UNION pour simuler une jointure externe.  
  
 Lorsque vous joignez deux tables dans une requête, seuls les enregistrements avec les valeurs correspondantes dans les champs de jointure sont inclus dans la sortie. Si un enregistrement dans la table parente n’a pas d’un enregistrement correspondant dans la table enfant, l’enregistrement dans la table parente n’est pas inclus dans la sortie. Une jointure externe vous permet d’inclure tous les enregistrements dans la table parente dans la sortie, ainsi que les enregistrements correspondants dans la table enfant. Pour créer une jointure externe dans Visual FoxPro, vous devez utiliser une commande SELECT imbriquée, comme dans l’exemple suivant :  
  
```  
SELECT customer.company, orders.order_id, orders.emp_id ;  
FROM customer, orders ;  
WHERE customer.cust_id = orders.cust_id ;  
UNION ;  
SELECT customer.company, 0, 0 ;  
FROM customer ;  
WHERE customer.cust_id NOT IN ;  
(SELECT orders.cust_id FROM orders)  
```  
  
> [!NOTE]  
>  Assurez-vous que vous incluez l’espace qui précède immédiatement chaque point-virgule. Sinon, vous recevrez une erreur.  
  
 La section de la commande avant la clause UNION sélectionne les enregistrements des deux tables qui ont des valeurs correspondantes. Les sociétés de client qui n’ont pas de factures associées ne sont pas incluses. La section de la commande après la clause UNION sélectionne des enregistrements dans la table customer qui n’ont pas d’enregistrements correspondants dans la table orders.  
  
 Concernant la deuxième section de la commande, notez les points suivants :  
  
-   L’instruction SELECT entre parenthèses est traitée en premier. Cette instruction crée une sélection de tous les numéros de client dans la table orders.  
  
-   La clause WHERE recherche tous les numéros de client dans la table customer qui ne sont pas dans la table orders. Étant donné que la première section de la commande fourni toutes les entreprises ayant un numéro de client dans la table orders, toutes les entreprises dans la table customer sont désormais inclus dans les résultats de requête.  
  
-   Étant donné que les structures des tables incluses dans une UNION doivent être identiques, il existe deux espaces réservés dans la seconde instruction SELECT pour représenter *orders.order_id* et *orders.emp_id* à partir de la première instruction SELECT instruction.  
  
    > [!NOTE]  
    >  Les espaces réservés doivent être du même type que les champs qu’ils représentent. Si le champ est un type de date, l’espace réservé doit être {/ /}. Si le champ est un champ de texte, l’espace réservé doit être une chaîne vide ( » »).  
  
 ORDER BY *Order_Item* [ASC &#124; DESC] [, *Order_Item* [ASC &#124; DESC] ...]  
 Trie les résultats de requête basés sur les données dans une ou plusieurs colonnes. Chaque *Order_Item* doit correspondre à une colonne dans les résultats de requête et peut prendre l’une des opérations suivantes :  
  
-   Un champ dans une table de départ qui est également un élément sélectionné dans la clause SELECT principal (pas dans une sous-requête).  
  
-   Une expression numérique qui indique l’emplacement de la colonne dans la table de résultats. (La colonne de gauche est le numérique 1.)  
  
 ASC spécifie un ordre croissant des résultats de requête, en fonction de l’ordre ou les éléments et est la valeur par défaut pour ORDER BY.  
  
 DESC spécifie un ordre décroissant pour les résultats de la requête.  
  
 Résultats de la requête apparaissent non triées, si vous ne spécifiez pas une commande avec ORDER BY.  
  
## <a name="remarks"></a>Notes  
 Sélectionnez est une commande SQL qui est intégrée à Visual FoxPro comme n’importe quel autre commande de Visual FoxPro. Lorsque vous utilisez, sélectionnez cette option pour poser une requête, Visual FoxPro interprète la requête et récupère les données spécifiées à partir des tables. Vous pouvez créer une requête SELECT à partir de la fenêtre d’invite de commandes ou un programme Visual FoxPro (comme avec toute autre commande Visual FoxPro).  
  
> [!NOTE]  
>  Sélectionnez ne respecte pas la condition de filtre actuel spécifiée par définir le filtre.  
  
## <a name="driver-remarks"></a>Notes de pilote  
 Lorsque votre application envoie l’instruction ODBC SQL SELECT à la source de données, le pilote ODBC Visual FoxPro convertit la commande dans la ligne de commande Visual FoxPro sélectionner sans traduction, sauf si la commande contient une séquence d’échappement ODBC. Les éléments entre dans une séquence d’échappement ODBC sont convertis en syntaxe de Visual FoxPro. Pour plus d’informations sur l’utilisation d’ODBC des séquences d’échappement, consultez [fonctions d’heure et Date](../../odbc/microsoft/time-and-date-functions-visual-foxpro-odbc-driver.md) et dans le *de référence du programmeur ODBC de Microsoft*, consultez [les séquences d’échappement dans ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE TABLE, SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT - SQL](../../odbc/microsoft/insert-sql-command.md)   
 [SET ANSI](../../odbc/microsoft/set-ansi-command.md)   
 [SET EXACT](../../odbc/microsoft/set-exact-command.md)
