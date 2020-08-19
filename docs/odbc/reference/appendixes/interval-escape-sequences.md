---
description: Séquences d’échappement des intervalles
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
ms.openlocfilehash: e2ef792403352568ce5f8d92c07a5b0e1027b507
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483292"
---
# <a name="interval-escape-sequences"></a>Séquences d’échappement des intervalles
ODBC utilise des séquences d’échappement pour les littéraux d’intervalle. La syntaxe de cette séquence d’échappement est la suivante :  
  
 {*Interval-Literal*}  
  
 Pour la syntaxe BNF du *littéral Interval*, consultez la section [syntaxe du littéral d’intervalle](../../../odbc/reference/appendixes/interval-literal-syntax.md) plus loin dans cette annexe.  
  
 La séquence d’échappement littérale d’intervalle est prise en charge si les types de données Interval sont pris en charge par la source de données. Une application doit appeler **SQLGetTypeInfo** pour déterminer si ces types de données sont pris en charge.
