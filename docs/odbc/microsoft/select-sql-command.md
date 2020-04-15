---
title: SELECT - Commandement SQL Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 640189a5a31d0c21642b037e906bd6361690a9a5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300939"
---
# <a name="select---sql-command"></a>SELECT, commande SQL
Récupère les données d’une ou plusieurs tables.  
  
 Le Visual FoxPro ODBC Driver prend en charge la syntaxe en langue visuelle FoxPro native pour cette commande. Pour obtenir des renseignements spécifiques au conducteur, consultez **les remarques du conducteur**.  
  
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
>  Une *sous-fertilité*, mentionnée dans les arguments suivants, est un SELECT dans un SELECT et doit être enfermée entre parenthèses. Vous pouvez avoir jusqu’à deux sous-ques au même niveau (non imbriqué) dans la clause WHERE. (Voir cet article des arguments.) Les sous-ques peuvent contenir plusieurs conditions de jointure.  
  
 [TOUS &#124; DISTINCT]   [*Alias*.] *Select_Item* [AS *Column_Name*] [, [*Alias*.] *Select_Item* [AS *Column_Name*] ...]  
 La clause SELECT spécifie les champs, les constantes et les expressions qui sont affichés dans les résultats de la requête.  
  
 Par défaut, TOUS affiche toutes les lignes dans les résultats de la requête.  
  
 DISTINCT exclut les doublons de toutes les lignes des résultats de la requête.  
  
> [!NOTE]  
>  Vous ne pouvez utiliser DISTINCT qu’une seule fois par clause SELECT.  
  
 *Alias*. qualifie les noms d’objets correspondants. Chaque élément que vous spécifiez avec *Select_Item* génère une colonne des résultats de la requête. Si deux éléments ou plus ont le même nom, inclure le pseudonyme de table et une période avant le nom de l’élément pour empêcher les colonnes d’être dupliquées.  
  
 *Select_Item* spécifie un élément à inclure dans les résultats de la requête. Un élément peut être l’un des éléments suivants :  
  
-   Le nom d’un champ à partir d’une table de la clause FROM.  
  
-   Une constante spécifiant que la même valeur constante doit apparaître dans chaque rangée des résultats de la requête.  
  
-   Une expression qui peut être le nom d’une fonction définie par l’utilisateur.  
  
 **Fonctions définies par l’utilisateur avec SELECT**  
  
 Bien que l’utilisation de fonctions définies par l’utilisateur dans la clause SELECT présente des avantages évidents, vous devez également tenir compte des restrictions suivantes :  
  
-   La vitesse des opérations effectuées avec SELECT peut être limitée par la vitesse à laquelle ces fonctions définies par l’utilisateur sont exécutées. Les manipulations à volume élevé impliquant des fonctions définies par l’utilisateur pourraient être mieux réalisées en utilisant l’API et les fonctions définies par l’utilisateur écrites en C ou en langage d’assemblage.  
  
-   La seule façon fiable de transmettre des valeurs aux fonctions définies par l’utilisateur invoquées par SELECT est par la liste d’argumentation transmise à la fonction lorsqu’elle est invoquée.  
  
-   Même si vous expérimentez et découvrez une manipulation soi-disant interdite qui fonctionne correctement dans une certaine version de FoxPro, il n’y a aucune garantie qu’elle continuera à fonctionner dans les versions ultérieures.  
  
 Outre ces restrictions, les fonctions définies par l’utilisateur sont acceptables dans la clause SELECT. Cependant, n’oubliez pas que l’utilisation de SELECT peut ralentir les performances.  
  
 Les fonctions de champ suivantes sont disponibles pour une utilisation avec un élément sélectionné qui est un champ ou une expression impliquant un champ :  
  
-   AVG (*Select_Item*)-Moyennes d’une colonne de données numériques.  
  
-   COUNT (*Select_Item*)-Compte le nombre d’éléments sélectionnés dans une colonne. COUNT)compte le nombre de lignes dans la sortie de requête.  
  
