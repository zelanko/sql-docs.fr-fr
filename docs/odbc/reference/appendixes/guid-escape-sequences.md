---
title: Séquences d’évasion GUID (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], GUID
- escape sequences [ODBC], guid
- guid escape sequence [ODBC]
ms.assetid: 71d43ef9-4a31-493e-b9e0-f864e9ef3ce6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 44907bfbd884bf361ce5f2ab8b3f6d8a247aba44
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306970"
---
# <a name="guid-escape-sequences"></a>Séquences d’échappement de GUID
ODBC utilise des séquences d’évasion pour les littérals GUID. La syntaxe de cette séquence d’évasion est la suivante :  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *ODBC-guid-escape* ::  
     *Guid ODBC-esc-initiateur* '*guid-value*' *ODBC-esc-terminator*  
  
 *ODBC-esc-initiateur* ::  
  
 *ODBC-esc-terminator* ::  
  
 *guid-value* :: *'clock-low-value guid-separator clock-middle-value guid-separator clock-high-value guid-separator clock-seq-value guid-separator node-value*  
  
 *guid-séparateur* ::- -  
  
 *horloge-faible valeur* ::' hex_digit hex_digit *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *horloge-valeur moyenne* ::' *hex_digit hex_digit hex_digit hex_digit*  
  
 *horloge-haute valeur* ::' *hex_digit hex_digit hex_digit hex_digit*  
  
 *horloge-seq-valeur* ::' *hex_digit hex_digit hex_digit hex_digit*  
  
 *valeur de l’horloge-noeud* :: hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit *hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *hex_digit* ::0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; A &#124; B &#124; C &#124; D &#124; E &#124; F  
  
 La séquence d’évacuation littérale GUID est prise en charge si le type de données GUID est pris en charge par la source de données. Une application doit appeler **SQLGetTypeInfo** pour déterminer si ce type de données est pris en charge.
