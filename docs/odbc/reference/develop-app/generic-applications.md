---
title: Applications génériques | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 607676d5370f02ee1d39196bff9261bc897521ee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305550"
---
# <a name="generic-applications"></a>Applications génériques
Les applications génériques effectuent parfois une tâche codée en dur, telle qu’une feuille de calcul qui récupère les données d’une base de données. Ils peuvent également effectuer diverses tâches définies par l’utilisateur, telles qu’une application de requête générique permettant à l’utilisateur d’entrer et d’exécuter une instruction SQL. Les applications génériques sont en commun : elles doivent fonctionner avec différents SGBD et que le développeur ne sache pas à l’avance ce que seront les SGBD.  
  
 Par conséquent, les applications génériques doivent être très interopérables. Le développeur doit faire de nombreux choix, commercialiser l’interopérabilité pour les fonctionnalités et écrire du code qui s’attend à ce que les pilotes prennent en charge un large éventail de fonctionnalités. Alors que les applications génériques peuvent être paramétrées pour fonctionner avec des SGBD répandus, elles contiennent rarement du code spécifique au pilote ou au SGBD.
