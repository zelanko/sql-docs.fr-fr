---
title: Sauvegarde et restauration de packages (Service SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, backup and restore
- backing up packages [Integration Services]
- packages [Integration Services], backup and restore
- SQL Server Integration Services packages, backup and restore
- restoring packages [Integration Services]
- Integration Services packages, backup and restore
ms.assetid: c67d3b83-a6c8-40de-920f-9236de4ac87f
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 586ab104ed802c0d78465d600fccd5f65e213b39
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139901"
---
# <a name="package-backup-and-restore-ssis-service"></a>Sauvegarde et restauration de packages (Service SSIS)
    
> [!IMPORTANT]  
>  Cette rubrique présente le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , un service Windows qui permet de gérer les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] prend en charge le service pour la compatibilité avec les versions antérieures de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. À compter de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], vous pouvez gérer des objets tels que des packages sur le serveur Integration Services.  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages peuvent être enregistrés dans le système de fichiers ou dans msdb, un [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] base de données système. Les packages enregistrés dans msdb peuvent être sauvegardés et restaurés à l’aide des fonctionnalités de sauvegarde et de restauration de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Pour plus d’informations sur la sauvegarde et la restauration de la base de données msdb, cliquez sur l’une des rubriques suivantes :  
  
-   [Sauvegarde et restauration des bases de données SQL Server](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
-   [Sauvegarde et restauration des bases de données système &#40;SQL Server&#41;](../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] inclut le **dtutil** utilitaire (dtutil.exec) qui vous permet de gérer les packages de ligne de commande. Pour plus d’informations, consultez [dtutil Utility](dtutil-utility.md).  
  
## <a name="configuration-files"></a>Fichiers de configuration  
 Tous les fichiers de configuration inclus dans les packages sont stockés dans le système de fichiers. Ces fichiers ne sont pas sauvegardés en même temps que la base de données msdb. Vous devez donc vérifier que les fichiers de configuration sont sauvegardés régulièrement dans le cadre de votre plan de sécurisation des packages enregistrés dans msdb. Pour inclure les configurations dans la sauvegarde de la base de données msdb, vous devez envisager d’utiliser le type de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à la place des configurations basées sur les fichiers.  
  
## <a name="packages-stored-in-the-file-system"></a>Packages stockés dans le système de fichiers  
 La sauvegarde des packages enregistrés dans le système de fichiers doit être incluse dans le plan de sauvegarde du système de fichiers du serveur. Le ficher de configuration du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , dont le nom par défaut est MsDtsSrvr.ini.xml, donne la liste des dossiers sur le serveur contrôlé par le service. Vous devez vous assurer que ces dossiers sont sauvegardés. En outre, les packages peuvent être stockés dans d'autres dossiers sur le serveur et vous devez vous assurer que ces dossiers sont inclus dans la sauvegarde.  
  
  
