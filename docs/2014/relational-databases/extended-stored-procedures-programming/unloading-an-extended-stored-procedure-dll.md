---
title: Déchargement d’une étendue de la DLL de procédure stockée | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 78d3e74d7316b31143253a2c1bd7c33d08b012f2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140741"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a>Déchargement d'une DLL de procédure stockée étendue
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] charge une DLL de procédure stockée étendue dès qu’un appel est fait à une des fonctions de la DLL. La DLL reste chargée jusqu'à ce que le serveur soit arrêté ou jusqu'à ce que l'administrateur système utilise l'instruction DBCC pour la décharger. Par exemple, cette commande décharge le **xp_hello.dll**, permettant à l’administrateur système copier une version plus récente de ce fichier dans le répertoire sans arrêter le serveur :  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DBCC dllname &#40;libre&#41; &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
