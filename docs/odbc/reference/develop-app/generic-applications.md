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
manager: craigg
ms.openlocfilehash: 59110f66c512845ff5ce1f2f246c05c63fa755b9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47751283"
---
# <a name="generic-applications"></a>Applications génériques
Applications génériques exécutent parfois une tâche codées en dur, par exemple une extraction de données à partir d’une base de données de feuille de calcul. Ils peuvent également effectuer diverses tâches définies par l’utilisateur, telle qu’une application de requête générique permettant à l’utilisateur entrer et exécuter une instruction SQL. Les applications génériques ont en commun est qu’ils doivent travailler avec un large éventail de SGBD différents et que le développeur ne sait pas au préalable ces SGBD sera.  
  
 Par conséquent, les applications génériques doivent être hautement interopérable. Le développeur doit effectuer des choix nombreux ajustant l’interopérabilité des fonctionnalités et doit écrire du code qui attend des pilotes pour prendre en charge un large éventail de fonctionnalités. Tandis que les applications génériques peuvent être paramétrées pour fonctionner avec SGBD courants, ils contiennent rarement code spécifiques au pilote ou propres au SGBD.
