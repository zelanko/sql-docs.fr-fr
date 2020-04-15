---
title: Test d’applications interopérables (fr) Microsoft Docs
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
ms.openlocfilehash: c1d43c7aad2501591c497475f6c250ac33712aa7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307740"
---
# <a name="testing-interoperable-applications"></a>Test des applications interopérables
Tester des applications interopérables est au mieux une entreprise qui prend beaucoup de temps et, au pire, impossible parce que de nouveaux conducteurs apparaissent continuellement sur le marché. Cependant, un degré raisonnable de tests est possible. Les applications avec une interopérabilité limitée ou faible n’ont qu’à être testées par rapport aux conducteurs qu’elles sont garanties de soutenir. Cependant, ils doivent être entièrement testés contre ces conducteurs.  
  
 Les applications hautement interopérables ne peuvent pas être testées pratiquement contre tous les conducteurs. Le mieux que la plupart des développeurs d’applications peuvent faire est de les tester pleinement contre un petit nombre de pilotes et maudire contre plusieurs autres. Les conducteurs testés devraient inclure les pilotes les plus populaires pour les DBMS les plus populaires sur le marché de l’application; si le marché couvre tous les DBMS, les pilotes pour les DBMS de bureau et de serveur doivent être testés.  
  
 L’un des problèmes dans le test des applications ODBC est le nombre de composants impliqués: l’application elle-même, le driver Manager, le pilote, le DBMS, et éventuellement un logiciel de réseau ou des passerelles. Les applications peuvent faciliter le suivi des erreurs en affichant les messages d’erreur retournés par les fonctions ODBC via **SQLGetDiagField** et **SQLGetDiagRec**. Ces messages identifient le fabricant et le composant dans lequel des erreurs se produisent. Pour plus d’informations, voir [Diagnostics](../../../odbc/reference/develop-app/diagnostics.md).
