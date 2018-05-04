---
title: Les séquences d’échappement intervalle | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e3a475170fed349a5bf85eb4f23bb93fe4ae804
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="interval-escape-sequences"></a>Séquences d’échappement d’intervalle
ODBC utilise les séquences d’échappement pour les littéraux de l’intervalle. La syntaxe de cette séquence d’échappement est comme suit :  
  
 {*intervalle-literal*}  
  
 Pour la syntaxe BNF de *intervalle-literal*, consultez la [syntaxe de littéral d’intervalle](../../../odbc/reference/appendixes/interval-literal-syntax.md) section plus loin dans cette annexe.  
  
 La séquence d’échappement des littéraux d’intervalle est pris en charge si les types de données d’intervalle sont pris en charge par la source de données. Une application doit appeler **SQLGetTypeInfo** pour déterminer si ces types de données sont pris en charge.
