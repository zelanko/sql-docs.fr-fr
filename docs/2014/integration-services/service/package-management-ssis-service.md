---
title: Gestion de packages (Service SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, managing
- packages [Integration Services], managing
- Integration Services packages, managing
- storing packages
- Stored Packages folder
- current packages
- Running Packages folder
- status information [Integration Services]
- SSIS packages, managing
- storage [Integration Services]
- monitoring [Integration Services], packages
- Integration Services service, package management
- services [Integration Services], package management
ms.assetid: 0261ed9e-3b01-4e37-a9d4-d039c41029b6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 89e925d72b4ca4815c05e9f4ab67211a1a7ea980
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62766625"
---
# <a name="package-management-ssis-service"></a>Gestion de packages (Service SSIS)
  La gestion des packages implique des actions incluant les tâches suivantes :  
  
-   Surveillance des packages en cours d'exécution  
  
-   Gestion du stockage des packages  
  
-   Importation et exportation de packages  
  
> [!IMPORTANT]  
>  Cette rubrique présente le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , un service Windows qui permet de gérer les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]prend en charge le service pour la compatibilité descendante [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]avec les versions antérieures de. À compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], vous pouvez gérer des objets tels que des packages sur le serveur Integration Services.  
  
## <a name="package-store"></a>Magasin de packages  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]fournit deux dossiers de niveau supérieur pour l’accès [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] aux packages : **exécution** des packages et des **packages stockés**. Le dossier **Exécution des packages** répertorie les packages en cours d'exécution sur le serveur. Le dossier **Packages stockés** répertorie les packages enregistrés dans le magasin de packages. Ce sont les seuls packages gérés par le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Le magasin de packages peut comprendre la base de données msdb et/ou les dossiers du système de fichiers répertoriés dans le fichier de configuration du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Le fichier de configuration indique la base de données msdb et les dossiers du système de fichiers à gérer. Il est possible que vous disposiez également de packages stockés ailleurs dans le système de fichiers qui ne sont pas gérés par le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Les packages que vous enregistrez dans la base de données msdb sont stockés dans une table nommée sysssispackages. Lorsque vous enregistrez des packages dans la base de données msdb, vous pouvez également les regrouper dans des dossiers logiques. L’usage de dossiers logiques vous permet d’organiser les packages selon leur fonction ou bien de les filtrer dans la table sysssispackages. Vous pouvez créer de nouveaux dossiers logiques à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Par défaut, tous les dossiers logiques que vous ajoutez à la base de données msdb sont inclus automatiquement dans le magasin de packages.  
  
 Les dossiers logiques que vous créez dans le but de regrouper les packages de la base de données msdb sont représentés par des lignes dans la table sysssispackagefolders de la base de données msdb. Les colonnes folderid et parentfolderid de sysssispackagefolders définissent l’arborescence des dossiers. Les dossiers logiques racines de la base de données msdb correspondent aux lignes de sysssispackagefolders dont la colonne parentfolderid comporte une valeur NULL. Pour plus d’informations, consultez [sysssispackages &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysssispackages-transact-sql) et [sysssispackagefolders &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysssispackagefolders-transact-sql).  
  
 Lorsque vous ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] puis que vous vous connectez à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], les dossiers msdb gérés par le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] apparaissent dans le dossier Packages stockés. Si le fichier de configuration spécifie des dossiers de système de fichiers racines, le dossier Packages stockés répertorie également les packages enregistrés dans le système de fichiers dans ces mêmes dossiers et dans tous les sous-dossiers.  
  
 Vous pouvez stocker des packages dans n'importe quel dossier de système de fichiers mais ces dossiers ne seront pas consignés dans la liste des sous-dossiers du dossier **Packages stockés** , à moins que vous n'ajoutiez le dossier à la liste des dossiers dans le fichier de configuration du magasin de packages. Pour plus d’informations sur le fichier de configuration, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](integration-services-service-ssis-service.md).  
  
 Le dossier **Exécution des packages** ne contient aucun sous-dossier et n'est pas extensible.  
  
 Par défaut, le dossier **Packages stockés** contient deux dossiers : **File System** et **MSDB**. Le dossier **File System** répertorie les packages enregistrés dans le système de fichiers. Le fichier de configuration du service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] indique l'emplacement de ces fichiers. Le dossier par défaut est le dossier Packages, situé dans %Program Files%\Microsoft SQL Server\100\DTS. Le dossier **MSDB** répertorie les packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] enregistrés dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb sur le serveur. La table sysssispackages contient les packages enregistrés dans la base de données msdb.  
  
 Pour visualiser la liste des packages stockés dans le magasin de packages, vous devez ouvrir [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et vous connecter à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Pour plus d’informations, consultez [Afficher les packages Integration Services dans SQL Server Management Studio &#40;Service SSIS&#41;](../view-integration-services-packages-in-sql-server-management-studio-ssis-service.md).  
  
## <a name="monitoring-running-packages"></a>Surveillance des packages en cours d'exécution  
 Le dossier **Exécution des packages** répertorie les packages en cours d'exécution. Pour afficher des informations relatives aux packages en cours d'exécution sur la page **Résumé** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez sur le dossier **Exécution des packages** . Des informations telles que la durée d'exécution des packages en cours d'exécution figurent sur la page **Résumé** . Vous pouvez également actualiser l'affichage du dossier pour obtenir les informations les plus récentes.  
  
 Pour afficher des informations sur un seul package en cours d'exécution sur la page **Résumé** , cliquez sur le package. La page **Résumé** affiche des informations telles que la version et la description du package.  
  
 Vous pouvez arrêter un package en cours d’exécution à partir du dossier **Exécution des packages** en cliquant avec le bouton droit sur le package, puis en cliquant sur **Arrêter**.  
  
## <a name="managing-package-storage"></a>Gestion du stockage des packages  
 Pour organiser les packages, vous pouvez ajouter des dossiers personnalisés aux dossiers des magasins de packages répertoriés par le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans le fichier de configuration. Par défaut, les dossiers racines sont les dossiers **File System** et **MSDB** . Par exemple, vous pouvez choisir d'ajouter au dossier **File System** un dossier **Nettoyage des données** contenant tous les packages utilisés pour nettoyer les données. Vous pouvez ajouter des dossiers personnalisés aux dossiers personnalisés et créer une hiérarchie de dossiers imbriqués répondant à vos besoins. Les dossiers personnalisés peuvent être supprimés et renommés ; cependant, vous ne pouvez pas renommer ou supprimer les dossiers racines spécifiés par le fichier de configuration. Pour mettre à jour les dossiers racines répertoriés par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vous devez mettre à jour le fichier de configuration.  
  
 Pour plus d’informations, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](../configuring-the-integration-services-service-ssis-service.md).  
  
## <a name="importing-and-exporting-packages"></a>Importation et exportation de packages  
 
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Les packages peuvent être enregistrés dans le système de fichiers ou dans la base de données msdb. Vous pouvez copier un package d'un type de stockage à un autre à l'aide de la fonctionnalité d'importation ou d'exportation fournie par [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Vous pouvez également importer un package du même type de stockage et donner un nom différent à ce package, afin de créer une copie du package. L’utilitaire d’invite de commandes **dtutil** (dtutil.exe) permet également d’importer et d’exporter des packages.  
  
 Pour plus d’informations, consultez [dtutil Utility](../dtutil-utility.md).  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Importer et exporter des packages &#40;service SSIS&#41;](../import-and-export-packages-ssis-service.md)  
  
-   [Afficher les packages de Integration Services dans SQL Server Management Studio &#40;service SSIS&#41;](../view-integration-services-packages-in-sql-server-management-studio-ssis-service.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Service Integration Services &#40;Service SSIS&#41;](integration-services-service-ssis-service.md)  
  
  
