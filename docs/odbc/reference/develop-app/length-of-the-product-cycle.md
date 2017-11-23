---
title: Longueur du Cycle de produit | Documents Microsoft
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
- interoperability [ODBC], product cycle
- length of the product cycle [ODBC]
ms.assetid: 4d08d886-6d8b-40fd-8544-13032f4bf6c7
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d58e64c6d53863c52d0e2194755e5d45ff1e99ae
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="length-of-the-product-cycle"></a>Longueur du Cycle de produit
La question finale sur l’interopérabilité est le temps. Développement d’une application interopérable généralement prend plu de développement d’un noninteroperable. La raison est que l’application doit vérifier les fonctionnalités SGBD, effectuer les mêmes tâches différemment pour les SGBD différents, contourner les fonctionnalités prises en charge par certains SGBD, mais pas les autres et ainsi de suite.  
  
 En plus de temps de développement, la durée de vie de produit doit être considérée. Si l’application est conçue pour être utilisée qu’une seule fois, par exemple, une application qui transfère les données lors de la migration d’un SGBD à l’autre, aucun point n’existe dans rend l’interopérable. L’application sera utilisée une seule fois et ignorée.  
  
 Si l’application existe pour un certain temps, il peut être plus facile à gérer comme une application interopérable. Cela est vrai même pour les applications personnalisées qui ont un SGBD unique en tant que cible. La raison est que l’interopérable code utilise un sous-ensemble des fonctionnalités de base de données. Le pilote est requis pour conserver les fonctionnalités disponibles, même en cas de modifications pour le SGBD sous-jacent. Par conséquent, code interopérable peut se déplacer la charge de la copie avec des modifications au SGBD développeur de l’application pour le développeur de pilote.
