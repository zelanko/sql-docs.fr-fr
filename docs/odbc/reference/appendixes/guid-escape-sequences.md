---
title: "GUID de séquences d’échappement | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC escape sequences [ODBC], GUID
- escape sequences [ODBC], guid
- guid escape sequence [ODBC]
ms.assetid: 71d43ef9-4a31-493e-b9e0-f864e9ef3ce6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d4ed6e517d9a8fa6f4c28c7b05541d36262df2a8
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="guid-escape-sequences"></a>Séquences d’échappement GUID
ODBC utilise les séquences d’échappement pour les littéraux de GUID. La syntaxe de cette séquence d’échappement est comme suit :  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Notes  
 Dans la notation BNF, la syntaxe est la suivante :  
  
 *Échappement de guid de ODBC* :: =  
     *Guid de l’initiateur-ÉCHAP ODBC* '*valeur de guid*' *ODBC ÉCHAP-marque de fin*  
  
 *ÉCHAP ODBC-initiateur* :: = {}  
  
 *Terminateur d’ÉCHAP ODBC* :: =}  
  
 *valeur de GUID* :: = *guid de l’horloge faible valeur de séparation des guid-séparateur de valeur du milieu d’horloge séparateur horloge forte valeur guid guid-séparateur de valeur clock-seq nœud-valeur*  
  
 *séparation des GUID* :: = -  
  
 *horloge faible valeur* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *valeur du milieu d’horloge* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *horloge importants* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *valeur d’horloge seq* :: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *valeur de nœud d’horloge* :: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *hex_digit* :: = 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; A &#124; B &#124; C &#124; D &#124; E &#124; F  
  
 La séquence d’échappement des littéraux de GUID est pris en charge si le type de données GUID est pris en charge par la source de données. Une application doit appeler **SQLGetTypeInfo** pour déterminer si ce type de données est prise en charge.
