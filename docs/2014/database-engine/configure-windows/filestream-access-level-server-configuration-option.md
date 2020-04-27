---
title: filestream access level (option de configuration de serveur) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 90b4ec97a3ab31c93e92219b96724b75d7f86425
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62782254"
---
# <a name="filestream-access-level-server-configuration-option"></a>filestream access level (option de configuration de serveur)
  Utilisez l'option de configuration filestream_access_level pour modifier le niveau d'accès FILESTREAM pour cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Pour que cette option ait un effet, les paramètres d'administration Windows pour FILESTREAM doivent être activés. Vous pouvez activer ces paramètres lorsque vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Valeur|Définition|  
|-----------|----------------|  
|0|Désactive la prise en charge FILESTREAM pour cette instance.|  
|1|Active FILESTREAM pour l'accès [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|2|Active FILESTREAM pour l'accès [!INCLUDE[tsql](../../includes/tsql-md.md)] et l'accès en continu Win32.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration du moteur de base de données - Filestream](../../sql-server/install/database-engine-configuration-filestream.md)   
 [Activer et configurer FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
  
