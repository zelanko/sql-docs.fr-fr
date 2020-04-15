---
title: Séquences d’évasion d’intervalles Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304954"
---
# <a name="interval-escape-sequences"></a>Séquences d’échappement des intervalles
ODBC utilise des séquences d’évasion pour les littérals d’intervalle. La syntaxe de cette séquence d’évasion est la suivante :  
  
 -*intervalle-littéral*-  
  
 Pour la syntaxe BNF de *l’intervalle-littérale*, voir la section [Syntaxe littérale d’intervalle](../../../odbc/reference/appendixes/interval-literal-syntax.md) plus tard dans cette annexe.  
  
 La séquence d’évacuation littérale d’intervalle est prise en charge si les types de données d’intervalle sont pris en charge par la source de données. Une application devrait appeler **SQLGetTypeInfo** pour déterminer si ces types de données sont pris en charge.
