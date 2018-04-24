---
title: Vous traitez des mises à jour ayant échouées | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- updates [ADO], dealing with failed updates
ms.assetid: 299c37bd-19ff-4261-8571-b9665687e075
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a3ca859e2e8d7a4948a1fb38567500c44daff4ba
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="dealing-with-failed-updates"></a>Traitement des mises à jour ayant échouées
Lorsqu’une mise à jour est terminée avec des erreurs, la résolution des erreurs dépend de la nature et la gravité des erreurs et la logique de votre application. Toutefois, si la base de données est partagée avec d’autres utilisateurs, une erreur standard est que quelqu'un d’autre modifie le champ avant de procéder. Ce type d’erreur est appelé un conflit. ADO détecte cette situation et signale une erreur.  
  
## <a name="remarks"></a>Notes  
 S’il existe des erreurs de mise à jour, ils seront bloqués dans une routine de gestion des erreurs. Filtrer le jeu d’enregistrements avec la constante adFilterConflictingRecords afin que seules les lignes en conflit sont visibles. Dans cet exemple, la stratégie de résolution de l’erreur est simplement pour imprimer l’auteur prénom et nom (au_fname et au_lname).  
  
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
