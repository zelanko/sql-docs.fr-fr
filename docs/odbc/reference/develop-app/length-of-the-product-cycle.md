---
title: Durée du Cycle de produit | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], product cycle
- length of the product cycle [ODBC]
ms.assetid: 4d08d886-6d8b-40fd-8544-13032f4bf6c7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 203ad92dd6abfc71b0fdeddc466752612e666cee
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100452"
---
# <a name="length-of-the-product-cycle"></a>Longueur du cycle produit
La dernière question sur l’interopérabilité est le temps. Développement d’une application interopérable généralement prend plus de temps que de développer un noninteroperable. La raison est que l’application doit vérifier les fonctionnalités de SGBD, effectuer les mêmes tâches différemment pour différents SGBD, contourner les fonctionnalités prises en charge par certains SGBD, mais pas pour d’autres et ainsi de suite.  
  
 En plus de temps de développement, la durée de vie de produit doit être considérée. Si l’application est conçue pour être utilisée qu’une seule fois, par exemple une application qui transfère les données lors de la migration d’un SGBD à l’autre, aucun point n’existe dans rend interopérable. L’application sera utilisée qu’une seule fois et ignorée.  
  
 Si l’application existe pendant une longue période, il peut être plus facile à gérer en tant qu’une application interopérable. Cela est vrai même pour les applications personnalisées qui ont un SGBD unique en tant que cible. La raison est que le code interopérable utilise un sous-ensemble limité de fonctionnalités de base de données. Le pilote est nécessaire pour conserver les fonctionnalités disponibles, même en cas de modifications pour le SGBD sous-jacent. Par conséquent, code interopérable peut se déplacer la charge de la copie avec les modifications apportées au SGBD développeur de l’application pour le développement de pilotes.
