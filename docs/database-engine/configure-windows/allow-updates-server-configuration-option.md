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
manager: jroth
ms.openlocfilehash: 2be9a6eb16bf2b4f481faf6409b28da11eb39eb5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799567"
---
# <a name="allow-updates-server-configuration-option"></a>allow updates (option de configuration de serveur)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Cette option est toujours présente dans la procédure stockée **sp_configure** , bien que ses fonctionnalités ne soient pas disponibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le paramètre n'a aucun effet. Les mises à jour directes des tables système ne sont pas prises en charge.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 La modification de l'option **allow updates** provoquera l'échec de l'instruction RECONFIGURE. Les modifications de l'option **allow updates** doivent être supprimées de tous les scripts.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
