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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0913458d683d7641145b262552e147033dbfc054
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63032838"
---
# <a name="scalar-function-escape-sequence"></a>Séquence d’échappement de fonction scalaire
ODBC utilise les séquences d’échappement pour les fonctions scalaires. La syntaxe de cette séquence d’échappement est comme suit :  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *Échappement ODBC-scalaire-fonction* :: =  
  
 *ODBC-ÉCHAP-initiateur* fn *fonction scalaire ODBC ÉCHAP-marque de fin*  
  
 *fonction scalaire* :: = *nom de la fonction* (*liste d’arguments*)  
  
 (Les définitions pour les éléments non terminaux *nom de la fonction* et *nom de la fonction* (*liste d’arguments*) sont dérivés de la liste des fonctions scalaires dans [ Annexe e : Fonctions scalaires](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *ODBC-esc-initiator* ::= {  
  
 *ODBC ÉCHAP-marque de fin* :: =}  
  
 Pour déterminer si la source de données prend en charge les procédures et le pilote prend en charge la syntaxe d’appel de procédure ODBC, une application peut appeler **SQLGetInfo**. Pour plus d’informations, consultez [annexe e : Fonctions scalaires](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
