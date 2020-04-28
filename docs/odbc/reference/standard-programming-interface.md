---
title: Interface de programmation standard | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], programming interface
- programming interface standardization [ODBC]
ms.assetid: a2fa727e-51f2-4123-ae25-0ee28e611231
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c7767f113d0f70569ce253f0200cd35cb83915a4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81279995"
---
# <a name="standard-programming-interface"></a>Interface de programmation standard
L’interface de programmation est peut-être le candidat le plus évident pour la normalisation. En fait, lors du développement d’ODBC, ANSI et ISO offraient déjà des normes pour les modules SQL et SQL incorporés. Bien qu’il n’existait pas de normes pour une interface de commande de base de données, le groupe d’accès SQL (un consortium de fournisseurs de bases de données) a envisagé d’en créer un. les parties d’ODBC sont ensuite devenues la base de leur travail.  
  
 L’une des conditions requises pour ODBC était qu’un seul fichier binaire d’application devait fonctionner avec plusieurs SGBD. C’est pour cette raison que ODBC n’utilise pas les langages Embedded SQL ou module. Bien que le langage dans Embedded SQL et les langages de module soit standardisé, chacun est lié à des précompilations propres au SGBD. Ainsi, les applications doivent être recompilées pour chaque SGBD et les binaires résultants fonctionnent uniquement avec un seul SGBD. Bien que cela soit acceptable pour les applications de faible volume détectées dans les mondes des ordinateurs et des ordinateurs de macroordinateurs, ce n’est pas inacceptable dans le monde des ordinateurs personnels. Tout d’abord, il s’agit d’un cauchemar logistique qui consiste à fournir plusieurs versions de logiciels volumineux et compactés à des clients ; Deuxièmement, les applications d’ordinateur personnel doivent souvent accéder simultanément à plusieurs SGBD.  
  
 D’un autre côté, une interface au niveau de l’appel peut être implémentée via des bibliothèques, ou des pilotes de base de données, qui résident sur chaque ordinateur local ; un autre pilote est requis pour chaque SGBD. Étant donné que les systèmes d’exploitation modernes peuvent charger ces bibliothèques (telles que les bibliothèques de liens dynamiques sur le système d’exploitation Microsoft® Windows®) au moment de l’exécution, une seule application peut accéder aux données à partir de différents SGBD sans recompilation et peut également accéder aux données de plusieurs bases de données simultanément. À mesure que de nouveaux pilotes de base de données deviennent disponibles, les utilisateurs peuvent simplement les installer sur leurs ordinateurs sans avoir à modifier, recompiler ou lier leurs applications de base de données. En outre, une interface au niveau de l’appel était un bon candidat pour ODBC, car Windows, la plateforme pour laquelle ODBC a été développé à l’origine-déjà utilisé de telles bibliothèques.
