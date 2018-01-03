---
title: "Limitations d’instruction de mise à jour | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UPDATE statement limitations [ODBC]
- ODBC SQL grammar, UPDATE statement limitations
ms.assetid: 14700aac-e135-4dc0-9138-4b01224461d5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8746a3a54ba46b418262f94c0c19d778d718571f
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="update-statement-limitations"></a>Limitations d’instruction de mise à jour
Pour le pilote Paradox mettre à jour une table, la table doit avoir un index unique (clé primaire). Lorsque vous utilisez le pilote Paradox sans implémenter le moteur de base de données Borland, il n’est pas possible de mettre à jour une table Paradox.  
  
 Non pris en charge par le pilote de texte.  
  
 Lorsque le pilote Microsoft Excel est utilisé, il est possible de mettre à jour les valeurs, mais une ligne ne peut pas être supprimée à partir d’une table basée sur une feuille de calcul Microsoft Excel. Par conséquent, l’instruction de mise à jour ne constitue pas officiellement pris en charge par le pilote Microsoft Excel. Seule l’instruction INSERT est considéré comme pris en charge.
