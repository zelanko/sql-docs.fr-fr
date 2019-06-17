---
title: Applications personnalisées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], custom applications
- custom applications [ODBC]
- interoperability [ODBC], levels
ms.assetid: f28178d9-ecd6-4e8c-9644-9bb624999dcb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ab470951162b5e4035c1253ed4ce425356ad8ec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63042525"
---
# <a name="custom-applications"></a>Applications personnalisées
En règle générale, des applications personnalisées effectuent une tâche spécifique pour certains SGBD. Par exemple, une application peut récupérer des données à partir d’un SGBD unique et générer un rapport, ou il peut transférer des données entre plusieurs SGBD. Ce que ces applications ont en commun est que ces SGBD est connues avant l’écriture de l’application et est peu susceptibles de changer pendant la durée de vie de l’application.  
  
 Par conséquent, l’application personnalisée requiert l’interopérabilité peu ou pas. Le développeur d’applications peut choisir un seul pilote pour chaque SGBD et le code directement à ces pilotes. L’application peut contenir en toute sécurité de code spécifiques au pilote pour exploiter les fonctions de ces pilotes et peut même effectuer des appels à l’API de base de données natif à utiliser les fonctionnalités non prises en charge par ODBC.  
  
 La préoccupation majeure de l’interopérabilité de la plupart des applications personnalisées est que la cible SGBD changera à l’avenir. Dans ce cas, ce processus peut être simplifié en écrivant du code plus interopérable pour commencer. Toutefois, cette modification de SGBD est rare et implique généralement une grande quantité de travail. Pour cette raison, les développeurs d’applications personnalisées rarement choisir d’augmenter l’interopérabilité au détriment de la fonctionnalité ; ils généralement choisir de les réécrire cette fonctionnalité quand ils changent les SGBD.
