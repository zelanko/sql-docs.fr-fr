---
title: Déchargement d’une DLL de procédure stockée étendue | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2772c8d6470f9ad6eb5e8b7cadb6dedd136bd48b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63137584"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Déchargement d'une DLL de procédure stockée étendue
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] charge une dll de procédure stockée étendue dès qu’un appel est effectué à l’une des fonctions de la dll. La DLL reste chargée jusqu'à ce que le serveur soit arrêté ou jusqu'à ce que l'administrateur système utilise l'instruction DBCC pour la décharger. Par exemple, cette commande décharge le fichier **xp_hello. dll**, ce qui permet à l’administrateur système de copier une version plus récente de ce fichier dans le répertoire sans arrêter le serveur :  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DBCC DllName &#40;FREE&#41; &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
