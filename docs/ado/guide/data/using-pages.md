---
title: À l’aide de Pages | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- PageSize property [ADO]
- pages [ADO]
- Recordset object [ADO]
- AbsolutePage property [ADO]
- PageCount property [ADO]
ms.assetid: 442b08c5-ccc7-4192-a1cc-22f250867782
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6afd68ddf99799288939eeb0c6522275ec4d273f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704539"
---
# <a name="using-pages"></a>Utilisation de pages
Utilisez le **PageCount** propriété afin de déterminer le nombre de pages de données est dans le **Recordset** objet. *Pages* sont des groupes d’enregistrements dont la taille est égale à la **PageSize** paramètre de propriété. Même si la dernière page est incomplète, car il existe moins d’enregistrements que le **PageSize** valeur, elle est considérée comme une page supplémentaire dans le **PageCount** valeur. Si le **Recordset** objet ne prend pas en charge cette propriété, **PageCount** sera -1 pour indiquer que le **PageCount** est indéterminable.  
  
 Utilisez le **PageSize** propriété pour déterminer le nombre d’enregistrements constituant une page logique de données. L’établissement d’une taille de page vous permet d’utiliser le **AbsolutePage** propriété pour déplacer vers le premier enregistrement d’une page particulière. Cela est utile dans les scénarios de serveur Web lorsque vous souhaitez autoriser l’utilisateur à parcourir les données, en affichant un certain nombre d’enregistrements à la fois.  
  
 Cette propriété peut être définie à tout moment, et sa valeur sera utilisée pour le calcul de l’emplacement du premier enregistrement d’une page particulière.  
  
 Utilisez le **AbsolutePage** propriété pour identifier le numéro de page sur lequel se trouve l’enregistrement actif. Là encore, le fournisseur doit prendre en charge les fonctionnalités requises pour cette propriété doit être disponible.  
  
 **AbsolutePage** basé sur 1 et est égale à 1 lors de l’enregistrement actif est le premier enregistrement dans le **Recordset**. Définissez cette propriété pour déplacer vers le premier enregistrement d’une page particulière. Obtenir le nombre total de pages à partir de la **PageCount** propriété.
