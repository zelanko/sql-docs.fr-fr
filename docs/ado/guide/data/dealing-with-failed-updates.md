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
manager: jroth
ms.openlocfilehash: 97a55923043d26c0eb672d7a698d5bf9224f1187
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718740"
---
# <a name="dealing-with-failed-updates"></a>Traitement des mises à jour ayant échoué
Lorsqu’une mise à jour est terminée avec des erreurs, comment vous résolvez les erreurs varie selon la nature et la gravité des erreurs et la logique de votre application. Toutefois, si la base de données est partagée avec d’autres utilisateurs, une erreur typique est que quelqu'un d’autre modifie le champ avant de procéder. Ce type d’erreur est appelé un conflit. ADO détecte cette situation et signale une erreur.  
  
## <a name="remarks"></a>Notes  
 S’il existe des erreurs de mise à jour, ils seront bloqués dans une routine de gestion des erreurs. Filtrer le jeu d’enregistrements avec la constante adFilterConflictingRecords afin que seules les lignes en conflit sont visibles. Dans cet exemple, la stratégie de résolution des erreurs consiste tout simplement pour imprimer l’auteur des noms et prénoms (au_fname et au_lname).  
  
 Le code pour avertir l’utilisateur pour le conflit de mise à jour ressemble à ceci :  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Mode batch](../../../ado/guide/data/batch-mode.md)
