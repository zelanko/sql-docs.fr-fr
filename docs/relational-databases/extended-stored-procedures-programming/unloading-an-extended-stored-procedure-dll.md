---
title: Déchargement d’une DLL de procédure stockée étendue | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
ms.openlocfilehash: 159be22fcaba28183c8b6cc5089906c19bf2b765
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68064260"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Déchargement d'une DLL de procédure stockée étendue
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez plutôt l’intégration du CLR.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] charge une dll de procédure stockée étendue dès qu’un appel est effectué à l’une des fonctions de la dll. La DLL reste chargée jusqu'à ce que le serveur soit arrêté ou jusqu'à ce que l'administrateur système utilise l'instruction DBCC pour la décharger. Par exemple, cette commande décharge le fichier **xp_hello. dll**, ce qui permet à l’administrateur système de copier une version plus récente de ce fichier dans le répertoire sans arrêter le serveur :  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DBCC DllName &#40;FREE&#41; &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-dllname-free-transact-sql.md)  
  
  
