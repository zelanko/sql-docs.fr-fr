---
title: Conformité à l’interface de niveau 1 (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d31d5fe8aea1df4e7937104580efb820ba6f031
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306180"
---
# <a name="level-1-interface-conformance"></a>Conformité de l’interface - niveau 1
Le niveau de conformité à l’interface de niveau 1 comprend la fonctionnalité de niveau de conformité à l’interface Core ainsi que des fonctionnalités supplémentaires, telles que les transactions, qui sont généralement disponibles dans un DBMS relationnel OLTP. Un pilote conforme à l’interface de niveau 1 permet à l’application de faire ce qui suit, en plus des fonctionnalités du niveau de conformation de l’interface Core :  
  
|||  
|-|-|  
|101|Spécifier le schéma des tableaux et des vues de base de données (à l’aide de la dénomination en deux parties). (Pour plus d’informations, voir la fonction de nommage en trois parties 201 dans [Le niveau 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|102|Invoquez la véritable exécution asynchrone des fonctions d’ODBC, lorsque les fonctions ODBC applicables sont toutes synchrones ou toutes asynchrones sur une connexion donnée.|  
|103|Utilisez des curseurs défilementables, et ainsi atteindre l’accès à un résultat défini dans des méthodes autres que vers l’avant seulement, en appelant **SQLFetchScroll** avec *l’argument FetchOrientation* autre que SQL_FETCH_NEXT. (Le SQL_FETCH_BOOKMARK *FetchOrientation* est en fonction 204 dans [le niveau 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|104|Obtenez les clés primaires des tables, en appelant **SQLPrimaryKeys**.|  
|105|Utilisez des procédures stockées, par l’intermédiaire de la séquence d’évacuation ODBC pour les appels de procédure, et interrogez le dictionnaire de données concernant les procédures stockées, en appelant **SQLProcedureColumns** et **SQLProcedures**. (Le processus par lequel les procédures sont créées et stockées sur la source de données est en dehors du champ d’application de ce document.)|  
|106|Connectez-vous à une source de données en parcourant interactivement les serveurs disponibles, en appelant **SQLBrowseConnect**.|  
|107|Utilisez les fonctions ODBC au lieu des relevés SQL pour effectuer certaines opérations de base de données : **SQLSetPos** avec SQL_POSITION et SQL_REFRESH.|  
|108|Accédez au contenu de plusieurs ensembles de résultats générés par des lots et des procédures stockées, en appelant **SQLMoreResults**.|  
|109|Opérations de délimitation couvrant plusieurs fonctions ODBC, avec une véritable infirmité et la capacité de spécifier SQL_ROLLBACK dans **SQLEndTran**.|
