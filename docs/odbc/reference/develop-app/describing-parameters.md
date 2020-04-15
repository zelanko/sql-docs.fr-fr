---
title: Décrire les paramètres Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f4d9284294707da0a469bf75ff9812ad5f7855bb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305940"
---
# <a name="describing-parameters"></a>Description des paramètres
**SQLBindParameter** a des arguments qui décrivent le paramètre : son type SQL, sa précision et son échelle. Le conducteur utilise ces informations, ou *métadonnées,* pour convertir la valeur du paramètre au type requis par la source de données. À première vue, il peut sembler que le conducteur est mieux placé pour connaître les métadonnées paramètres que l’application; après tout, le conducteur peut facilement découvrir les métadonnées pour une colonne de jeu de résultat. Il s’avère que ce n’est pas le cas. Tout d’abord, la plupart des sources de données ne fournissent pas un moyen pour le conducteur de découvrir les métadonnées paramètres. Deuxièmement, la plupart des applications connaissent déjà les métadonnées.  
  
 Si une déclaration SQL est codée dans l’application, l’auteur de l’application connaît déjà le type de chaque paramètre. Si une déclaration SQL est construite par l’application au moment de l’exécution, l’application peut déterminer les métadonnées au fur et à mesure qu’elle élabore l’énoncé. Par exemple, lorsque la demande construit la clause  
  
```  
WHERE OrderID = ?  
```  
  
 il peut appeler **SQLColumns** pour la colonne OrderID.  
  
 La seule situation dans laquelle l’application ne peut pas facilement déterminer les métadonnées paramètres est lorsque l’utilisateur entre une déclaration paramétisée. Dans ce cas, la demande appelle **SQLPrepare** pour préparer la déclaration, **SQLNumParams** pour déterminer le nombre de paramètres, et **SQLDescribeParam** pour décrire chaque paramètre. Cependant, comme cela a été mentionné précédemment, la plupart des sources de données ne fournissent pas un moyen pour le conducteur de découvrir les métadonnées paramètres, de sorte **QUE SQLDescribeParam** n’est pas largement pris en charge.
