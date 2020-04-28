---
title: Fonctions de l’API de niveau 1 (pilote ODBC pour Oracle) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], ODBC driver for Oracle
- ODBC level 1 API functions [ODBC]
- ODBC driver for Oracle [ODBC], functions
- level 1 API functions [ODBC]
- API functions [ODBC]
ms.assetid: 98cced6f-41b8-43c1-a3cd-f4ea1615c0af
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37305ee75ebeb0686bafe039f1102cb3c6e18674
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299949"
---
# <a name="level-1-api-functions-odbc-driver-for-oracle"></a>Fonctions de l’API du niveau 1 (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Les fonctions à ce niveau fournissent la conformité de l’interface principale et des fonctionnalités supplémentaires telles que la prise en charge des transactions.  
  
|Fonction API|Notes|  
|------------------|-----------|  
|**SQLColumns**|Crée un jeu de résultats pour une table, qui est la liste des colonnes de la ou des tables spécifiées. Lorsque vous demandez des colonnes pour un synonyme PUBLIC, vous devez avoir défini l’attribut de connexion SYNONYMCOLUMNS et spécifié une chaîne vide comme argument *szTableOwner* . Lors du retour de colonnes pour les synonymes publics, le pilote définit la colonne de nom de TABLE sur une chaîne vide. Le jeu de résultats contient une colonne supplémentaire, POSITION ORDINALe, à la fin de chaque ligne. Cette valeur est la position ordinale de la colonne dans la table.|  
|**SQLDriverConnect**|Établit une connexion à une source de données existante. Pour plus d’informations, consultez [format de chaîne de connexion et attributs](../../odbc/microsoft/connection-string-format-and-attributes.md).|  
|**Sqlgetconnectoption,**|Retourne le paramètre actuel d’une option de connexion. Cette fonction est partiellement prise en charge. Le pilote prend en charge toutes les valeurs pour l’argument *fOption* , mais ne prend pas en charge certaines valeurs *vParam* pour l’argument *fOption* [SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md). Pour plus d’informations, consultez [options de connexion](../../odbc/microsoft/connect-options.md).|  
|**SQLGetData**|Récupère la valeur d’un champ unique dans l’enregistrement actif du jeu de résultats donné.|  
|**SQLGetFunctions**|Retourne la valeur TRUE pour toutes les fonctions prises en charge. Implémenté par le gestionnaire de pilotes.|  
|**SQLGetInfo**|Retourne des informations, notamment SQLHDBC, SQLUSMALLINT, SQLPOINTER, SQLSMALLINT et SQLSMALLINT \*, sur le pilote ODBC pour Oracle et la source de données associée à un handle de connexion, *hdbc*.|  
|**SQLGetStmtOption**|Retourne le paramètre actuel d’une option d’instruction. Pour plus d’informations, consultez [Options des instructions](../../odbc/microsoft/statement-options.md).|  
|**SQLGetTypeInfo**|Retourne des informations sur les types de données pris en charge par une source de données. Le pilote retourne les informations dans un jeu de résultats SQL.|  
|**SQLParamData**|Utilisé conjointement avec **SQLPutData** pour spécifier des données de paramètre au moment de l’exécution de l’instruction.|  
|**SQLPutData**|Permet à une application d’envoyer des données pour un paramètre ou une colonne au pilote au moment de l’exécution de l’instruction.|  
|**SQLSetConnectOption**|Donne accès aux options qui régissent les aspects de la connexion. Cette fonction est partiellement prise en charge : le pilote prend en charge toutes les valeurs pour l’argument *fOption* , mais ne prend pas en charge certaines valeurs *vParam* pour l’argument *fOption* [SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md). Pour plus d’informations, consultez [options de connexion](../../odbc/microsoft/connect-options.md).|  
|**SQLSetStmtOption**|Définit les options associées à un descripteur d’instruction, *HSTMT*. Pour plus d’informations, consultez [Options des instructions](../../odbc/microsoft/statement-options.md).|  
|**SQLSpecialColumns**|Récupère l’ensemble optimal de colonnes qui identifie de façon unique une ligne dans la table.|  
|**SQLStatistics**|Récupère une liste de statistiques sur une table unique et les index, ou les noms de balises, associés à la table. Le pilote retourne les informations sous la forme d’un jeu de résultats.|  
|**SQLTables**|Retourne la liste des noms de tables spécifiés par le paramètre dans l’instruction **SQLTables** . Si aucun paramètre n’est spécifié, retourne les noms de tables stockés dans la source de données actuelle. Le pilote retourne les informations sous la forme d’un jeu de résultats.<br /><br /> Les appels de type énumération ne recevront pas d’entrée de jeu de résultats pour les vues distantes ou les vues paramétrées locales. Toutefois, un appel à **SQLTables** avec un spécificateur de nom de table unique trouvera une correspondance pour une telle vue, si elle existe, avec ce nom ; Cela permet à l’API de vérifier les conflits de noms avant la création d’une nouvelle table.<br /><br /> Les synonymes publics sont retournés avec une valeur TABLE_OWNER de «».<br /><br /> Les vues détenues par SYS ou système sont identifiées comme vue système.|
