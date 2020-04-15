---
title: Longueur du cycle de produits (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d235146ffe1b4699f0064c5772407bcf40ae962
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306192"
---
# <a name="length-of-the-product-cycle"></a>Longueur du cycle produit
La dernière question sur l’interopérabilité est le temps. Le développement d’une application interopérable prend généralement plus de temps que le développement d’une application non interutilisable. La raison en est que l’application doit vérifier les capacités DBMS, effectuer les mêmes tâches différemment pour différents DBMS, travailler autour de fonctionnalités prises en charge par certains DBMS, mais pas d’autres, et ainsi de suite.  
  
 En plus du temps de développement, la durée de vie du produit doit être prise en considération. Si l’application est conçue pour être utilisée une fois, comme une application qui transfère des données lors de la migration d’un DBMS à l’autre, il est inutile de la rendre interopérable. L’application sera utilisée une fois et jetée.  
  
 Si l’application existe pendant une longue période, il pourrait être plus facile à maintenir comme une application interopérable. Cela est vrai même pour les applications personnalisées qui ont un seul DBMS comme cible. La raison en est que le code interopérable utilise un sous-ensemble limité de fonctionnalités de base de données. Le conducteur est tenu de garder ces fonctionnalités disponibles, même en cas de changements à la DBMS sous-jacente. Ainsi, le code interopérable peut transférer le fardeau de faire face aux modifications apportées à la DBMS du développeur d’applications au développeur du conducteur.
