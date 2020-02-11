---
title: Nouvelles fonctionnalités | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 74c9a97c2511bc9c9a738b9e63548a9179552489
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086344"
---
# <a name="new-features"></a>Nouvelles fonctionnalités
Les nouvelles fonctionnalités suivantes ont été introduites dans ODBC *3. x*. Une application ODBC *3. x* fonctionnant avec un pilote ODBC *2. x* ne sera pas en mesure d’utiliser cette fonctionnalité. Le gestionnaire de pilotes ODBC *3. x* ne mappe pas ces fonctionnalités lors de l’utilisation d’un pilote ODBC *2. x* .  
  
-   Fonctions qui prennent un handle de descripteur comme argument : **SQLSetDescField**, **SQLGetDescField**, **SQLSetDescRec**, **SQLGetDescRec**et **SQLCopyDesc**.  
  
-   Fonctions **SQLSetEnvAttr** et **SQLGetEnvAttr**.  
  
-   Utilisation de **SQLAllocHandle** pour allouer un handle de descripteur. (L’utilisation de **SQLAllocHandle** pour allouer des descripteurs d’environnement, de connexion et d’instruction est dupliquée, et non une nouvelle fonctionnalité).  
  
-   L’utilisation de **SQLGetConnectAttr** pour récupérer les attributs de connexion SQL_ATTR_AUTO_IPD. (L’utilisation de **SQLSetConnectAttr** pour définir et **SQLGetConnectAttr** pour la récupération, d’autres attributs de connexion sont dupliqués, et non de nouvelles fonctionnalités.)  
  
-   L’utilisation de **SQLSetStmtAttr** pour définir et **SQLGetStmtAttr** pour l’extraction des attributs d’instruction suivants. (L’utilisation de **SQLSetStmtAttr** pour définir, et **SQLGetStmtAttr** pour la récupération, les autres attributs d’instruction sont dupliqués, et non nouvelles fonctionnalités.)  
  
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
  
-   L’utilisation de **SQLGetStmtAttr** pour récupérer les attributs d’instruction suivants. (L’utilisation de **SQLGetStmtAttr** pour récupérer d’autres attributs d’instruction est une fonctionnalité dupliquée, et non une nouvelle fonctionnalité).  
  
     SQL_ATTR_IMP_ROW_DESC SQL_ATTR_IMP_PARAM_DESC  
  
-   Utilisez le type de données Interval C, les types de données interval SQL, les types de données BIGINT C et la structure de données SQL_C_NUMERIC.  
  
-   Liaison selon les lignes des paramètres.  
  
-   Extractions de signet basées sur un décalage, telles que l’appel de **SQLFetchScroll** avec un argument *FetchOrientation* de SQL_FETCH_BOOKMARK et la spécification d’un offset autre que 0.  
  
-   **SQLFetch** retourne le tableau d’état de ligne, le nombre de lignes extraites, l’extraction de plusieurs lignes, l’intercombinaison d’appels avec **SQLFetchScroll**et l’Association d’appels avec **SQLBulkOperations** ou **SQLSetPos**. Pour plus d’informations, consultez la section suivante, [curseurs de bloc, curseurs avec défilement et compatibilité descendante pour les applications ODBC 3. x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md).  
  
-   Paramètres nommés.  
  
-   N’importe laquelle des options de **SQLGetInfo** spécifiques à ODBC *3. x*. (Si une application ODBC *3. x* qui utilise un pilote ODBC *2. x* appelle les types d’informations SQL_XXX_CURSOR_ATTRIBUTES1, qui ont remplacé plusieurs types d’informations ODBC *2. x* , certaines informations peuvent être fiables, mais d’autres peuvent ne pas être fiables. Pour plus d’informations, consultez [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).)  
  
-   Décalages de liaison.  
  
-   Mise à jour, actualisation et suppression par signets (par le biais d’un appel à **SQLBulkOperations**).  
  
-   Appel de **SQLBulkOperations** ou **SQLSetPos** dans l’État S5.  
  
-   Les champs ROW_NUMBER et COLUMN_NUMBER dans l’enregistrement de diagnostic (qui doivent être récupérés par les fonctions de remplacement **SQLGetDiagField** ou **SQLGetDiagRec**).  
  
-   Nombre approximatif de lignes.  
  
-   Informations d’avertissement (SQL_ROW_SUCCESS_WITH_INFO à partir de **SQLFetchScroll**).  
  
-   Signets de longueur variable.  
  
-   Informations d’erreur étendues pour les tableaux de paramètres.  
  
-   Toutes les nouvelles colonnes des jeux de résultats retournés par les fonctions de catalogue.  
  
-   Utilisation de **SQLDescribeCol** et **SQLColAttribute** sur la colonne 0.  
  
-   Utilisation d’attributs de colonne spécifiques ODBC *3. x*dans un appel à **SQLColAttribute**.  
  
-   Utilisation de plusieurs descripteurs d’environnement.  
  
 Cette section contient la rubrique suivante.  
  
-   [Curseurs de bloc, curseurs avec défilement et compatibilité descendante pour les applications ODBC 3.x](../../../odbc/reference/develop-app/block-cursors-scrollable-backward-compatibility-odbc-3-x-applications.md)
