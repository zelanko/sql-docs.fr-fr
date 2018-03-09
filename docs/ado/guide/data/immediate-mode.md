---
title: "Mode immédiat | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data updates [ADO], immediate mode
- immediate mode [ADO]
- updating data [ADO], immediate mode
ms.assetid: 31fc53d0-97de-4315-a87b-3bf5cdd1f432
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f737d3b05e27eff7aae0aa95ee336a054c38f29f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="immediate-mode"></a>Mode immédiat
Le mode immédiat est activé lorsque la **LockType** est définie sur **adLockOptimistic** ou **adLockPessimistic**. Dans ce mode, les modifications apportées à un enregistrement sont propagées à la source de données dès que vous déclarez que le travail sur une ligne est terminé en appelant le **mise à jour** (méthode).  
  
## <a name="calling-update"></a>Appel de mise à jour  
 Si vous passez de l’enregistrement vous ajoutez ou modifiez avant d’appeler le **mise à jour** (méthode), ADO appelle automatiquement **mise à jour** pour enregistrer les modifications. Vous devez appeler la **CancelUpdate** méthode avant de quitter si vous voulez annuler les modifications apportées à l’enregistrement actif ou supprimer un enregistrement qui vient d’être ajouté.  
  
 L’enregistrement actif reste actif après avoir appelé la **mise à jour** (méthode).  
  
## <a name="cancelupdate"></a>CancelUpdate  
 Utilisez le **CancelUpdate** méthode pour annuler les modifications apportées à la ligne actuelle ou ignorer une ligne ajoutée. Vous ne pouvez pas annuler les modifications apportées à la ligne actuelle ou une nouvelle ligne après avoir appelé la **mise à jour** (méthode), à moins que les modifications font partie d’une transaction que vous pouvez restaurer avec la **RollbackTrans** méthode ou une partie du une mise à jour par lots. Dans le cas d’une mise à jour par lots, vous pouvez annuler la **mettre à jour** avec la **CancelUpdate** ou **CancelBatch** (méthode).  
  
 Si vous ajoutez une nouvelle ligne lorsque vous appelez le **CancelUpdate** (méthode), la ligne actuelle devient la ligne qui était active avant la **AddNew** appeler.  
  
 Si vous n’avez pas modifié la ligne active ou ajouté une nouvelle ligne, l’appel du **CancelUpdate** méthode génère une erreur.
