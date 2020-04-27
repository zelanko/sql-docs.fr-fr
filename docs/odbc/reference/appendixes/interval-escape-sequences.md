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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9fe7f6941e9ec9fba8b6698faaa18a678732dd6f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304954"
---
# <a name="interval-escape-sequences"></a>Séquences d’échappement des intervalles
ODBC utilise des séquences d’échappement pour les littéraux d’intervalle. La syntaxe de cette séquence d’échappement est la suivante :  
  
 {*Interval-Literal*}  
  
 Pour la syntaxe BNF du *littéral Interval*, consultez la section [syntaxe du littéral d’intervalle](../../../odbc/reference/appendixes/interval-literal-syntax.md) plus loin dans cette annexe.  
  
 La séquence d’échappement littérale d’intervalle est prise en charge si les types de données Interval sont pris en charge par la source de données. Une application doit appeler **SQLGetTypeInfo** pour déterminer si ces types de données sont pris en charge.
