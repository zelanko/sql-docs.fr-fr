---
title: Nouvelles fonctionnalités ( fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], new features in release
- ODBC drivers [ODBC], backward compatibility
- new features [ODBC]
- compatibility [ODBC], new features in release
- ODBC [ODBC], new features
ms.assetid: a8fcdd00-6cb3-4871-9489-6018b3d0d65f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b40803dac6c9f296043a8dcac50f9bc69036875a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302397"
---
# <a name="new-features"></a>Nouvelles fonctionnalités
La nouvelle fonctionnalité suivante a été introduite dans ODBC *3.x*. Une application ODBC *3.x* travaillant avec un pilote ODBC *2.x* ne sera pas en mesure d’utiliser cette fonctionnalité. L’ODBC *3.x* Driver Manager ne cartographie pas ces fonctionnalités lorsqu’il travaille avec un pilote ODBC *2.x.*  
  
-   Fonctions qui prennent une poignée descripteur comme argument: **SQLSetDescField**, **SQLGetDescField**, **SQLSetDescRec**, **SQLGetDescRec**, et **SQLCopyDesc**.  
  
-   Les fonctions **SQLSetEnvAttr** et **SQLGetEnvAttr**.  
  
-   L’utilisation de **SQLAllocHandle** pour allouer une poignée descripteur. (L’utilisation de **SQLAllocHandle** pour allouer l’environnement, la connexion et les poignées de déclaration est dupliquée, et non nouvelle, fonctionnalité.)  
  
-   L’utilisation de **SQLGetConnectAttr** pour obtenir les attributs de connexion SQL_ATTR_AUTO_IPD. (L’utilisation de **SQLSetConnectAttr** pour définir, et **SQLGetConnectAttr** pour obtenir, d’autres attributs de connexion est dupliqué, pas nouveau, fonctionnalité.)  
  
-   L’utilisation de **SQLSetStmtAttr** pour définir, et **SQLGetStmtAttr** pour obtenir, les attributs de déclaration suivante. (L’utilisation de **SQLSetStmtAttr** pour définir, et **SQLGetStmtAttr** pour obtenir, d’autres attributs de déclaration est dupliqué, pas nouveau, fonctionnalité.)  
  
     SQL_ATTR_APP_ROW_DESC  
  
     SQL_ATTR_APP_PARAM_DESC  
  
     SQL_ATTR_ENABLE_AUTO_IPD  
  
     SQL_ATTR_FETCH_BOOKMARK_PTR  
  
     SQL_ATTR_BIND_OFFSET  
  
     SQL_ATTR_METADATA_ID  
  
     SQL_ATTR_PARAM_BIND_OFFSET_PTR  
  
     SQL_ATTR_PARAM_BIND_TYPE  
  
     SQL_ATTR_PARAM_OPERATION_PTR  
  
     SQL_DESC_PARAM_STATUS_PTR  
  
     SQL_ATTR_PARAMS_PROCESSED_PTR  
  
     SQL_ATTR_PARAMSET_SIZE  
  
     SQL_ATTR_ROW_BIND_OFFSET_PTR  
  
     SQL_ATTR_ROW_OPERATION_PTR  
  
     SQL_ATTR_ROW_ARRAY_SIZE  
  
-   L’utilisation de **SQLGetStmtAttr** pour obtenir les attributs de déclaration suivante. (L’utilisation de **SQLGetStmtAttr** pour obtenir d’autres attributs de déclaration est une fonctionnalité dupliquée, et non de nouvelles fonctionnalités.)  
  
     SQL_ATTR_IMP_ROW_DESC SQL_ATTR_IMP_PARAM_DESC  
  
-   Utilisation du type de données d’intervalle C, des types de données SQL d’intervalle, des types de données BIGINT C et de la structure de données SQL_C_NUMERIC.  
  
-   Liaison de paramètres sur le plan de la ligne.  
  
-   Des signets basés sur des compensations, comme appeler **SQLFetchScroll** avec un argument *d’orientation de fetchorientation* de SQL_FETCH_BOOKMARK et spécifier un décalage autre que 0.  
  
-   **SQLFetch** retournant le tableau d’état de la ligne, nombre de rangées récupérées, allant chercher plusieurs rangées, intermélanger les appels avec **SQLFetchScroll**, et entremêler les appels avec **SQLBulkOperations** ou **SQLSetPos**. Pour plus d’informations, voir la section suivante, [Block Cursors, Cursesors Scrollable, et Compatibilité vers l’arrière pour ODBC 3.x Applications](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
-   Paramètres nommés.  
  
-   N’importe lequel des options **SQLGetInfo** spécifiques à *L’ODBC 3.x.* (Si une application ODBC *3.x* travaillant avec un conducteur ODBC *2.x* appelle les types d’information SQL_XXX_CURSOR_ATTRIBUTES1, qui ont remplacé plusieurs types d’informations ODBC *2.x,* certaines des informations peuvent être fiables, mais certains pourraient être peu fiables. Pour plus d’informations, voir [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).)  
  
-   Lier les compensations.  
  
-   Mise à jour, rafraîchissant et suppression par signets (par un appel à **SQLBulkOperations**).  
  
-   Appel **SQLBulkOperations** ou **SQLSetPos** dans l’état S5.  
  
-   Les ROW_NUMBER et COLUMN_NUMBER champs dans le dossier de diagnostic (qui doivent être récupérés par les fonctions de remplacement **SQLGetDiagField** ou **SQLGetDiagRec**).  
  
-   Nombre de rangées approximatives.  
  
-   Informations d’avertissement (SQL_ROW_SUCCESS_WITH_INFO de **SQLFetchScroll**).  
  
-   Signets à longueur variable.  
  
-   Informations d’erreur étendues pour les ensembles de paramètres.  
  
-   Toutes les nouvelles colonnes dans les ensembles de résultats retournés par les fonctions du catalogue.  
  
-   Utilisation de **SQLDescribeCol** et **SQLColAttribute** sur la colonne 0.  
  
-   Utilisation de tous les attributs de colonneS spécifiques ODBC *3.x*dans un appel à **SQLColAttribute**.  
  
-   Utilisation de poignées d’environnement multiples.  
  
 Cette section contient le sujet suivant.  
  
-   [Curseurs de bloc, curseurs avec défilement et compatibilité descendante pour les applications ODBC 3.x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)
