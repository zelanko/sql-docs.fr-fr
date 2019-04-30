---
title: Les séquences d’échappement intervalle | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 81481db74d973da0e54bc6bf9e70550fa3cc0c81
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188887"
---
# <a name="interval-escape-sequences"></a>Séquences d’échappement des intervalles
ODBC utilise les séquences d’échappement pour les littéraux d’intervalle. La syntaxe de cette séquence d’échappement est comme suit :  
  
 {*interval-literal*}  
  
 Pour connaître la syntaxe BNF de *littéral d’intervalle*, consultez le [syntaxe de littéral d’intervalle](../../../odbc/reference/appendixes/interval-literal-syntax.md) section plus loin dans cette annexe.  
  
 La séquence d’échappement des littéraux d’intervalle est pris en charge si les types de données d’intervalle sont pris en charge par la source de données. Une application doit appeler **SQLGetTypeInfo** pour déterminer si ces types de données sont pris en charge.
