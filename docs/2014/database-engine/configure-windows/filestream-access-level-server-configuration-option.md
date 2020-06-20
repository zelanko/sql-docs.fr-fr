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
ms.openlocfilehash: dfa43b8e6e1762e87dd9c2abbdf7a583963e196e
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935307"
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
  
  
