---
title: "Limitations d’instruction ALTER TABLE | Documents Microsoft"
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
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b3969d9c8985cadba3d8e8e4ec72986660931109
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="alter-table-statement-limitations"></a>Limitations d’instruction ALTER TABLE
Lorsque le pilote dBASE ou Paradox est utilisé, une fois qu’un index a été créé et ajouté à un nouvel enregistrement, la structure de la table ne peut pas être modifiée par l’instruction ALTER TABLE, sauf si l’index est supprimé et le contenu de la table est supprimé.  
  
 Les instructions ALTER TABLE ne sont pas pris en charge pour les pilotes Microsoft Excel ou texte.  
  
> [!NOTE]  
>  Lorsque vous utilisez le pilote Paradox sans implémenter le moteur de base de données Borland, les instructions ALTER TABLE ne sont pas pris en charge ; uniquement lire et ajoutez les instructions sont autorisées.
