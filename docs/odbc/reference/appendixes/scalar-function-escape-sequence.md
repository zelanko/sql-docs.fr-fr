---
title: Séquence d’évasion de fonction scalaire (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305072"
---
# <a name="scalar-function-escape-sequence"></a>Séquence d’échappement de fonction scalaire
ODBC utilise des séquences d’évasion pour des fonctions scalaires. La syntaxe de cette séquence d’évasion est la suivante :  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *ODBC-scalar-function-escape* ::  
  
 *ODBC-esc-initiateur* fn *scalar-function ODBC-esc-terminator*  
  
 *fonction scalaire* ::md *fonction-nom* *(argument-liste*)  
  
 (Les définitions du nom *de fonction* et du *nom de fonction* *(liste d’arguments)* sont dérivées de la liste des fonctions scalaires de [l’Annexe E : Fonctions Scalar](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *ODBC-esc-initiateur* ::  
  
 *ODBC-esc-terminator* ::  
  
 Pour déterminer si la source de données prend en charge les procédures et le conducteur prend en charge la syntaxe d’invocation de la procédure ODBC, une application peut appeler **SQLGetInfo**. Pour plus d’informations, voir [Annexe E: Scalar Functions](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
