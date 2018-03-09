---
title: "Limitations d’instruction DELETE | Documents Microsoft"
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
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cce6402f913348dd3b9aa3d116b7ceffb5a55ea4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="delete-statement-limitations"></a>SUPPRIMER les Limitations de l’instruction
L’instruction DELETE n’est pas prise en charge pour le pilote Microsoft Excel ou texte. Notez que l’instruction INSERT est pris en charge pour le pilote de texte.  
  
 Le pilote dBASE ne prend pas en charge la compression d’une table pour supprimer les valeurs de « supprimé ».  
  
 Pour le pilote Paradox supprimer une ligne d’une table, la table doit avoir un index unique (clé primaire).
