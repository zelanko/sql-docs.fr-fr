---
title: Fonctions API de niveau 1 (ODBC Driver pour Oracle) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299949"
---
# <a name="level-1-api-functions-odbc-driver-for-oracle"></a>Fonctions de l’API du niveau 1 (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Les fonctions à ce niveau fournissent la conformité à l’interface De base ainsi que des fonctionnalités supplémentaires telles que le support transactionnel.  
  
|Fonction API|Notes|  
|------------------|-----------|  
|**SQLColumns**|Crée un ensemble de résultats pour une table, qui est la liste de colonnes pour la table ou les tables spécifiées. Lorsque vous demandez des colonnes pour un synonyme PUBLIC, vous devez avoir défini l’attribut de connexion SYNONYMCOLUMNS et spécifié une chaîne vide comme argument *szTableOwner.* Lors du retour des colonnes pour les synonymes PUBLIC, le conducteur définit la colonne TABLE NAME sur une chaîne vide. L’ensemble de résultats contient une colonne supplémentaire, ORDINAL POSITION, à la fin de chaque rangée. Cette valeur est la position ordinaire de la colonne dans le tableau.|  
|**SQLDriverConnect**|Se connecte à une source de données existante. Pour plus de détails, voir [Format et attributs de chaîne de connexion](../../odbc/microsoft/connection-string-format-and-attributes.md).|  
|**SQLGetConnectOption (SQLGetConnectOption)**|Retourne le paramètre actuel d’une option de connexion. Cette fonction est partiellement prise en charge. Le conducteur soutient toutes les valeurs pour *l’argument fOption,* mais ne supporte pas certaines valeurs *vParam* pour *l’argument fOption* [SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md). Pour plus d’informations, voir [Options Connect](../../odbc/microsoft/connect-options.md).|  
|**SQLGetData**|Récupère la valeur d’un seul champ dans le dossier actuel de l’ensemble de résultats donné.|  
|**SQLGetFunctions**|Retourne TRUE pour toutes les fonctions prises en charge. Mise en œuvre par le Driver Manager.|  
|**SQLGetInfo**|Retourne l’information, y compris SQLHDBC, SQLUSMALLINT, SQLPOINTER, SQLSMALLINT, et SQLSMALLINT \*, sur le pilote ODBC pour Oracle et source de données associées à une poignée de connexion, *hdbc*.|  
|**SQLGetStmtOption**|Retourne le paramètre actuel d’une option d’instruction. Pour plus d’informations, voir [Options d’instruction](../../odbc/microsoft/statement-options.md).|  
|**SQLGetTypeInfo**|Renvoie des informations sur les types de données pris en charge par une source de données. Le conducteur renvoie l’information dans un ensemble de résultats SQL.|  
|**SQLParamData**|Utilisé en conjonction avec **SQLPutData** pour spécifier les données de paramètres au moment de l’exécution des relevés.|  
|**SQLPutData**|Permet à une application d’envoyer des données pour un paramètre ou une colonne au pilote au moment de l’exécution de l’instruction.|  
|**SQLSetConnectOption**|Donne accès à des options qui régissent certains aspects de la connexion. Cette fonction est partiellement soutenue: Le conducteur prend en charge toutes les valeurs pour *l’argument fOption,* mais ne supporte pas certaines valeurs *vParam* pour *l’argument fOption* [SQL_TXN_ISOLATION](../../odbc/microsoft/connect-options.md). Pour plus d’informations, voir [Options Connect](../../odbc/microsoft/connect-options.md).|  
|**SQLSetStmtOption**|Définit les options liées à une poignée de relevé, *hstmt*. Pour plus d’informations, voir [Options d’instruction](../../odbc/microsoft/statement-options.md).|  
|**SQLSpecialColumns**|Récupère l’ensemble optimal de colonnes qui identifie uniquement une ligne dans la table.|  
|**SQLStatistics**|Récupère une liste de statistiques sur un tableau unique et les index, ou noms d’étiquettes, associés au tableau. Le conducteur renvoie l’information à la suite de l’ensemble.|  
|**SQLTables**|Retourne la liste des noms de table spécifiés par le paramètre dans l’énoncé **SQLTables.** Si aucun paramètre n’est spécifié, renvoie les noms de table stockés dans la source de données actuelle. Le conducteur renvoie l’information à la suite de l’ensemble.<br /><br /> Les appels de type recensement ne recevront pas d’entrée définie de résultat pour les vues à distance ou les vues paramétrisées locales. Cependant, un appel à **SQLTables** avec un spécificateur de nom de table unique trouvera une correspondance pour une telle vue, si elle est présente, avec ce nom; cela permet à l’API de vérifier les conflits de nom avant la création d’une nouvelle table.<br /><br /> LES synonymes PUBLIC sont retournés avec une valeur TABLE_OWNER de "".<br /><br /> Les VIEWS appartenant à SYS ou SYSTEM sont identifiés comme SYSTEM VIEW.|
