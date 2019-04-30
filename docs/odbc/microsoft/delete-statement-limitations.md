---
title: DELETE, instruction-Limitations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DELETE statement limitations [ODBC]
- ODBC SQL grammar, DELETE statement limitations
ms.assetid: 084761fe-e65b-4f38-ba4f-69884b2a7700
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 98bd56051c724186d7308eff669263d29b82ecd5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63198171"
---
# <a name="delete-statement-limitations"></a>DELETE, instruction - limitations
L’instruction DELETE n’est pas pris en charge pour le pilote Microsoft Excel ou texte. Notez que l’instruction INSERT est prise en charge pour le pilote de texte.  
  
 Le pilote dBASE ne prend pas en charge la compression d’une table pour supprimer les valeurs « supprimé ».  
  
 Pour le pilote Paradox supprimer une ligne d’une table, la table doit avoir un index unique (clé primaire).
