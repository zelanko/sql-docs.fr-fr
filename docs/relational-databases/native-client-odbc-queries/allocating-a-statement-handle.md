---
title: Allocation d’un descripteur d’instruction | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- statements [ODBC], statement handles
- ODBC applications, executing queries
- SQLGetStmtAttr function
- SQL Server Native Client ODBC driver, statements
- allocating statement handles
- ODBC applications, statements
- statement handles [ODBC]
- SQLAllocHandle function
ms.assetid: 9ee207f3-2667-45f5-87ca-e6efa1fd7a5c
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 41bf309a1a2b1795f8d642ea7418289e94db4591
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937324"
---
# <a name="allocating-a-statement-handle"></a>Allocation d'un descripteur d'instruction
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Pour qu'une application puisse exécuter une instruction, elle doit allouer un descripteur d'instruction. Pour ce faire appel **SQLAllocHandle** avec la *HandleType* paramètre défini à SQL_HANDLE_STMT et *InputHandle* pointant vers un handle de connexion.  
  
 Les attributs d'instruction sont caractéristiques du descripteur d'instruction. Les exemples d'attributs d'instruction peuvent inclure l'utilisation de signets et le type de curseur à utiliser avec le jeu de résultats de l'instruction. Attributs d’instruction sont définis avec [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md), et leurs paramètres actuels sont récupérés à l’aide de [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md). Il n'y a aucune obligation pour une application de définir des attributs d'instruction ; tous les attributs d'instruction ont des valeurs par défaut, et certaines sont spécifiques aux pilotes.  
  
 Soyez prudent lorsque vous utilisez plusieurs options de connexion et d'instruction ODBC. Appel [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) avec *fOption* définie sur les contrôles sql_attr_login_timeout permet de contrôler l’heure à laquelle une application attend une tentative de connexion à un délai d’attente lors de l’attente pour établir une connexion (0 Spécifie une attente infinie). Sur les sites dont les temps de réponse sont longs, il est possible de définir cette valeur à un niveau élevé pour s'assurer que les connexions disposent d'un délai suffisant pour s'effectuer. Toutefois, l'intervalle doit toujours être suffisamment faible pour qu'une réponse soit fournie à l'utilisateur dans un délai raisonnable, si le pilote ne peut pas se connecter.  
  
 Appel **SQLSetStmtAttr** avec *fOption* ensemble à SQL_ATTR_QUERY_TIMEOUT définit un intervalle de délai d’attente de requête permettant de protéger le serveur et l’utilisateur à partir de requêtes à long terme.  
  
 Appel **SQLSetStmtAttr** avec *fOption* ensemble à SQL_ATTR_MAX_LENGTH limite la quantité de **texte** et **image** données qui un instruction individuelle peut récupérer. Appel **SQLSetStmtAttr** avec *fOption* SQL_ATTR_MAX_ROWS la valeur limite également un ensemble de lignes à la première *n* nécessite des lignes si c’est toute l’application. Notez que la définition de SQL_ATTR_MAX_ROWS oblige le pilote à émettre une instruction SET ROWCOUNT à destination du serveur. Cela affecte toutes les [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instructions, y compris les déclencheurs et les mises à jour.  
  
 Soyez prudent lorsque vous définissez ces options. Il est préférable que tous les descripteurs d'instruction d'un handle de connexion aient les mêmes paramètres pour SQL_ATTR_MAX_LENGTH et SQL_ATTR_MAX_ROWS. Si le pilote passe d'un descripteur d'instruction à un autre avec des valeurs différentes pour ces options, il doit générer les instructions SET TEXTSIZE et SET ROWCOUNT appropriées pour modifier les paramètres. Le pilote ne peut pas placer ces instructions dans le même lot que l'instruction SQL utilisateur, car cette dernière peut contenir une instruction qui doit être la première dans un lot. Le pilote doit envoyer les instructions SET TEXTSIZE et SET ROWCOUNT dans un lot séparé, ce qui génère automatiquement un aller-retour supplémentaire au serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [L’exécution de requêtes &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
