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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1f3ff800938574bec81e9cbb86839e014085a2a8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283853"
---
# <a name="between-predicate"></a>BETWEEN, prédicat
La syntaxe :  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 retourne true uniquement si *expression1* est supérieur ou égal à *Expression2* et que *expression1* est inférieur ou égal à *expression3*.  
  
 La sémantique de cette syntaxe est différente pour les pilotes de base de données de bureau et le moteur Microsoft Jet. Dans Microsoft Jet SQL, *Expression2* peut être supérieur à *expression3* afin que l’instruction retourne true uniquement si *expression1* est supérieur ou égal à *expression3*, et que *expression1* est inférieur ou égal à *Expression2*.
