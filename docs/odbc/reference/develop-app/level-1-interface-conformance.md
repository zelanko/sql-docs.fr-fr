---
title: "Niveau 1 Interface conformité | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- level 1 interface conformance levels [ODBC]
ms.assetid: ee3f5c08-0583-4f3b-8354-ef71b6086a7e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c1f9e266e4379b2d1cfc9ee771ac49694cd3c58b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="level-1-interface-conformance"></a>Conformité d’Interface de niveau 1
Niveau de conformité de l’interface de niveau 1 inclut les fonctionnalités au niveau de la mise en conformité Core interface ainsi que des fonctionnalités supplémentaires, telles que les transactions, qui sont généralement disponibles dans un SGBD OLTP. Un pilote d’interface conforme de niveau 1 permet à l’application effectuer les opérations suivantes, en plus des fonctionnalités dans le niveau de conformité de l’interface Core :  
  
|||  
|-|-|  
|101|Spécifiez le schéma de base de données des tables et vues (à l’aide d’affectation de noms en deux parties). (Pour plus d’informations, consultez la dénomination en trois parties fonctionnalité 201 dans [mise en conformité de niveau 2 Interface](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|102|Appeler true exécution asynchrone de fonctions ODBC, où les fonctions ODBC applicables sont tous synchrone ou asynchrone sur une connexion donnée.|  
|103|Utilisez les curseurs de défilement et ainsi obtenir l’accès à un jeu de résultats dans les méthodes autres qu’avant uniquement, en appelant **SQLFetchScroll** avec la *FetchOrientation* argument autre que SQL_FETCH_NEXT. (Le SQL_FETCH_BOOKMARK *FetchOrientation* est dans la fonctionnalité de 204 [mise en conformité de niveau 2 Interface](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|104|Obtenir des clés primaires des tables, en appelant **SQLPrimaryKeys**.|  
|105|Utiliser des procédures stockées, via la séquence d’échappement ODBC pour les appels de procédure et interroger le dictionnaire de données concernant les procédures stockées, en appelant **SQLProcedureColumns** et **SQLProcedures**. (Le processus par lequel les procédures sont créées et stockées sur la source de données est en dehors de la portée de ce document.)|  
|106|Se connecter à une source de données en mode interactif en parcourant les serveurs disponibles, en appelant **SQLBrowseConnect**.|  
|107|Utiliser les fonctions ODBC au lieu d’instructions SQL pour effectuer certaines opérations de base de données : **SQLSetPos** avec SQL_POSITION et SQL_REFRESH.|  
|108|Accéder au contenu de plusieurs jeux de résultats générés par lots et procédures stockées, en appelant **SQLMoreResults**.|  
|109|Délimiter les transactions couvrant plusieurs fonctions ODBC, avec l’atomicité et la possibilité de spécifier SQL_ROLLBACK dans **SQLEndTran**.|

