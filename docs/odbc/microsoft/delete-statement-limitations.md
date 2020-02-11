---
title: Limitations des instructions DELETE | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68096313"
---
# <a name="delete-statement-limitations"></a>DELETE, instruction - limitations
L’instruction DELETE n’est pas prise en charge pour Microsoft Excel ou le pilote texte. Notez que l’instruction INSERT est prise en charge pour le pilote Text.  
  
 Le pilote dBASE ne prend pas en charge l’empaquetage d’une table pour supprimer les valeurs « supprimées ».  
  
 Pour que le pilote Paradox supprime une ligne d’une table, la table doit avoir un index unique (clé primaire Paradox).
