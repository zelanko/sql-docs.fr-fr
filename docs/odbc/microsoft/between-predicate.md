---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1a0ac99729966acdcb03c2aab0175c34bba0c08a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138119"
---
# <a name="between-predicate"></a>BETWEEN, prédicat
La syntaxe :  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 retourne true uniquement si *expression1* est supérieur ou égal à *Expression2* et que *expression1* est inférieur ou égal à *expression3*.  
  
 La sémantique de cette syntaxe est différente pour les pilotes de base de données de bureau et le moteur Microsoft Jet. Dans Microsoft Jet SQL, *Expression2* peut être supérieur à *expression3* afin que l’instruction retourne true uniquement si *expression1* est supérieur ou égal à *expression3*, et que *expression1* est inférieur ou égal à *Expression2*.
