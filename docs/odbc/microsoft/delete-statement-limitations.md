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
ms.openlocfilehash: eb2587f733f5042436144f7865627fee576e3d9c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096313"
---
# <a name="delete-statement-limitations"></a>DELETE, instruction - limitations
L’instruction DELETE n’est pas pris en charge pour le pilote Microsoft Excel ou texte. Notez que l’instruction INSERT est prise en charge pour le pilote de texte.  
  
 Le pilote dBASE ne prend pas en charge la compression d’une table pour supprimer les valeurs « supprimé ».  
  
 Pour le pilote Paradox supprimer une ligne d’une table, la table doit avoir un index unique (clé primaire).
