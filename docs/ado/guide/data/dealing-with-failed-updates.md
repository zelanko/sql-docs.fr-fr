---
title: Gestion des mises à jour ayant échoués | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- updates [ADO], dealing with failed updates
ms.assetid: 299c37bd-19ff-4261-8571-b9665687e075
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6ba4b4189691bf907b3ad67db91a8534268a8ec0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616427"
---
# <a name="dealing-with-failed-updates"></a>Traitement des mises à jour ayant échoué
Lorsqu’une mise à jour est terminée avec des erreurs, comment vous résolvez les erreurs varie selon la nature et la gravité des erreurs et la logique de votre application. Toutefois, si la base de données est partagée avec d’autres utilisateurs, une erreur typique est que quelqu'un d’autre modifie le champ avant de procéder. Ce type d’erreur est appelé un conflit. ADO détecte cette situation et signale une erreur.  
  
## <a name="remarks"></a>Notes  
 S’il existe des erreurs de mise à jour, ils seront bloqués dans une routine de gestion des erreurs. Filtrer le jeu d’enregistrements avec la constante adFilterConflictingRecords afin que seules les lignes en conflit sont visibles. Dans cet exemple, la stratégie de résolution des erreurs consiste tout simplement pour imprimer l’auteur des noms et prénoms (au_fname et au_lname).  
  
 Le code pour avertir l’utilisateur pour le conflit de mise à jour ressemble à ceci :  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Mode batch](../../../ado/guide/data/batch-mode.md)
