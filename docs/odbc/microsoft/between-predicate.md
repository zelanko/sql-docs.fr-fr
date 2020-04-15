---
title: BETWEEN Predicate ( France Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283853"
---
# <a name="between-predicate"></a>BETWEEN, prédicat
La syntaxe :  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 rendements vrais seulement si *l’expression1* est supérieure ou égale à *l’expression2* et *l’expression1* est inférieure ou égale à *l’expression3*.  
  
 La sémantique de cette syntaxe est différente pour les pilotes de base de données de bureau et le moteur Microsoft Jet. Dans Microsoft Jet SQL, *l’expression2* peut être supérieure à *l’expression3* de sorte que la déclaration ne retournera VRAI que si *l’expression1* est supérieure ou égale à *l’expression3*, et *l’expression1* est inférieure ou égale à *l’expression2*.
