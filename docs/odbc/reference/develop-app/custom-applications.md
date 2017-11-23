---
title: "Applications personnalisées | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC], custom applications
- custom applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: f28178d9-ecd6-4e8c-9644-9bb624999dcb
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fe974d13b438cdb7fe010a35621665557cf2af8d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="custom-applications"></a>Applications personnalisées
Applications personnalisées effectuent une tâche spécifique pour quelques SGBD. Par exemple, une application peut récupérer des données à partir d’un SGBD unique et générer un rapport, ou il peut transférer des données entre plusieurs SGBD. Ce que ces applications ont en commun est que ces SGBD est connues avant l’écriture de l’application et qu’il est peu probable que l’évolution de la durée de vie de l’application.  
  
 Par conséquent, l’application personnalisée requiert peu ou pas de l’interopérabilité. Le développeur peut choisir un pilote unique pour chaque SGBD et le code directement à ces pilotes. L’application peut contenir en toute sécurité de code spécifiques au pilote pour exploiter les fonctions de ces pilotes et peut même effectuer des appels à l’API de base de données native pour utiliser les fonctionnalités non prises en charge par ODBC.  
  
 La préoccupation majeure de l’interopérabilité de la plupart des applications personnalisées est si la SGBD cible sera changer à l’avenir. Dans ce cas, ce processus peut être simplifié en écrivant du code plus interopérable pour commencer. Toutefois, cette modification de SGBD est rare et généralement implique une grande quantité de travail. Pour cette raison, les développeurs d’applications personnalisées rarement choisir d’augmenter l’interopérabilité au détriment de la fonctionnalité ; généralement choisissent de réécrire ces fonctionnalités quand ils changent le SGBD.
