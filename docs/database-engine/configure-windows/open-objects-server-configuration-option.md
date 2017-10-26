---
title: open objects (option de configuration de serveur) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- open objects option
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: e620443786ae337e78062abc8cf99f0a077fbd99
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="open-objects-server-configuration-option"></a>open objects (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette option est toujours présente dans **sp_configure**, bien que ses fonctionnalités aient été désactivées dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (La valeur n'a pas d'effet.) Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le nombre d'objets de base de données ouverts est géré dynamiquement et n'est limité que par la mémoire disponible. L’option **open objects** est disponible dans **sp_configure** pour assurer une compatibilité descendante avec les scripts existants.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  

