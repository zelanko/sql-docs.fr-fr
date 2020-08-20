---
description: Test des applications interopérables
title: Test des applications interopérables | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: feebbe5914e9da1e414f5c77a1a69bc0a6e0e7b1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487522"
---
# <a name="testing-interoperable-applications"></a>Test des applications interopérables
Le test des applications interopérables est au mieux une activité fastidieuse et au pire, car de nouveaux pilotes apparaissent continuellement sur le marché. Toutefois, un degré raisonnable de test est possible. Les applications dont l’interopérabilité est limitée ou faible ne doivent être testées que par rapport aux pilotes qu’ils sont assurés de prendre en charge. Toutefois, ils doivent être entièrement testés sur ces pilotes.  
  
 Les applications hautement interopérables ne peuvent pas être testées pratiquement contre tous les pilotes. Le mieux que la plupart des développeurs d’applications est de les tester entièrement contre un petit nombre de pilotes et de cursorily contre plusieurs. Les pilotes testés doivent inclure les pilotes les plus populaires pour les SGBD les plus populaires sur le marché de l’application. Si le marché couvre tous les SGBD, les pilotes des SGBD de bureau et de serveur doivent être testés.  
  
 L’un des problèmes de test des applications ODBC est le nombre de composants impliqués : l’application elle-même, le gestionnaire de pilotes, le pilote, le SGBD et éventuellement les logiciels réseau ou les passerelles. Les applications peuvent faciliter le suivi des erreurs en publiant les messages d’erreur retournés par les fonctions ODBC via **SQLGetDiagField** et **SQLGetDiagRec**. Ces messages identifient le fabricant et le composant dans lesquels des erreurs se produisent. Pour plus d’informations, consultez [Diagnostics](../../../odbc/reference/develop-app/diagnostics.md).
