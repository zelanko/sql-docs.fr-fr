---
title: BETWEEN, prédicat | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4411345d790e64ae9fb21144a7d82ffe4cd45e8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63301959"
---
# <a name="between-predicate"></a>BETWEEN, prédicat
La syntaxe suivante :  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 Retourne true uniquement si *expression1* est supérieur ou égal à *expression2* et *expression1* est inférieure ou égale à *expression3*.  
  
 La sémantique de cette syntaxe est différente pour les pilotes de base de données de bureau et le moteur Microsoft Jet. Dans Microsoft Jet SQL, *expression2* peut être supérieur à *expression3* afin que l’instruction renvoie la valeur TRUE uniquement si *expression1* est supérieur ou égal à *expression3*, et *expression1* est inférieure ou égale à *expression2*.
