---
title: Conformité à l’interface de niveau 2 (fr) Microsoft Docs
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
ms.openlocfilehash: 3ee57d716cbb93f855e1fd78d41bff62a681eb6c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306161"
---
# <a name="level-2-interface-conformance"></a>Conformité de l’interface - niveau 2
Le niveau de conformité à l’interface de niveau 2 comprend la fonctionnalité de niveau 1 de niveau conforme au niveau de la conformité ainsi que les fonctionnalités suivantes :  
  
|||  
|-|-|  
|201|Utilisez des noms en trois parties de tables et de vues de base de données. (Pour plus d’informations, voir la fonction de support de nommage en deux parties 101 dans [le niveau 1 Interface Conformance](../../../odbc/reference/develop-app/level-1-interface-conformance.md).)|  
|202|Décrivez les paramètres dynamiques, en appelant **SQLDescribeParam**.|  
|203|Utilisez non seulement les paramètres d’entrée, mais aussi les paramètres de sortie et d’entrée/sortie, et les valeurs de résultat des procédures stockées.|  
|204|Utilisez des signets, y compris la récupération de signets, en appelant **SQLDescribeCol** et **SQLColAttribute** sur la colonne numéro 0; aller chercher sur la base d’un signet, en appelant **SQLFetchScroll** avec *l’argument FetchOrientation* mis à SQL_FETCH_BOOKMARK; et mettre à jour, supprimer et aller chercher par des opérations de signets, en appelant **SQLBulkOperations** avec *l’argument de l’opération* réglé pour SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK ou SQL_FETCH_BY_BOOKMARK.|  
|205|Récupérez des informations avancées sur le dictionnaire de données, en appelant **SQLColumnPrivileges**, **SQLForeignKeys**, et **SQLTablePrivileges**.|  
|206|Utilisez les fonctions ODBC au lieu des relevés SQL pour effectuer d’autres opérations de base de données, en appelant **SQLBulkOperations** avec SQL_ADD, ou **SQLSetPos** avec SQL_DELETE ou SQL_UPDATE. (Le soutien aux appels à **SQLSetPos** avec l’argument *LockType* réglé pour SQL_LOCK_EXCLUSIVE ou SQL_LOCK_UNLOCK ne fait pas partie des niveaux de conformité, mais est une caractéristique facultative.)|  
|207|Activez l’exécution asynchrone des fonctions d’ODBC pour des déclarations individuelles spécifiées.|  
|208|Obtenez la colonne SQL_ROWVER d’identification des rangées de tables, en appelant **SQLSpecialColumns**. (Pour plus d’informations, voir le soutien de **SQLSpecialColumns** avec *l’argument IdentifierType* mis à SQL_BEST_ROWID comme fonctionnalité 20 dans [Core Interface Conformance](../../../odbc/reference/develop-app/core-interface-conformance.md).)|  
|209|Définissez l’attribut SQL_ATTR_CONCURRENCY d’énoncé à au moins une valeur autre que SQL_CONCUR_READ_ONLY.|  
|210|La possibilité de temps libre demande de connexion et les requêtes SQL (SQL_ATTR_LOGIN_TIMEOUT et SQL_ATTR_QUERY_TIMEOUT).|  
|211|La capacité de modifier le niveau d’isolement par défaut; la capacité d’exécuter des transactions avec le niveau d’isolement « sérialisable ».|
