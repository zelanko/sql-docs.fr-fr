---
title: "Déchargement d’une étendue de la DLL de procédure stockée | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
caps.latest.revision: "33"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 039646f41ae952d21cca7047b0942aa8bcf10860
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Déchargement d'une DLL de procédure stockée étendue
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] charge une DLL de procédure stockée étendue dès qu’un appel est fait à une des fonctions de la DLL. La DLL reste chargée jusqu'à ce que le serveur soit arrêté ou jusqu'à ce que l'administrateur système utilise l'instruction DBCC pour la décharger. Par exemple, cette commande décharge le **xp_hello.dll**, permettant à l’administrateur système copier une version plus récente de ce fichier dans le répertoire sans arrêter le serveur :  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DBCC dllname &#40; LIBRE &#41; &#40; Transact-SQL &#41;](../../t-sql/database-console-commands/dbcc-dllname-free-transact-sql.md)  
  
  
