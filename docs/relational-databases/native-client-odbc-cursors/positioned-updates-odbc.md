---
title: Mises à jour positionnées (ODBC) Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- SQLSetPos function
- SQLSetCursorName function
- ODBC applications, cursors
- cursors [ODBC], positioned updates
- positioned updates [ODBC]
- ODBC cursors, positioned updates
ms.assetid: ff404e02-630f-474d-b5d4-06442b756991
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 52495f670986638cac02661240e349713424256e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305322"
---
# <a name="positioned-updates-odbc"></a>Mises à jour positionnées (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC prend en charge deux méthodes permettant d'effectuer des mises à jour positionnées dans un curseur :  
  
-   **SQLSetPos**  
  
-   Clause WHERE CURRENT OF  
  
 L’approche la plus courante est d’utiliser **SQLSetPos**. Il a les options suivantes.  
  
 SQL_POSITION  
 Positionne le curseur sur une ligne spécifique dans l'ensemble de lignes actif.  
  
 SQL_REFRESH  
 Actualise les variables de programme liées aux colonnes de jeu de résultats avec les valeurs provenant de la ligne sur laquelle le curseur est actuellement positionné.  
  
 SQL_UPDATE  
 Met à jour la ligne active du curseur avec les valeurs stockées dans les variables de programme liées aux colonnes de jeu de résultats.  
  
 SQL_DELETE  
 Supprime la ligne active du curseur.  
  
 **SQLSetPos** peut être utilisé avec n’importe quel ensemble de résultat de déclaration lorsque les attributs de curseur de poignée de déclaration sont réglés pour employer des curseurs de serveur. Les colonnes de jeu de résultats doivent être liées à des variables de programme. Dès que l’application est allée chercher une rangée, elle appelle **SQLSetPos**(SQL_POSTION) pour positionner le curseur sur la ligne. L'application peut ensuite appeler SQLSetPos(SQL_DELETE) pour supprimer la ligne active, ou elle peut déplacer les nouvelles valeurs de données dans les variables de programme liées et appeler SQLSetPos(SQL_UPDATE) pour mettre à jour la ligne active.  
  
 Les applications peuvent mettre à jour ou supprimer n’importe quelle ligne dans le rowset avec **SQLSetPos**. Appeler **SQLSetPos** est une alternative pratique à la construction et à l’exécution d’une déclaration SQL. **SQLSetPos** fonctionne sur le rowset actuel et ne peut être utilisé qu’après un appel à [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md).  
  
 La taille de Rowset est réglée par un appel à [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) avec un argument d’attribut de SQL_ATTR_ROW_ARRAY_SIZE. **SQLSetPos** utilise une nouvelle taille de rowset, mais seulement après un appel à **SQLFetch** ou **SQLFetchScroll**. Par exemple, si la taille de l’aviron est modifiée, **SQLSetPos** est appelé, puis **SQLFetch** ou **SQLFetchScroll** est appelé. L’appel à **SQLSetPos** utilise l’ancienne taille de l’ensemble de rangées, mais **SQLFetch** ou **SQLFetchScroll** utilise la nouvelle taille de l’aviron.  
  
 La première ligne de l'ensemble de lignes porte le numéro 1. L’argument de RowNumber dans **SQLSetPos** doit identifier une rangée dans le rangée; c’est-à-dire que sa valeur doit être de l’ordre de 1 à 1 et du nombre de rangées qui ont été récemment récupérées. Cette valeur peut être inférieure à la taille de l'ensemble de lignes. Si RowNumber a la valeur 0, l'opération s'applique à chaque ligne de l'ensemble de lignes.  
  
 L’opération de suppression de **SQLSetPos** permet à la source de données de supprimer une ou plusieurs rangées sélectionnées d’une table. Pour supprimer les lignes avec **SQLSetPos**, l’application appelle **SQLSetPos** avec Opération réglée à SQL_DELETE et RowNumber réglé au nombre de la ligne à supprimer. Si RowNumber a la valeur 0, toutes les lignes de l'ensemble de lignes sont supprimées.  
  
 Après le retour **de SQLSetPos,** la ligne supprimée est la ligne actuelle et son statut est SQL_ROW_DELETED. La ligne ne peut pas être utilisée dans d’autres opérations positionnées, comme les appels à [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) ou **SQLSetPos**.  
  
 Lorsque vous supprimez toutes les lignes de la ligne (RowNumber est égal à 0), l’application peut empêcher le conducteur de supprimer certaines lignes en utilisant le tableau d’opération de ligne tout comme pour l’opération de mise à jour de **SQLSetPos**.  
  
 Chaque ligne supprimée doit être une ligne qui existe dans le jeu de résultats. Si les mémoires tampons de l'application ont été remplies par extraction et si un tableau de statut de ligne a été maintenu, ses valeurs à chacune de ces positions de ligne ne doivent pas être SQL_ROW_DELETED, SQL_ROW_ERROR ou SQL_ROW_NOROW.  
  
 Les mises à jour positionnées peuvent également être réalisées à l'aide de la clause WHERE CURRENT OF sur les instructions UPDATE, DELETE et INSERT. Où CURRENT OF nécessite un nom curseur que ODBC va générer lorsque la fonction [SQLGetCursorName](../../relational-databases/native-client-odbc-api/sqlgetcursorname.md) est appelé, ou que vous pouvez spécifier en appelant **SQLSetCursorName**. La procédure générale suivante est utilisée pour effectuer une mise à jour de WHERE CURRENT OF dans une application ODBC :  
  
-   Appelez **SQLSetCursorName** pour établir un nom de curseur pour la poignée de déclaration.  
  
-   Générez une instruction SELECT avec une clause FOR UPDATE OF et exécutez-la.  
  
-   Appelez **SQLFetchScroll** pour récupérer un aviron ou **SQLFetch** pour récupérer une rangée.  
  
-   Appelez **SQLSetPos** (SQL_POSITION) pour placer le curseur sur la rangée.  
  
-   Construire et exécuter une déclaration UPDATE avec une clause WHERE CURRENT OF à l’aide du nom de curseur défini avec **SQLSetCursorName**.  
  
 Alternativement, vous pouvez appeler **SQLGetCursorName** après avoir exécuté la déclaration SELECT au lieu d’appeler **SQLSetCursorName** avant d’exécuter la déclaration SELECT. **SQLGetCursorName renvoie** un nom de curseur par défaut attribué par ODBC si vous ne définissez pas un nom de curseur à l’aide **de SQLSetCursorName**.  
  
 **SQLSetPos** est préféré à WHERE CURRENT OF lorsque vous utilisez des curseurs serveur. Si vous utilisez un curseur statique pouvant être mis à jour avec la bibliothèque de curseurs ODBC, la bibliothèque de curseurs implémente les mises à jour WHERE CURRENT OF en ajoutant une clause WHERE avec les valeurs de clé pour la table sous-jacente. Cela peut entraîner des mises à jour inattendues si les clés de la table ne sont pas uniques.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de cursors &#40;&#41;ODBC](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
