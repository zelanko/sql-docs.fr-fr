---
title: La conformité de niveau 1 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- level 1 interface conformance levels [ODBC]
ms.assetid: ee3f5c08-0583-4f3b-8354-ef71b6086a7e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f2071ec7d7c9a31a9da8982b583ef7618700db5e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649317"
---
# <a name="level-1-interface-conformance"></a>Conformité de l’interface - niveau 1
Niveau de la conformité de l’interface de niveau 1 inclut les fonctionnalités de niveau de conformité Core interface ainsi que des fonctionnalités supplémentaires, telles que les transactions, qui sont généralement disponibles dans un SGBD relationnelle OLTP. Un pilote d’interface conforme de niveau 1 permet à l’application procédez comme suit, en plus des fonctionnalités dans le niveau de la conformité de l’interface Core :  
  
|||  
|-|-|  
|101|Spécifiez le schéma de base de données des tables et vues (à l’aide d’affectation de noms en deux parties). (Pour plus d’informations, consultez la dénomination en trois parties fonctionnalité 201 dans [au niveau de conformité de l’Interface 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|102|Appeler true exécution asynchrone de fonctions ODBC, où les fonctions ODBC applicables sont tout synchrones ou tous asynchrones sur une connexion donnée.|  
|103|Utiliser des curseurs avec défilement et obtenir ainsi un accès à un jeu de résultats dans les méthodes autres qu’avant uniquement, en appelant **SQLFetchScroll** avec la *FetchOrientation* argument autre que de SQL_FETCH_NEXT. (Le SQL_FETCH_BOOKMARK *FetchOrientation* est dans la fonctionnalité de 204 [au niveau de conformité de l’Interface 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|104|Obtenir les clés primaires des tables, en appelant **SQLPrimaryKeys**.|  
|105|Utiliser des procédures stockées, via la séquence d’échappement ODBC pour les appels de procédure et interroger le dictionnaire de données concernant les procédures stockées, en appelant **SQLProcedureColumns** et **SQLProcedures**. (Le processus par lequel les procédures sont créées et stockées sur la source de données est en dehors de la portée de ce document.)|  
|106|Se connecter à une source de données en mode interactif en parcourant les serveurs disponibles, en appelant **SQLBrowseConnect**.|  
|107|Utiliser les fonctions ODBC au lieu d’instructions SQL pour effectuer certaines opérations de base de données : **SQLSetPos** avec SQL_POSITION et SQL_REFRESH.|  
|108|Accéder au contenu de plusieurs jeux de résultats générés par lots et procédures stockées, en appelant **SQLMoreResults**.|  
|109|Délimiter les transactions s’étendant sur plusieurs fonctions ODBC, avec l’atomicité et la possibilité de spécifier SQL_ROLLBACK dans **SQLEndTran**.|
