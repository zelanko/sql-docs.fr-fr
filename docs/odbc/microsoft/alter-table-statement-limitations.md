---
title: "Limitations d’instruction ALTER TABLE | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: acdeccfa07141c267a77a927217ad2ec610034c7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="alter-table-statement-limitations"></a>Limitations d’instruction ALTER TABLE
Lorsque le pilote dBASE ou Paradox est utilisé, une fois qu’un index a été créé et ajouté à un nouvel enregistrement, la structure de la table ne peut pas être modifiée par l’instruction ALTER TABLE, sauf si l’index est supprimé et le contenu de la table est supprimé.  
  
 Les instructions ALTER TABLE ne sont pas pris en charge pour les pilotes Microsoft Excel ou texte.  
  
> [!NOTE]  
>  Lorsque vous utilisez le pilote Paradox sans implémenter le moteur de base de données Borland, les instructions ALTER TABLE ne sont pas pris en charge ; uniquement lire et ajoutez les instructions sont autorisées.
