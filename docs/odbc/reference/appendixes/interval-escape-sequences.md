---
title: "Les séquences d’échappement intervalle | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interval literals [ODBC]
- escape sequences [ODBC], interval
- ODBC escape sequences [ODBC], interval
ms.assetid: 303e8dab-8f13-4fa5-857f-15cc1f75bdd6
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: faaafb71236b9d3b2aa15aa67a80211bbce493a1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="interval-escape-sequences"></a>Séquences d’échappement d’intervalle
ODBC utilise les séquences d’échappement pour les littéraux de l’intervalle. La syntaxe de cette séquence d’échappement est comme suit :  
  
 {*intervalle-literal*}  
  
 Pour la syntaxe BNF de *intervalle-literal*, consultez la [syntaxe de littéral d’intervalle](../../../odbc/reference/appendixes/interval-literal-syntax.md) section plus loin dans cette annexe.  
  
 La séquence d’échappement des littéraux d’intervalle est pris en charge si les types de données d’intervalle sont pris en charge par la source de données. Une application doit appeler **SQLGetTypeInfo** pour déterminer si ces types de données sont pris en charge.