-   MIN (*Select_Item*)-Détermine la plus petite valeur de *Select_Item* dans une colonne.  
  
-   MAX (*Select_Item*) -Détermine la plus grande valeur de *Select_Item* dans une colonne.  
  
-   SUM (*Select_Item*)-Totalise une colonne de données numériques.  
  
 Vous ne pouvez pas nicher les fonctions de champ.  
  
 AS *Column_Name*  
 Spécifie la rubrique pour une colonne dans la sortie de requête. Ceci est utile lorsque *Select_Item* est une expression ou contient une fonction de champ et que vous voulez donner à la colonne un nom significatif. *Column_Name* peut être une expression mais ne peut pas contenir des caractères (par exemple, des espaces) qui ne sont pas autorisés dans les noms de champ de table.  
  
 DE [*DatabaseName*!] *Tableau* [*Local_Alias*] [, [*DatabaseName*!] *Tableau* *[Local_Alias*] ...]  
 Répertorie les tableaux qui contiennent les données que la requête récupère. Si aucune table n’est ouverte, Visual FoxPro affiche la boîte de dialogue **Ouverte** afin que vous puissiez spécifier l’emplacement du fichier. Une fois qu’elle a été ouverte, la table reste ouverte après la fin de la requête.  
  
 *DatabaseName*! spécifie le nom d’une base de données autre que celle spécifiée avec la source de données. Vous devez inclure le nom de la base de données qui contient la table si la base de données n’est pas spécifiée avec la source de données. Inclure le point d’exclamation (!) delimiter après le nom de la base de données et avant le nom de table.  
  
 *Local_Alias* spécifie un nom temporaire pour la table nommée dans *le tableau*. Si vous spécifiez un pseudonyme local, vous devez utiliser le pseudonyme local au lieu du nom de table tout au long de la déclaration SELECT. Le pseudonyme local n’affecte pas l’environnement Visual FoxPro.  
  
 Où *JoinCondition* [ET *JoinCondition* ...]    [ET &#124; OU *FilterCondition* [ET &#124; OU *FilterCondition* ...]]  
 Indique à Visual FoxPro d’inclure uniquement certains enregistrements dans les résultats de la requête. Où est nécessaire pour récupérer les données de plusieurs tables.  
  
 *JoinCondition* spécifie les champs qui relient les tables dans la clause FROM. Si vous incluez plus d’une table dans une requête, vous devez spécifier une condition de jointure pour chaque table après la première.  
  
> [!IMPORTANT]  
>  Considérez les informations suivantes lorsque vous créez des conditions de jointure :  
  
-   Si vous incluez deux tables dans une requête et ne spécifiez pas une condition de jointure, chaque enregistrement dans le premier tableau est joint à chaque enregistrement dans le deuxième tableau tant que les conditions de filtre sont remplies. Une telle requête peut produire de longs résultats.  
  
-   Faites preuve de prudence lorsque vous vous joignez à des tables avec des champs vides parce que Visual FoxPro correspond à des champs vides. Par exemple, si vous vous joignez à CUSTOMER. ZIP ET INVOICE. ZIP et si CUSTOMER contient 100 codes postaux vides et QUE INVOICE contient 400 codes postaux vides, la sortie de requête contient 40 000 enregistrements supplémentaires résultant des champs vides. Utilisez la fonction **EMPTY)** pour éliminer les enregistrements vides de la sortie de requête.  
  
-   Vous devez utiliser l’opérateur ET pour connecter plusieurs conditions de jointure. Chaque condition de jointure a la forme suivante :  
  
     *FieldName1 Comparaison FieldName2*  
  
     *FieldName1* est le nom d’un champ d’une table, *FieldName2* est le nom d’un champ d’une autre table, et *La comparaison* est l’un des opérateurs décrits dans le tableau suivant.  
  
