---
title: filestream access level (option de configuration de serveur) | Microsoft Docs
description: Familiarisez-vous avec l’option « filestream_access_level ». Découvrez comment elle modifie le niveau d’accès FILESTREAM pour une instance de SQL Server.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 04205ee05e3c26cc807a3a6aa828152c20e4c3c7
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91670952"
---
# <a name="filestream-access-level-server-configuration-option"></a>filestream access level (option de configuration de serveur)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Utilisez l'option de configuration filestream_access_level pour modifier le niveau d'accès FILESTREAM pour cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Pour que cette option ait un effet, les paramètres d'administration Windows pour FILESTREAM doivent être activés. Vous pouvez activer ces paramètres lorsque vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Valeur|Définition|  
|-----------|----------------|  
|0|Désactive la prise en charge FILESTREAM pour cette instance.|  
|1|Active FILESTREAM pour l'accès [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|2|Active FILESTREAM pour l'accès [!INCLUDE[tsql](../../includes/tsql-md.md)] et l'accès en continu Win32.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration du moteur de base de données - Filestream](../install-windows/install-sql-server.md)   
 [Activer et configurer FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
