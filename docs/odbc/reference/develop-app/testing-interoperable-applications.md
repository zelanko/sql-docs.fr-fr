---
title: Test des Applications interopérables | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], testing interoperable applications
- testing interoperable applications [ODBC]
ms.assetid: 489083cb-8430-40be-9ef2-d75b9a2eea88
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 509dd17efeeb982c51938d7a18fad99a2e84ba5b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63148931"
---
# <a name="testing-interoperable-applications"></a>Test des applications interopérables
Test des applications interopérables est au mieux un long commerciaux et au pire impossible, car les nouveaux pilotes s’affichent en permanence sur le marché. Toutefois, un niveau raisonnable de test est possible. Applications avec l’interopérabilité limitée ou faible doivent uniquement être testées par rapport à ces pilotes que sont assurés de prendre en charge. Toutefois, ils doivent être entièrement testés par rapport à ces pilotes.  
  
 Applications hautement interopérables ne peut pas être comparées pratiquement tous les pilotes. La meilleure que la plupart des développeurs d’applications peuvent effectuer consiste à les tester entièrement sur un petit nombre de pilotes et cursorily plusieurs autres. Pilotes testés doivent inclure les pilotes les plus populaires pour les SGBD plus populaires dans le marché de l’application ; Si le marché couvre tous les SGBD, les pilotes pour bureau et serveur SGBD doivent être testés.  
  
 Un des problèmes lors du test des applications ODBC est le nombre de composants impliqués : l’application elle-même, le Gestionnaire de pilotes, le pilote, les SGBD et éventuellement d’un logiciel réseau ou les passerelles. Applications peuvent faciliter le suivi des erreurs en validant les messages d’erreur retournées par les fonctions ODBC via **SQLGetDiagField** et **SQLGetDiagRec**. Ces messages indiquent le fabricant et le composant dans lequel les erreurs se produisent. Pour plus d’informations, consultez [Diagnostics](../../../odbc/reference/develop-app/diagnostics.md).
