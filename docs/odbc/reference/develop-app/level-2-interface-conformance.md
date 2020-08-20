---
description: Conformité de l’interface - niveau 2
title: Conformité de l’interface de niveau 2 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- level 2 interface conformance levels [ODBC]
- conformance levels [ODBC], interface
ms.assetid: 2dc87840-f2fe-43dd-9d7b-bd95523081d9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31b7148b05d3870a7f23a51167fffeb1860c26d8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476561"
---
# <a name="level-2-interface-conformance"></a>Conformité de l’interface - niveau 2
Le niveau de conformité de l’interface de niveau 2 comprend la fonctionnalité de niveau de conformité de l’interface de niveau 1, ainsi que les fonctionnalités suivantes :  
  
|Numéro de fonctionnalité|Description|  
|-|-|  
|201|Utilisez des noms en trois parties pour les vues et les tables de base de données. (Pour plus d’informations, consultez la fonctionnalité de prise en charge des noms en deux parties 101 dans conformité de l' [interface de niveau 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md).)|  
|202|Décrivez les paramètres dynamiques en appelant **SQLDescribeParam**.|  
|203|Utilisez non seulement des paramètres d’entrée, mais également des paramètres de sortie et d’entrée/sortie, ainsi que des valeurs de résultat de procédures stockées.|  
|204|Utilisez des signets, y compris la récupération de signets, en appelant **SQLDescribeCol** et **SQLColAttribute** sur la colonne numéro 0 ; récupération basée sur un signet, en appelant **SQLFetchScroll** avec l’argument *FetchOrientation* défini sur SQL_FETCH_BOOKMARK ; les opérations de mise à jour, de suppression et d’extraction par signet, en appelant **SQLBulkOperations** avec l’argument *operation* défini sur SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK ou SQL_FETCH_BY_BOOKMARK.|  
|205|Récupérez des informations avancées sur le dictionnaire de données en appelant **SQLColumnPrivileges**, **SQLForeignKeys**et **SQLTablePrivileges**.|  
|206|Utilisez les fonctions ODBC à la place des instructions SQL pour effectuer des opérations de base de données supplémentaires, en appelant **SQLBulkOperations** avec SQL_ADD ou **SQLSetPos** avec SQL_DELETE ou SQL_UPDATE. (La prise en charge des appels à **SQLSetPos** avec l’argument *LockType* défini sur SQL_LOCK_EXCLUSIVE ou SQL_LOCK_UNLOCK ne fait pas partie des niveaux de conformité, mais est une fonctionnalité facultative.)|  
|207|Active l’exécution asynchrone des fonctions ODBC pour les instructions individuelles spécifiées.|  
|208|Obtenez le SQL_ROWVER colonne d’identification de lignes des tables en appelant **SQLSpecialColumns**. (Pour plus d’informations, consultez la prise en charge de **SQLSpecialColumns** avec l’argument *IdentifierType* défini sur SQL_BEST_ROWID comme Feature 20 dans conformité de l' [interface principale](../../../odbc/reference/develop-app/core-interface-conformance.md).)|  
|209|Définissez l’attribut d’instruction SQL_ATTR_CONCURRENCY sur au moins une valeur autre que SQL_CONCUR_READ_ONLY.|  
|210|La possibilité de délai d’expiration de la demande de connexion et des requêtes SQL (SQL_ATTR_LOGIN_TIMEOUT et SQL_ATTR_QUERY_TIMEOUT).|  
|211|La possibilité de modifier le niveau d’isolation par défaut ; possibilité d’exécuter des transactions avec le niveau d’isolation « Serializable ».|
