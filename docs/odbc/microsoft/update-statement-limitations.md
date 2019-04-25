---
title: Mise à jour, instruction-Limitations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6b854cc417898c5576c60ca129c597eae280df4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633131"
---
# <a name="update-statement-limitations"></a>UPDATE, instruction - limitations
Pour le pilote Paradox mettre à jour une table, la table doit avoir un index unique (clé primaire). Lorsque vous utilisez le pilote Paradox sans avoir à implémenter le moteur de base de données Borland, il n’est pas possible de mettre à jour une table Paradox.  
  
 Pas de prise en charge par le pilote de texte.  
  
 Lorsque le pilote Microsoft Excel est utilisé, il est possible de mettre à jour les valeurs, mais une ligne ne peut pas être supprimée à partir d’une table basée sur une feuille de calcul Microsoft Excel. Par conséquent, l’instruction de mise à jour ne constitue pas officiellement pris en charge par le pilote Microsoft Excel. Seule l’instruction INSERT est considéré comme pris en charge.
