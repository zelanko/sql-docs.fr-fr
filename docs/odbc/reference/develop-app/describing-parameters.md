---
title: Décrivant les paramètres | Documents Microsoft
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
- SQLBindParameter function [ODBC], describing parameters
ms.assetid: 118d0f47-2afd-4955-bb47-38b1e2c2f38f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 629241f2385eeb3059800d35288b9c71d1d0ac97
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="describing-parameters"></a>Décrivant les paramètres
**SQLBindParameter** a des arguments qui décrivent le paramètre : son type SQL, la précision et l’échelle. Le pilote utilise ces informations, ou *métadonnées,* pour convertir la valeur du paramètre du type requis par la source de données. À première vue, il peut sembler que le pilote est en mesure de mieux connaître les métadonnées de paramètre que l’application ; Après tout, le pilote peut découvrir facilement les métadonnées de colonne du jeu de résultats. En fait, cela n’est pas le cas. Tout d’abord, la plupart des sources de données ne fournissent pas un moyen pour le pilote découvrir les métadonnées de paramètre. Ensuite, la plupart des applications connaissez déjà les métadonnées.  
  
 Si une instruction SQL est codée en dur dans l’application, le writer d’application connaît déjà le type de chaque paramètre. Si une instruction SQL est générée par l’application au moment de l’exécution, l’application peut déterminer les métadonnées, car elle génère l’instruction. Par exemple, lorsque l’application construit la clause  
  
```  
WHERE OrderID = ?  
```  
  
 elle peut appeler **SQLColumns** pour la colonne OrderID.  
  
 Le seul cas dans lequel l’application ne peut pas déterminer facilement les métadonnées de paramètre est lorsque l’utilisateur entre une instruction paramétrable. Dans ce cas, l’application appelle **SQLPrepare** pour préparer l’instruction, **SQLNumParams** pour déterminer le nombre de paramètres, et **SQLDescribeParam** pour décrire chaque paramètre. Toutefois, comme indiqué précédemment, la plupart des sources de données ne fournissent pas un moyen pour le pilote découvrir les métadonnées de paramètre, donc **SQLDescribeParam** n’est pas largement pris en charge.
