---
title: Limitations des instructions ALTER TABLE | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138430"
---
# <a name="alter-table-statement-limitations"></a>ALTER TABLE, instruction - limitations
Lorsque le pilote dBASE ou Paradox est utilisé, une fois qu’un index a été créé et qu’un nouvel enregistrement a été ajouté, la structure de la table ne peut pas être modifiée par l’instruction ALTER TABLE, sauf si l’index est supprimé et si le contenu de la table est supprimé.  
  
 Les instructions ALTER TABLE ne sont pas prises en charge pour Microsoft Excel ou les pilotes texte.  
  
> [!NOTE]  
>  Lorsque vous utilisez le pilote Paradox sans implémenter le Moteur de base de données Borland, les instructions ALTER TABLE ne sont pas prises en charge. seules les instructions Read et Append sont autorisées.
