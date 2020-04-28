---
title: Séquence d’échappement de fonction scalaire | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8347b8e6f0fab6dffc5295fb3b8260a6a56ed123
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305072"
---
# <a name="scalar-function-escape-sequence"></a>Séquence d’échappement de fonction scalaire
ODBC utilise des séquences d’échappement pour les fonctions scalaires. La syntaxe de cette séquence d’échappement est la suivante :  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *ODBC-scalaire-fonction-Escape* :: =  
  
 *ODBC-ESC-initiateur* Fn *scalaire-fonction ODBC-ESC-terminateur*  
  
 *scalaire-Function* :: = *nom-fonction* (*liste d’arguments*)  
  
 (Les définitions pour les fonctions non Terminals *nom-fonction* et *nom-fonction* (*liste d’arguments*) sont dérivées de la liste des fonctions scalaires dans [annexe E : fonctions scalaires](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *ODBC-Echap-Initiator* :: = {  
  
 *ODBC-ESC-terminateur* :: =}  
  
 Pour déterminer si la source de données prend en charge les procédures et que le pilote prend en charge la syntaxe d’appel de procédure ODBC, une application peut appeler **SQLGetInfo**. Pour plus d’informations, consultez [l’annexe E : fonctions scalaires](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
