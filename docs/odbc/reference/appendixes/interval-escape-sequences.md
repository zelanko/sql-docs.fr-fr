---
title: Séquences d’échappement d’intervalle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 69c674ee8838273af9bf4ed91ddcead7e1768fb9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041640"
---
# <a name="interval-escape-sequences"></a>Séquences d’échappement des intervalles
ODBC utilise des séquences d’échappement pour les littéraux d’intervalle. La syntaxe de cette séquence d’échappement est la suivante :  
  
 {*Interval-Literal*}  
  
 Pour la syntaxe BNF du *littéral Interval*, consultez la section [syntaxe du littéral d’intervalle](../../../odbc/reference/appendixes/interval-literal-syntax.md) plus loin dans cette annexe.  
  
 La séquence d’échappement littérale d’intervalle est prise en charge si les types de données Interval sont pris en charge par la source de données. Une application doit appeler **SQLGetTypeInfo** pour déterminer si ces types de données sont pris en charge.
