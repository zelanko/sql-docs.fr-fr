---
title: ALTER TABLE, instruction-Limitations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, ALTER TABLE statement limitations
- ALTER TABLE statement limitations [ODBC]
ms.assetid: f3e88f85-edf4-47cd-a822-292b106ddb34
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1333cd6cd5946b7a3a70152e12f4d3decfa7fed0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138430"
---
# <a name="alter-table-statement-limitations"></a>ALTER TABLE, instruction - limitations
Lorsque le pilote dBASE ou Paradox est utilisé, une fois qu’un index a été créé et ajouté à un nouvel enregistrement, la structure de la table ne peut pas être modifiée par l’instruction ALTER TABLE, sauf si l’index est supprimé et le contenu de la table est supprimé.  
  
 Les instructions ALTER TABLE ne sont pas pris en charge pour les pilotes Microsoft Excel ou texte.  
  
> [!NOTE]  
>  Lorsque vous utilisez le pilote Paradox sans avoir à implémenter le moteur de base de données Borland, les instructions ALTER TABLE ne sont pas pris en charge ; uniquement lire et ajoutez les instructions sont autorisées.
