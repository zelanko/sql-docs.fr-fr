---
title: allow updates (option de configuration de serveur) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4cbf1454658cc74e2b4bd1c6bf44acdd7c2b25ad
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="allow-updates-server-configuration-option"></a>allow updates (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette option est toujours présente dans la procédure stockée **sp_configure** , bien que ses fonctionnalités ne soient pas disponibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le paramètre n'a aucun effet. Les mises à jour directes des tables système ne sont pas prises en charge.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 La modification de l'option **allow updates** provoquera l'échec de l'instruction RECONFIGURE. Les modifications de l'option **allow updates** doivent être supprimées de tous les scripts.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
