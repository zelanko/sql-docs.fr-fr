---
title: open objects (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- open objects option
ms.assetid: c8424d3c-86ba-4cc5-bf0c-be4ce44bdd04
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 526a196c280e4a8b62db27be4c8644315379b2d3
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "67997944"
---
# <a name="open-objects-server-configuration-option"></a>open objects (option de configuration de serveur)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Cette option est toujours présente dans **sp_configure**, même si ses fonctionnalités ont été désactivées dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. (La valeur n'a pas d'effet.) Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le nombre d'objets de base de données ouverts est géré dynamiquement et n'est limité que par la mémoire disponible. L’option **open objects** est disponible dans **sp_configure** pour assurer une compatibilité descendante avec les scripts existants.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
