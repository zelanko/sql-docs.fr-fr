---
title: Séquences d’échappement GUID | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bf41671abc6393a18fad06e1debd297fed1f04c5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654979"
---
# <a name="guid-escape-sequences"></a>Séquences d’échappement de GUID
ODBC utilise les séquences d’échappement pour les littéraux de GUID. La syntaxe de cette séquence d’échappement est comme suit :  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *Échappement ODBC-guid* :: =  
     *Guid de l’initiateur-ÉCHAP ODBC* '*valeur de guid*' *ODBC ÉCHAP-marque de fin*  
  
 *ODBC-ÉCHAP-initiateur* :: = {}  
  
 *ODBC ÉCHAP-marque de fin* :: =}  
  
 *valeur de GUID* :: = *horloge faible valeur guid-séparateur horloge-intermédiaire-valeur guid-séparateur horloge grande valeur guid-séparateur clock-seq-valeur guid-nœud-valeur de séparateur*  
  
 *séparation des GUID* :: = -  
  
 *horloge faible valeur* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *valeur du milieu d’horloge* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *horloge de grande valeur* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *valeur Clock-seq* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *valeur de nœud horloge* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *hex_digit* :: = 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; A &#124; B &#124; C &#124; D &#124; E &#124; F  
  
 La séquence d’échappement de littéral de GUID est pris en charge si le type de données GUID est pris en charge par la source de données. Une application doit appeler **SQLGetTypeInfo** pour déterminer si ce type de données est prise en charge.
