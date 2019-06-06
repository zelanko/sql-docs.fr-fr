---
title: Mode immédiat | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], immediate mode
- immediate mode [ADO]
- updating data [ADO], immediate mode
ms.assetid: 31fc53d0-97de-4315-a87b-3bf5cdd1f432
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 37ad4cbc60ad4c08b65ff7f0db9b5c70245a96e3
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700582"
---
# <a name="immediate-mode"></a>Mode immédiat
Le mode immédiat est activé lorsque la **LockType** propriété est définie sur **adLockOptimistic** ou **adLockPessimistic**. Dans ce mode, les modifications apportées à un enregistrement sont propagées à la source de données dès que vous déclarez que le travail sur une ligne est terminé en appelant le **mise à jour** (méthode).  
  
## <a name="calling-update"></a>Appel de mise à jour  
 Si vous passez de l’enregistrement vous ajoutez ou modifiez avant d’appeler le **mise à jour** (méthode), ADO appelle automatiquement **mise à jour** pour enregistrer les modifications. Vous devez appeler la **CancelUpdate** méthode avant la navigation, si vous souhaitez annuler toutes les modifications apportées à l’enregistrement actif ou supprimer un enregistrement qui vient d’être ajouté.  
  
 L’enregistrement actif reste actif après avoir appelé la **mise à jour** (méthode).  
  
## <a name="cancelupdate"></a>CancelUpdate  
 Utilisez le **CancelUpdate** méthode pour annuler toutes les modifications apportées à la ligne actuelle ou ignorer une ligne ajoutée. Vous ne pouvez pas annuler les modifications apportées à la ligne actuelle ou une nouvelle ligne après avoir appelé la **mise à jour** (méthode), à moins que les modifications font partie d’une transaction que vous pouvez annuler avec la **RollbackTrans** méthode ou une partie de une mise à jour par lots. Dans le cas d’une mise à jour par lots, vous pouvez annuler la **mettre à jour** avec la **CancelUpdate** ou **CancelBatch** (méthode).  
  
 Si vous ajoutez une nouvelle ligne lorsque vous appelez le **CancelUpdate** (méthode), la ligne actuelle devient la ligne qui était actuelle avant le **AddNew** appeler.  
  
 Si vous n’avez pas modifié la ligne active ou ajouté une nouvelle ligne, l’appel la **CancelUpdate** méthode génère une erreur.
