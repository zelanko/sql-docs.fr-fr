---
title: Fonctions d’API de niveau 1 (pilote ODBC pour Oracle) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a70116fb0e8ef1236b18cb478184e96fe08fce5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47829417"
---
# <a name="level-1-api-functions-odbc-driver-for-oracle"></a>Fonctions de l’API du niveau 1 (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Prend en charge des fonctions à cette fournir au niveau de conformité de l’interface Core ainsi que des fonctionnalités supplémentaires telles que des transactions.  
  
|Fonction d’API|Remarques|  
|------------------|-----------|  
|**SQLColumns**|Crée un jeu de résultats pour une table, qui est la liste des colonnes pour la table spécifiée ou tables. Lorsque vous demandez des colonnes pour un synonyme PUBLIC, vous devez avoir défini l’attribut de connexion SYNONYMCOLUMNS et spécifié une chaîne vide en tant que le *szTableOwner* argument. Lors du renvoi des colonnes pour les synonymes PUBLIC, le pilote définit la colonne de nom de la TABLE sur une chaîne vide. Le jeu de résultats contient une colonne supplémentaire, ORDINAL POSITION, à la fin de chaque ligne. Cette valeur est la position ordinale de la colonne dans la table.|  
|**SQLDriverConnect**|Se connecte à une source de données existante. Pour plus d’informations, consultez [Format chaîne de connexion et les attributs](../../odbc/microsoft/connection-string-format-and-attributes.md).|  
|**SQLGetConnectOption**|Retourne le paramètre actuel d’une option de connexion. Cette fonction est partiellement prises en charge. Le pilote prend en charge toutes les valeurs pour le *fOption* argument mais ne prend ne pas en charge certaines *vParam* valeurs pour le *fOption* argument [SQL_TXN_ISOLATION ](../../odbc/microsoft/connect-options.md). Pour plus d’informations, consultez [Options connecter](../../odbc/microsoft/connect-options.md).|  
|**SQLGetData**|Récupère la valeur d’un champ unique dans l’enregistrement actif du jeu de résultats donné.|  
|**SQLGetFunctions**|Retourne TRUE pour toutes les fonctions prises en charge. Implémenté par le Gestionnaire de pilotes.|  
|**SQLGetInfo**|Retourne des informations, y compris SQLHDBC SQLUSMALLINT, SQLPOINTER, SQLSMALLINT et SQLSMALLINT \*, sur le pilote ODBC pour Oracle et source de données associée à un handle de connexion, *pas*.|  
|**SQLGetStmtOption**|Retourne le paramètre actuel d’une option d’instruction. Pour plus d’informations, consultez [Options d’instruction](../../odbc/microsoft/statement-options.md).|  
|**SQLGetTypeInfo**|Retourne des informations sur les types de données pris en charge par une source de données. Le pilote retourne les informations dans un jeu de résultats SQL.|  
|**SQLParamData**|Utilisé conjointement avec **SQLPutData** pour spécifier les données de paramètre au moment de l’exécution d’instruction.|  
|**SQLPutData**|Permet à une application envoyer des données pour un paramètre ou une colonne pour le pilote au moment de l’exécution d’instruction.|  
|**SQLSetConnectOption**|Fournit l’accès aux options qui régissent les aspects de la connexion. Cette fonction est partiellement disponible : le pilote prend en charge toutes les valeurs pour le *fOption* argument mais ne prend ne pas en charge certaines *vParam* valeurs pour le *fOption* argument [SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md). Pour plus d’informations, consultez [Options connecter](../../odbc/microsoft/connect-options.md).|  
|**SQLSetStmtOption**|Définit les options relatives à un descripteur d’instruction, *hstmt*. Pour plus d’informations, consultez [Options d’instruction](../../odbc/microsoft/statement-options.md).|  
|**SQLSpecialColumns**|Récupère l’ensemble optimal de colonnes qui identifie de façon unique une ligne dans la table.|  
|**SQLStatistics**|Récupère une liste des statistiques sur une seule table index et les noms de balise, associés à la table. Le pilote retourne les informations comme jeu de résultats.|  
|**SQLTables**|Retourne la liste des noms de table spécifié par le paramètre dans le **SQLTables** instruction. Si aucun paramètre n’est spécifié, retourne les noms de table stockées dans la source de données actuelle. Le pilote retourne les informations comme jeu de résultats.<br /><br /> Énumération type appelle la méthode ne reçoit pas une entrée de jeu de résultats pour des vues paramétrées locales ou distant. Toutefois, un appel à **SQLTables** avec une table unique spécificateur de nom trouve une correspondance pour une telle vue, le cas échéant, portant le même nom ; Cela permet à l’API de recherche de conflits de nom avant la création d’une nouvelle table.<br /><br /> Synonymes publics sont retournés avec la valeur TABLE_OWNER » ».<br /><br /> VUES appartenant à SYS ou système sont identifiés en tant que vue système.|
