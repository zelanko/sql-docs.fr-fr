---
title: Conformité de l’interface de niveau 1 | Microsoft Docs
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
ms.openlocfilehash: 29f59cf06eac1ce0f6589ad9c7cba8491e8383b5
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363423"
---
# <a name="level-1-interface-conformance"></a>Conformité de l’interface - niveau 1
Le niveau de conformité de l’interface de niveau 1 comprend la fonctionnalité de niveau de conformité de l’interface principale, ainsi que les fonctionnalités supplémentaires, telles que les transactions, qui sont généralement disponibles dans un SGBD relationnel OLTP. Un pilote conforme à l’interface de niveau 1 permet à l’application d’effectuer les opérations suivantes, en plus des fonctionnalités du niveau de conformité de l’interface principale :  
  
|Numéro de fonctionnalité|Description|  
|-|-|  
|101|Spécifiez le schéma des tables et des vues de base de données (à l’aide d’un nom en deux parties). (Pour plus d’informations, consultez la fonctionnalité de nommage en trois parties 201 dans conformité de l' [interface de niveau 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|102|Appelle une véritable exécution asynchrone des fonctions ODBC, où les fonctions ODBC applicables sont toutes synchrones ou asynchrones sur une connexion donnée.|  
|103|Utilisez des curseurs de défilement, et obtenez ainsi un accès à un jeu de résultats dans des méthodes autres que Forward uniquement, en appelant **SQLFetchScroll** avec l’argument *FetchOrientation* autre que SQL_FETCH_NEXT. (Le SQL_FETCH_BOOKMARK *FetchOrientation* est dans la fonctionnalité 204 dans la conformité de l' [interface de niveau 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|104|Obtenez les clés primaires des tables en appelant **SQLPrimaryKeys**.|  
|105|Utilisez des procédures stockées, par le biais de la séquence d’échappement ODBC pour les appels de procédure, et interrogez le dictionnaire de données concernant les procédures stockées, en appelant **SQLProcedureColumns** et **SQLProcedures**. (Le processus par lequel les procédures sont créées et stockées dans la source de données dépasse le cadre de ce document.)|  
|106|Connectez-vous à une source de données en parcourant de manière interactive les serveurs disponibles, en appelant **SQLBrowseConnect**.|  
|107|Utilisez les fonctions ODBC à la place des instructions SQL pour effectuer certaines opérations de base de données : **SQLSetPos** avec SQL_POSITION et SQL_REFRESH.|  
|108|Accédez au contenu de plusieurs jeux de résultats générés par des traitements et des procédures stockées, en appelant **SQLMoreResults**.|  
|109|Délimitez les transactions couvrant plusieurs fonctions ODBC, avec une atomicité réelle et la possibilité de spécifier des SQL_ROLLBACK dans **SQLEndTran**.|
