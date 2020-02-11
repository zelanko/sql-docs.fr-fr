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
ms.openlocfilehash: 3952ef502bf79d6704cbaea80b9a825a3c70981b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925015"
---
# <a name="immediate-mode"></a>Mode immédiat
Le mode immédiat est activé lorsque la propriété **LockType** est définie sur **adLockOptimistic** ou **adLockPessimistic**. En mode immédiat, les modifications apportées à un enregistrement sont propagées à la source de données dès que vous déclarez le travail sur une ligne terminée en appelant la méthode **Update** .  
  
## <a name="calling-update"></a>Appel de Update  
 Si vous effectuez un déplacement à partir de l’enregistrement que vous ajoutez ou modifiez avant d’appeler la méthode **Update** , ADO appellera automatiquement **Update** pour enregistrer les modifications. Vous devez appeler la méthode **CancelUpdate** avant la navigation si vous voulez annuler les modifications apportées à l’enregistrement actuel ou ignorer un enregistrement qui vient d’être ajouté.  
  
 L’enregistrement actif reste actif après l’appel de la méthode **Update** .  
  
## <a name="cancelupdate"></a>CancelUpdate  
 Utilisez la méthode **CancelUpdate** pour annuler les modifications apportées à la ligne actuelle ou pour ignorer une ligne qui vient d’être ajoutée. Vous ne pouvez pas annuler les modifications apportées à la ligne actuelle ou à une nouvelle ligne après avoir appelé la méthode **Update** , sauf si les modifications font partie d’une transaction que vous pouvez restaurer avec la méthode **RollbackTrans** ou une mise à jour par lot. Dans le cas d’une mise à jour par lot, vous pouvez annuler la **mise à jour** avec la méthode **CancelUpdate** ou **CancelBatch** .  
  
 Si vous ajoutez une nouvelle ligne lorsque vous appelez la méthode **CancelUpdate** , la ligne active devient la ligne qui était en cours avant l’appel **AddNew** .  
  
 Si vous n’avez pas modifié la ligne actuelle ou ajouté une nouvelle ligne, l’appel de la méthode **CancelUpdate** génère une erreur.
