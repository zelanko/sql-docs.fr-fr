---
title: allow updates (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- allow updates option
ms.assetid: 3967c3ed-280a-4de8-a2ce-393e82745a7b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3cccccebcbbd9054752aa8aa4e65f3f2bc17b342
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68013149"
---
# <a name="allow-updates-server-configuration-option"></a>allow updates (option de configuration de serveur)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Cette option est toujours présente dans la procédure stockée **sp_configure** , bien que ses fonctionnalités ne soient pas disponibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le paramètre n'a aucun effet. Les mises à jour directes des tables système ne sont pas prises en charge.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 La modification de l'option **allow updates** provoquera l'échec de l'instruction RECONFIGURE. Les modifications de l'option **allow updates** doivent être supprimées de tous les scripts.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
