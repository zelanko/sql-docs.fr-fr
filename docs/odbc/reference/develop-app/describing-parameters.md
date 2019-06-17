---
title: Décrivant les paramètres | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], describing parameters
ms.assetid: 118d0f47-2afd-4955-bb47-38b1e2c2f38f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1bc752afc0cb5214e629a343c35464e612b57c36
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63049839"
---
# <a name="describing-parameters"></a>Description des paramètres
**SQLBindParameter** a des arguments qui décrivent le paramètre : son type SQL, la précision et l’échelle. Le pilote utilise ces informations, ou *métadonnées,* pour convertir la valeur du paramètre du type requis par la source de données. À première vue, il peut sembler que le pilote est mieux connaître les métadonnées de paramètre que l’application ; Après tout, le pilote peut découvrir facilement les métadonnées pour un résultat de jeu de colonnes. En fait, cela n’est pas le cas. Tout d’abord, la plupart des sources de données ne fournissent pas un moyen pour le pilote découvrir les métadonnées de paramètre. Ensuite, la plupart des applications connaissez déjà les métadonnées.  
  
 Si une instruction SQL est codé en dur dans l’application, le rédacteur d’application connaît déjà le type de chaque paramètre. Si une instruction SQL est générée par l’application au moment de l’exécution, l’application peut déterminer les métadonnées, car elle génère l’instruction. Par exemple, lorsque l’application construit la clause  
  
```  
WHERE OrderID = ?  
```  
  
 elle peut appeler **SQLColumns** pour la colonne OrderID.  
  
 Le seul cas dans lequel l’application ne peut pas déterminer facilement les métadonnées de paramètre est lorsque l’utilisateur entre une instruction paramétrable. Dans ce cas, l’application appelle **SQLPrepare** pour préparer l’instruction, **SQLNumParams** pour déterminer le nombre de paramètres, et **SQLDescribeParam** pour décrire chaque paramètre. Toutefois, comme indiqué précédemment, la plupart des sources de données ne fournissent pas un moyen pour le pilote découvrir les métadonnées de paramètre, donc **SQLDescribeParam** n’est pas largement pris en charge.
