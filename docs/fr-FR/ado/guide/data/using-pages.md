---
title: À l’aide de Pages | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- PageSize property [ADO]
- pages [ADO]
- Recordset object [ADO]
- AbsolutePage property [ADO]
- PageCount property [ADO]
ms.assetid: 442b08c5-ccc7-4192-a1cc-22f250867782
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c52e7eedf020ca0885e3ede1e09ad0bc2a0adbf6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="using-pages"></a>À l’aide de Pages
Utilisez le **PageCount** propriété pour déterminer le nombre de pages de données dans le **Recordset** objet. *Pages* sont des groupes d’enregistrements dont la taille est égale à la **PageSize** paramètre de propriété. Même si la dernière page est incomplète, car il existe moins d’enregistrements que le **PageSize** valeur, elle est considérée comme une page supplémentaire dans le **PageCount** valeur. Si le **Recordset** objet ne prend pas en charge cette propriété, **PageCount** sera -1 pour indiquer que le **PageCount** est indéterminable.  
  
 Utilisez le **PageSize** propriété pour déterminer le nombre d’enregistrements constituant une page logique de données. L’établissement d’une taille de page vous permet d’utiliser le **AbsolutePage** propriété pour accéder au premier enregistrement d’une page particulière. Cela est utile dans les scénarios de serveur Web lorsque vous souhaitez autoriser l’utilisateur à parcourir les données, affichage d’un certain nombre d’enregistrements à la fois.  
  
 Cette propriété peut être définie à tout moment, et sa valeur sera utilisée pour le calcul de l’emplacement du premier enregistrement d’une page particulière.  
  
 Utilisez le **AbsolutePage** propriété pour identifier le numéro de page sur laquelle se trouve l’enregistrement actif. Là encore, le fournisseur doit prendre en charge les fonctionnalités requises pour cette propriété doit être disponible.  
  
 **AbsolutePage** basé sur 1 et est égale à 1 lorsque l’enregistrement actif est le premier enregistrement de la **Recordset**. Définissez cette propriété pour déplacer vers le premier enregistrement d’une page particulière. Obtenir le nombre total de pages à partir de la **PageCount** propriété.
