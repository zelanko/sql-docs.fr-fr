---
title: Description des paramètres | Microsoft Docs
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
ms.openlocfilehash: 2d32e5212ba1ba28262d871498f2974485d38233
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68040017"
---
# <a name="describing-parameters"></a>Description des paramètres
**SQLBindParameter** possède des arguments qui décrivent le paramètre : son type SQL, sa précision et son échelle. Le pilote utilise ces informations, ou *métadonnées,* pour convertir la valeur du paramètre en type requis par la source de données. À première vue, il peut sembler que le pilote soit dans une meilleure position pour connaître les métadonnées de paramètre que l’application. Après tout, le pilote peut facilement découvrir les métadonnées d’une colonne de jeu de résultats. Ce n’est pas le cas. Premièrement, la plupart des sources de données ne permettent pas au pilote de découvrir des métadonnées de paramètre. Deuxièmement, la plupart des applications connaissent déjà les métadonnées.  
  
 Si une instruction SQL est codée en dur dans l’application, le writer d’application connaît déjà le type de chaque paramètre. Si une instruction SQL est construite par l’application au moment de l’exécution, l’application peut déterminer les métadonnées lors de la génération de l’instruction. Par exemple, lorsque l’application construit la clause  
  
```  
WHERE OrderID = ?  
```  
  
 Il peut appeler **SQLColumns** pour la colonne OrderID.  
  
 La seule situation dans laquelle l’application ne peut pas facilement déterminer les métadonnées des paramètres est lorsque l’utilisateur entre une instruction paramétrable. Dans ce cas, l’application appelle **SQLPrepare** pour préparer l’instruction, **SQLNumParams** pour déterminer le nombre de paramètres et **SQLDescribeParam** pour décrire chaque paramètre. Toutefois, comme indiqué précédemment, la plupart des sources de données n’offrent pas de méthode permettant au pilote de découvrir les métadonnées de paramètre, de sorte que **SQLDescribeParam** n’est pas largement pris en charge.
