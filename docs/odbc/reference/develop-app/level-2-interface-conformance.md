---
title: Conformité de l’Interface de niveau 2 | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 50e74eaed2d651158834a241563d10b3b2e90d5b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915571"
---
# <a name="level-2-interface-conformance"></a>Conformité de l’interface - niveau 2
Niveau de la conformité de l’interface de niveau 2 inclut des fonctionnalités de niveau de conformité de l’interface de niveau 1 ainsi que les fonctionnalités suivantes :  
  
|||  
|-|-|  
|201|Utiliser des noms en trois parties des tables de base de données et des vues. (Pour plus d’informations, consultez la deux parties d’affectation de noms fonctionnalité prise en charge 101 dans [au niveau de conformité de l’Interface 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md).)|  
|202|Décrire les paramètres dynamiques, en appelant **SQLDescribeParam**.|  
|203|Utiliser non seulement les paramètres d’entrée mais également les paramètres de sortie et d’entrée/sortie et des procédures stockées, les valeurs de résultat.|  
|204|Utiliser des signets, y compris la récupération des signets, en appelant **SQLDescribeCol** et **SQLColAttribute** sur la colonne numéro 0 ; l’extraction basé sur un signet, en appelant **SQLFetchScroll** avec la *FetchOrientation* à l’argument SQL_FETCH_BOOKMARK ; et la mise à jour, supprimer et à extraire par les opérations de signet, en appelant **SQLBulkOperations** avec la *Opération* argument la valeur SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK ou SQL_FETCH_BY_BOOKMARK.|  
|205|Récupérer des informations avancées sur le dictionnaire de données, en appelant **SQLColumnPrivileges**, **SQLForeignKeys**, et **SQLTablePrivileges**.|  
|206|Utiliser les fonctions ODBC au lieu d’instructions SQL pour effectuer des opérations de base de données supplémentaires, en appelant **SQLBulkOperations** avec SQL_ADD, ou **SQLSetPos** avec SQL_DELETE ou SQL_UPDATE. (Prise en charge pour les appels à **SQLSetPos** avec la *LockType* à l’argument SQL_LOCK_EXCLUSIVE ou SQL_LOCK_UNLOCK ne fait pas partie des niveaux de conformité, mais est une fonctionnalité facultative.)|  
|207|Permettre une exécution asynchrone de fonctions ODBC pour les instructions individuelles spécifiées.|  
|208|Obtenir la colonne d’identification de ligne SQL_ROWVER des tables, en appelant **SQLSpecialColumns**. (Pour plus d’informations, consultez la prise en charge pour **SQLSpecialColumns** avec la *IdentifierType* argument a la valeur SQL_BEST_ROWID en tant que fonction 20 dans [conformité de l’Interface Core](../../../odbc/reference/develop-app/core-interface-conformance.md) .)|  
|209|L’attribut d’instruction SQL_ATTR_CONCURRENCY la valeur est au moins une valeur autre que SQL_CONCUR_READ_ONLY.|  
|210|La possibilité de demande de connexion de délai d’attente et de requêtes SQL (sql_attr_login_timeout permet de contrôler et SQL_ATTR_QUERY_TIMEOUT).|  
|211|La possibilité de modifier le niveau d’isolation par défaut ; la possibilité d’exécuter des transactions avec niveau d’isolement « sérialisable ».|
