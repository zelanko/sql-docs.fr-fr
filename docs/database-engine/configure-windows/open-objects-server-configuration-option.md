---
title: open objects (option de configuration de serveur) | Microsoft Docs
description: Apprenez-en plus sur l’option de configuration désactivée « open objects ». Découvrez comment SQL Server gère maintenant le nombre d’objets de base de données ouverts.
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0bbcb11a80f06eae10e5481c965e9216cc84695e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773622"
---
# <a name="open-objects-server-configuration-option"></a>open objects (option de configuration de serveur)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Cette option est toujours présente dans **sp_configure**, même si ses fonctionnalités ont été désactivées dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. (La valeur n'a pas d'effet.) Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le nombre d'objets de base de données ouverts est géré dynamiquement et n'est limité que par la mémoire disponible. L’option **open objects** est disponible dans **sp_configure** pour assurer une compatibilité descendante avec les scripts existants.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
