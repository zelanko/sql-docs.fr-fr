---
title: "Niveau d&#39;acc&#232;s du flux de fichier (option de configuration de serveur) | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FILESTREAM [SQL Server], niveau d’accès"
  - "niveau d'accès du flux de fichier"
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# Niveau d&#39;acc&#232;s du flux de fichier (option de configuration de serveur)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilisez l'option de configuration filestream_access_level pour modifier le niveau d'accès FILESTREAM pour cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Pour que cette option ait un effet, les paramètres d'administration Windows pour FILESTREAM doivent être activés. Vous pouvez activer ces paramètres lorsque vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Valeur|Définition|  
|-----------|----------------|  
|0|Désactive la prise en charge FILESTREAM pour cette instance.|  
|1|Active FILESTREAM pour l'accès [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
|2|Active FILESTREAM pour l'accès [!INCLUDE[tsql](../../includes/tsql-md.md)] et l'accès en continu Win32.|  
  
## Voir aussi  
 [Configuration du moteur de base de données - Filestream](../Topic/Database%20Engine%20Configuration%20-%20Filestream.md)   
 [Activer et configurer FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
  