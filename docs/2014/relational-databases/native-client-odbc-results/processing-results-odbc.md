---
title: Traitement des résultats (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], about result sets
- SQLRowCount function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- COMPUTE clause
- result sets [ODBC]
- COMPUTE BY clause
ms.assetid: 61a8db19-6571-47dd-84e8-fcc97cb60b45
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 761f74a56fd846361ca98dd8f2746a01b53106ec
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82699319"
---
# <a name="processing-results-odbc"></a>Traitement des résultats (ODBC)
  Après qu'une application a soumis une instruction SQL, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne les données obtenues sous forme d'un ou plusieurs jeux de résultats. Un jeu de résultats est un ensemble de lignes et colonnes qui correspondent aux critères de la requête. Les instructions SELECT, les fonctions de catalogue et certaines procédures stockées produisent un jeu de résultats sous forme de tableau, accessible par une application. Si l'instruction SQL exécutée est une procédure stockée, un lot contenant plusieurs commandes ou une instruction SELECT avec des mots clés, il y aura plusieurs jeux de résultats à traiter.  
  
 Les fonctions de catalogue ODBC peuvent aussi récupérer les données. Par exemple, [SQLColumns](../native-client-odbc-api/sqlcolumns.md) récupère les données relatives aux colonnes dans la source de données. Ces jeux de résultats peuvent contenir zéro ou plusieurs lignes.  
  
 D'autres instructions SQL, telles que GRANT ou REVOKE, ne retournent pas de jeux de résultats. Pour ces instructions, le code de retour de **SQLExecute** ou **SQLExecDirect** est généralement la seule indication que l’instruction a réussi.  
  
 Chaque instruction INSERT, UPDATE et DELETE retourne un jeu de résultats qui contient uniquement le nombre de lignes concernées par la modification. Ce nombre est rendu disponible quand l’application appelle [SQLRowCount](../native-client-odbc-api/sqlrowcount.md). ODBC 3. *x* doivent appeler **SQLRowCount** pour récupérer le jeu de résultats ou [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) pour l’annuler. Lorsqu’une application exécute un traitement ou une procédure stockée contenant plusieurs instructions INSERT, UPDATE ou DELETE, le jeu de résultats de chaque instruction de modification doit être traité à l’aide de **SQLRowCount** ou annulé à l’aide de **SQLMoreResults**. Ces nombres peuvent être annulés en incluant une instruction SET NOCOUNT ON dans le lot ou la procédure stockée.  
  
 Transact-SQL inclut l'instruction SET NOCOUNT. Lorsque l’option NOCOUNT est activée, SQL Server ne retourne pas le nombre de lignes affectées par une instruction et **SQLRowCount** retourne 0. La [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version du pilote ODBC Native Client introduit une option [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md) spécifique au pilote, SQL_SOPT_SS_NOCOUNT_STATUS, pour indiquer si l’option NOCOUNT est activée ou désactivée. Chaque fois que **SQLRowCount** retourne 0, l’application doit tester SQL_SOPT_SS_NOCOUNT_STATUS. Si SQL_NC_ON est retourné, la valeur 0 de **SQLRowCount** indique uniquement que SQL Server n’a pas retourné de nombre de lignes. Si SQL_NC_OFF est retourné, cela signifie que NOCOUNT est désactivé et la valeur 0 de **SQLRowCount** indique que l’instruction n’a affecté aucune ligne. Les applications ne doivent pas afficher la valeur de **SQLRowCount** lorsque SQL_SOPT_SS_NOCOUNT_STATUS est SQL_NC_OFF. Comme les lots ou procédures stockées importants peuvent contenir plusieurs instructions SET NOCOUNT, les programmeurs ne peuvent pas en déduire que SQL_SOPT_SS_NOCOUNT_STATUS demeure constant. L’option doit être testée à chaque fois que **SQLRowCount** retourne 0.  
  
 Plusieurs autres instructions Transact-SQL retournent leurs données dans des messages plutôt que dans des jeux de résultats. Lorsque le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC native client reçoit ces messages, il retourne SQL_SUCCESS_WITH_INFO pour permettre à l’application de savoir que des messages d’information sont disponibles. L’application peut alors appeler **SQLGetDiagRec** pour extraire ces messages. Les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui fonctionnent ainsi sont :  
  
-   DBCC  
  
-   SET SHOWPLAN (disponible avec les versions antérieures de SQL Server)  
  
-   SET STATISTICS  
  
-   PRINT  
  
-   RAISERROR  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client retourne SQL_ERROR sur une instruction RAISERROR dont le niveau de gravité est supérieur ou égal à 11. Si la gravité de RAISERROR est supérieure ou égale à 19, la connexion est également abandonnée.  
  
 Pour traiter les jeux de résultats d'une instruction SQL, l'application :  
  
-   détermine les caractéristiques du jeu de résultats ;  
  
-   lie les colonnes aux variables de programme ;  
  
-   extrait une valeur unique, une ligne entière de valeurs ou plusieurs lignes de valeurs ;  
  
-   effectue un test pour voir s'il y a plusieurs jeux de résultats, et si tel est le cas, effectue une nouvelle boucle pour déterminer les caractéristiques du nouveau jeu de résultats.  
  
 Le processus de récupération des lignes de la source de données et leur renvoi à l'application est appelé extraction.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Détermination des caractéristiques d’un jeu de résultats &#40;ODBC&#41;](determining-the-characteristics-of-a-result-set-odbc.md)  
  
-   [Assignation du stockage](assigning-storage.md)  
  
-   [Extraction des données de résultat](fetching-result-data.md)  
  
-   [Mappage de types de données &#40;ODBC&#41;](mapping-data-types-odbc.md)  
  
-   [Utilisation des types de données](data-type-usage.md)  
  
-   [Traduction automatique de données caractères](autotranslation-of-character-data.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;&#41;ODBC](../native-client/odbc/sql-server-native-client-odbc.md)   
 [Rubriques de procédures relatives au traitement des résultats &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  