|Opérateur|Comparaison|  
|--------------|----------------|  
|=|Égal à|  
|==|Exactement égal|  
|LIKE|SQL COMME|  
|<>, ! #|Non égal à|  
|>|Plus de|  
|>=|Plus ou égal à|  
|<|Inférieur à|  
|<=|Inférieur ou égal à|  
  
 Lorsque vous utilisez l’opérateur avec des cordes, il agit différemment, en fonction du réglage de SET ANSI. Lorsque SET ANSI est configuré à OFF, Visual FoxPro traite les comparaisons de chaînes d’une manière familière aux utilisateurs de Xbase. Lorsque SET ANSI est configuré sur ON, Visual FoxPro suit les normes ANSI pour les comparaisons de chaînes. Voir [SET ANSI](../../odbc/microsoft/set-ansi-command.md) et [SET EXACT](../../odbc/microsoft/set-exact-command.md) pour plus d’informations sur la façon dont Visual FoxPro effectue des comparaisons de chaînes.  
  
 *FilterCondition* spécifie les critères que les enregistrements doivent respecter pour être inclus dans les résultats de la requête. Vous pouvez inclure autant de conditions de filtre dans une requête que vous le souhaitez, en les connectant avec l’opérateur ET ou OU. Vous pouvez également utiliser l’opérateur PAS pour inverser la valeur d’une expression logique, ou vous pouvez utiliser **EMPTY( )** pour vérifier un champ vide. *FilterCondition* peut prendre n’importe laquelle des formes dans les exemples suivants :  
  
 **Exemple 1** *FieldName1 Comparaison FieldName2*  
  
 `customer.cust_id = orders.cust_id`  
  
 **Exemple 2** *Expression de comparaison FieldName*  
  
 `payments.amount >= 1000`  
  
 **Exemple 3** *FieldName Comparison* ALL (*Sous-laquery*)  
  
 `company < ALL ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 Lorsque l’état du filtre comprend ALL, le champ doit répondre à la condition de comparaison pour toutes les valeurs générées par la sous-fertilité avant que son enregistrement ne soit inclus dans les résultats de la requête.  
  
 **Exemple 4** *Comparaison FieldName* ANY &#124; SOME (*Subquery*)  
  
 `company < ANY ;`  
  
 `(SELECT company FROM customer WHERE country = "USA")`  
  
 Lorsque l’état du filtre comprend n’importe quel ou SOME, le champ doit répondre à la condition de comparaison pour au moins une des valeurs générées par la sous-pays.  
  
 L’exemple suivant vérifie si les valeurs sur le terrain se situent dans une gamme de valeurs spécifiées :  
  
 **Exemple 5** *FieldName* [NOT] BETWEEN *Start_Range* AND *End_Range*  
  
 `customer.postalcode BETWEEN 90000 AND 99999`  
  
 L’exemple suivant vérifie si au moins une rangée répond aux critères de la sous-pays. Lorsque l’état du filtre comprend EXISTS, l’état du filtre s’évalue à True (. T.) à moins que la sous-virerie n’évalue à l’ensemble vide.  
  
 **Exemple 6** [PAS] EXISTS (*Sous-laquery*)  
  
 `EXISTS ;`  
  
 `(SELECT * FROM orders WHERE customer.postalcode =`  
  
 `orders.postalcode)`  
  
 **Exemple 7** *FieldName* [NOT] IN *Value_Set*  
  
 `customer.postalcode NOT IN ("98052","98072","98034")`  
  
 Lorsque l’état du filtre comprend IN, le champ doit contenir l’une des valeurs avant que son enregistrement ne soit inclus dans les résultats de la requête.  
  
 **Exemple 8** *FieldName* [NOT] IN (*Subquery*)  
  
 `customer.cust_id IN ;`  
  
 `(SELECT orders.cust_id FROM orders WHERE orders.city="Seattle")`  
  
 Ici, le champ doit contenir l’une des valeurs retournées par la sous-pays avant que son dossier ne soit inclus dans les résultats de la requête.  
  
 **Exemple 9** *FieldName* [NOT] LIKE *cExpression*  
  
 `customer.country NOT LIKE "USA"`  
  
 Cette condition de filtre recherche chaque champ qui correspond *à cExpression*. Vous pouvez utiliser le signe de pourcentage (%) et souligner ( ) caractères wildcard dans le cadre de *cExpression*. Le soulignement représente un seul personnage inconnu dans la chaîne.  
  
 GROUPE PAR *GroupColumn* [, *GroupColumn* ...]  
 Groupes rangs dans la requête en fonction des valeurs dans une ou plusieurs colonnes. *GroupColumn* peut être l’un des éléments suivants :  
  
-   Le nom d’un champ de table régulier.  
  
-   Un champ qui comprend une fonction de terrain SQL.  
  
-   Une expression numérique qui indique l’emplacement de la colonne dans le tableau de résultat. (Le numéro de colonne le plus à gauche est de 1.)  
  
 HAVING *FilterCondition (en)*  
 Spécifie une condition de filtre que les groupes doivent respecter pour être inclus dans les résultats de la requête. HAVING doit être utilisé avec GROUP BY et peut inclure autant de conditions de filtre que vous le souhaitez, connecté par l’opérateur ET ou OU. Vous pouvez également utiliser PAS pour inverser la valeur d’une expression logique.  
  
 *FilterCondition* ne peut pas contenir une sous-query.  
  
 Une clause HAVING sans clause GROUPE BY se comporte comme une clause WHERE. Vous pouvez utiliser des alias locaux et des fonctions sur le terrain dans la clause HAVING. Utilisez une clause WHERE pour des performances plus rapides si votre clause HAVING ne contient aucune fonction sur le terrain.  
  
 [UNION [TOUS] *SELECTCommand*]  
 Combine les résultats finaux d’un SELECT avec les résultats finaux d’un autre SELECT. Par défaut, UNION vérifie les résultats combinés et élimine les lignes en double. Utilisez les parenthèses pour combiner plusieurs clauses UNION.  
  
 TOUS empêche UNION d’éliminer les lignes en double des résultats combinés.  
  
 Les clauses UNION suivent ces règles :  
  
-   Vous ne pouvez pas utiliser UNION pour combiner des sous-ques.  
  
-   Les deux commandes SELECT doivent avoir le même nombre de colonnes dans leur sortie de requête.  
  
-   Chaque colonne dans les résultats de requête d’un SELECT doit avoir le même type de données et la même largeur que la colonne correspondante dans l’autre SELECT.  
  
-   Seul le SELECT final peut avoir une clause ORDER BY, qui doit se référer à des colonnes de sortie par numéro. Si une clause ORDER BY est incluse, elle affecte le résultat complet.  
  
 Vous pouvez également utiliser la clause UNION pour simuler une jointure extérieure.  
  
 Lorsque vous vous joignez à deux tables dans une requête, seuls les enregistrements avec des valeurs correspondantes dans les champs de jointure sont inclus dans la sortie. Si un dossier dans le tableau des parents n’a pas de dossier correspondant dans le tableau des enfants, le dossier dans le tableau parent n’est pas inclus dans le dossier. Une jointure extérieure vous permet d’inclure tous les enregistrements dans le tableau parent dans la sortie, ainsi que les enregistrements correspondants dans le tableau des enfants. Pour créer une jointure externe dans Visual FoxPro, vous devez utiliser une commande SELECT imbriquée, comme dans l’exemple suivant :  
  
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
>  Assurez-vous d’inclure l’espace qui précède immédiatement chaque point-virgule. Sinon, vous recevrez une erreur.  
  
 La section de la commande avant la clause UNION sélectionne les enregistrements des deux tableaux qui ont des valeurs correspondantes. Les entreprises clientes qui n’ont pas de factures associées ne sont pas incluses. La section de la commande après la clause UNION sélectionne les enregistrements dans le tableau des clients qui n’ont pas d’enregistrements correspondants dans le tableau des commandes.  
  
 En ce qui concerne la deuxième section de la commande, notez ce qui suit :  
  
-   L’énoncé SELECT dans les parenthèses est traité en premier. Cette déclaration crée une sélection de tous les numéros de clients dans le tableau des commandes.  
  
-   La clause WHERE trouve tous les numéros de clients dans le tableau des clients qui ne sont pas dans le tableau des commandes. Étant donné que la première section de la commande fournissait à toutes les entreprises qui avaient un numéro de client dans le tableau des commandes, toutes les entreprises dans le tableau des clients sont maintenant incluses dans les résultats de la requête.  
  
-   Étant donné que les structures des tableaux inclus dans une UNION doivent être identiques, il y a deux places dans la deuxième déclaration SELECT pour représenter *les ordres.order_id* et *les ordres.emp_id* de la première déclaration SELECT.  
  
    > [!NOTE]  
    >  Les propriétaires de places doivent être du même type que les champs qu’ils représentent. Si le champ est un type de date, le lieu de départ doit être / / . Si le champ est un champ de caractère, le placeholder doit être la chaîne vide ("").  
  
 ORDER BY *ORDER_ITEM* [ASC &#124; DESC] [, *Order_Item* [ASC &#124; DESC] ...]  
 Trie les résultats de la requête en fonction des données dans une ou plusieurs colonnes. Chaque *Order_Item* doit correspondre à une colonne dans les résultats de la requête et peut être l’un des éléments suivants :  
  
-   Un champ dans une table FROM qui est également un élément choisi dans la clause SELECT principale (pas dans une sous-fertilité).  
  
-   Une expression numérique qui indique l’emplacement de la colonne dans le tableau de résultat. (La colonne la plus gauche est le numéro 1.)  
  
 ASC spécifie une commande ascendante pour les résultats de requête, selon l’élément de commande ou des éléments, et est la valeur par défaut pour ORDER BY.  
  
 DESC précise une commande descendante pour les résultats de requête.  
  
 Les résultats de requête semblent non commandés si vous ne spécifiez pas une commande avec ORDER BY.  
  
## <a name="remarks"></a>Notes  
 SELECT est une commande SQL qui est intégrée à Visual FoxPro comme n’importe quelle autre commande Visual FoxPro. Lorsque vous utilisez SELECT pour poser une requête, Visual FoxPro interprète la requête et récupère les données spécifiées des tables. Vous pouvez créer une requête SELECT à partir de la fenêtre Command Prompt ou d’un programme Visual FoxPro (comme avec toute autre commande Visuelle FoxPro).  
  
> [!NOTE]  
>  SELECT ne respecte pas l’état actuel du filtre spécifié avec SET FILTER.  
  
## <a name="driver-remarks"></a>Remarques du conducteur  
 Lorsque votre application envoie la déclaration SQL ODBC SELECT à la source de données, le visual FoxPro ODBC Driver convertit la commande en commande Visual FoxPro SELECT sans traduction à moins que la commande ne contienne une séquence d’évacuation ODBC. Les objets inclus dans une séquence d’évacuation ODBC sont convertis en syntaxe Visuelle FoxPro. Pour plus d’informations sur l’utilisation des séquences d’évasion ODBC, voir [fonctions d’heure et de date](../../odbc/microsoft/time-and-date-functions-visual-foxpro-odbc-driver.md) et dans la *référence du programmeur Microsoft ODBC*, voir [Séquences d’évasion dans ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER TABLE - SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INSERT - SQL](../../odbc/microsoft/insert-sql-command.md)   
 [ENSEMBLE ANSI](../../odbc/microsoft/set-ansi-command.md)   
 [ENSEMBLE EXACT](../../odbc/microsoft/set-exact-command.md)
