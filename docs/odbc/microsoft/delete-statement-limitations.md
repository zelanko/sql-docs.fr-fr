---
description: DELETE, instruction - limitations
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5ffb3a6d0ab28fc2b8bc8785df586ac6bbc86aa0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340895"
---
# <a name="delete-statement-limitations"></a>DELETE, instruction - limitations
L’instruction DELETE n’est pas prise en charge pour Microsoft Excel ou le pilote texte. Notez que l’instruction INSERT est prise en charge pour le pilote Text.  
  
 Le pilote dBASE ne prend pas en charge l’empaquetage d’une table pour supprimer les valeurs « supprimées ».  
  
 Pour que le pilote Paradox supprime une ligne d’une table, la table doit avoir un index unique (clé primaire Paradox).
