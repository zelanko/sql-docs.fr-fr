---
title: "À l’aide de Pages | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PageSize property [ADO]
- pages [ADO]
- Recordset object [ADO]
- AbsolutePage property [ADO]
- PageCount property [ADO]
ms.assetid: 442b08c5-ccc7-4192-a1cc-22f250867782
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 00394ba3e6a7e07e36ab28d0899c5ea1e6ff32ef
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="using-pages"></a>À l’aide de Pages
Utilisez le **PageCount** propriété pour déterminer le nombre de pages de données dans le **Recordset** objet. *Pages* sont des groupes d’enregistrements dont la taille est égale à la **PageSize** paramètre de propriété. Même si la dernière page est incomplète, car il existe moins d’enregistrements que le **PageSize** valeur, elle est considérée comme une page supplémentaire dans le **PageCount** valeur. Si le **Recordset** objet ne prend pas en charge cette propriété, **PageCount** sera -1 pour indiquer que le **PageCount** est indéterminable.  
  
 Utilisez le **PageSize** propriété pour déterminer le nombre d’enregistrements constituant une page logique de données. L’établissement d’une taille de page vous permet d’utiliser le **AbsolutePage** propriété pour accéder au premier enregistrement d’une page particulière. Cela est utile dans les scénarios de serveur Web lorsque vous souhaitez autoriser l’utilisateur à parcourir les données, affichage d’un certain nombre d’enregistrements à la fois.  
  
 Cette propriété peut être définie à tout moment, et sa valeur sera utilisée pour le calcul de l’emplacement du premier enregistrement d’une page particulière.  
  
 Utilisez le **AbsolutePage** propriété pour identifier le numéro de page sur laquelle se trouve l’enregistrement actif. Là encore, le fournisseur doit prendre en charge les fonctionnalités requises pour cette propriété doit être disponible.  
  
 **AbsolutePage** basé sur 1 et est égale à 1 lorsque l’enregistrement actif est le premier enregistrement de la **Recordset**. Définissez cette propriété pour déplacer vers le premier enregistrement d’une page particulière. Obtenir le nombre total de pages à partir de la **PageCount** propriété.
