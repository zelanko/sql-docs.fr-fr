---
title: allow updates (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: configure-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
caps.latest.revision: 32
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f874caf6697a12e7988a9ae3a2ead4be13a97aa1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="allow-updates-server-configuration-option"></a>allow updates (option de configuration de serveur)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Cette option est toujours présente dans la procédure stockée **sp_configure** , bien que ses fonctionnalités ne soient pas disponibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le paramètre n'a aucun effet. Les mises à jour directes des tables système ne sont pas prises en charge.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 La modification de l'option **allow updates** provoquera l'échec de l'instruction RECONFIGURE. Les modifications de l'option **allow updates** doivent être supprimées de tous les scripts.  
  
## <a name="see-also"></a> Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
