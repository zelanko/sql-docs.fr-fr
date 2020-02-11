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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6b1544f5562468db03a649c263993039a722a3c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139297"
---
# <a name="generic-applications"></a>Applications génériques
Les applications génériques effectuent parfois une tâche codée en dur, telle qu’une feuille de calcul qui récupère les données d’une base de données. Ils peuvent également effectuer diverses tâches définies par l’utilisateur, telles qu’une application de requête générique permettant à l’utilisateur d’entrer et d’exécuter une instruction SQL. Les applications génériques sont en commun : elles doivent fonctionner avec différents SGBD et que le développeur ne sache pas à l’avance ce que seront les SGBD.  
  
 Par conséquent, les applications génériques doivent être très interopérables. Le développeur doit faire de nombreux choix, commercialiser l’interopérabilité pour les fonctionnalités et écrire du code qui s’attend à ce que les pilotes prennent en charge un large éventail de fonctionnalités. Alors que les applications génériques peuvent être paramétrées pour fonctionner avec des SGBD répandus, elles contiennent rarement du code spécifique au pilote ou au SGBD.
