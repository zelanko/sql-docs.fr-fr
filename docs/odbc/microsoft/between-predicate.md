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
ms.openlocfilehash: 1a0ac99729966acdcb03c2aab0175c34bba0c08a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138119"
---
# <a name="between-predicate"></a>BETWEEN, prédicat
La syntaxe suivante :  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 Retourne true uniquement si *expression1* est supérieur ou égal à *expression2* et *expression1* est inférieure ou égale à *expression3*.  
  
 La sémantique de cette syntaxe est différente pour les pilotes de base de données de bureau et le moteur Microsoft Jet. Dans Microsoft Jet SQL, *expression2* peut être supérieur à *expression3* afin que l’instruction renvoie la valeur TRUE uniquement si *expression1* est supérieur ou égal à *expression3*, et *expression1* est inférieure ou égale à *expression2*.
