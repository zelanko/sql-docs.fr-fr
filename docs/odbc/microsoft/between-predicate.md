---
description: BETWEEN, prédicat
title: ENTRE prédicat | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- BETWEEN predicate [ODBC]
- SQL grammar [ODBC], between predicate
ms.assetid: 0cc7464b-d788-4720-98d8-411e1169185f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2f2283f5824e4be0c9702bfe8feef9fe3109849a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500382"
---
# <a name="between-predicate"></a>BETWEEN, prédicat
La syntaxe :  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 retourne true uniquement si *expression1* est supérieur ou égal à *Expression2* et que *expression1* est inférieur ou égal à *expression3*.  
  
 La sémantique de cette syntaxe est différente pour les pilotes de base de données de bureau et le moteur Microsoft Jet. Dans Microsoft Jet SQL, *Expression2* peut être supérieur à *expression3* afin que l’instruction retourne true uniquement si *expression1* est supérieur ou égal à *expression3*, et que *expression1* est inférieur ou égal à *Expression2*.
