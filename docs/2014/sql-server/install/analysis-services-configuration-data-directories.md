---
title: Configuration de la Analysis Services-répertoires de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ef732855-b7af-4f40-a619-5573c1c354bb
author: heidisteen
ms.author: heidist
ms.openlocfilehash: b31000d7d044a781b38faa7c366c8f8f6a439399
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85045589"
---
# <a name="analysis-services-configuration---data-directories"></a>Configuration de Analysis Services – Répertoires de données
  Les répertoires par défaut indiqués dans le tableau suivant sont configurables par l'utilisateur pendant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L’autorisation d’accéder à ces fichiers est accordée aux administrateurs locaux et aux membres du groupe de sécurité SQLServerMSASUser $ \<instance> qui est créé et approvisionné lors de l’installation.  
  
## <a name="ui-element-list"></a>Liste des éléments d’interface utilisateur  
  
|Description|Répertoire par défaut|Recommandations|  
|-----------------|-----------------------|---------------------|  
|Répertoire de données racine|C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID> \OLAP\Data \| Assurez-vous que le dossier \Program files\Microsoft SQL Server \ est protégé avec des autorisations limitées. Le fonctionnement de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dépend, dans de nombreuses configurations, de la performance de l'emplacement de stockage sur lequel le répertoire de données se trouve. Placez ce répertoire sur l'emplacement de stockage le plus performant raccordé au système. Pour les installations de cluster de basculement, vérifiez que les répertoires de données sont placés sur le disque partagé.|  
|Répertoire de fichiers journaux|C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID> \OLAP\Log \| il s’agit du répertoire pour les [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fichiers journaux et il comprend le journal FlightRecorder. Si vous augmentez la durée de la boîte noire, assurez-vous que le répertoire de journal dispose de l'espace adéquat.|  
|Répertoire Temp|C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID> \OLAP\Temp \| Placez le répertoire Temp sur le sous-système de stockage hautes performances.|  
|Répertoire de sauvegarde|C:\Program Files\Microsoft SQL Server\MSAS12. \<InstanceID> \OLAP\Backup \| il s’agit du répertoire pour les [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fichiers de sauvegarde par défaut. Pour les installations de PowerPivot pour SharePoint, il s'agit également de l'emplacement où les services système PowerPivot mettent en cache les fichiers de données PowerPivot.<br /><br /> Vérifiez que des autorisations appropriées sont définies pour empêcher la perte de données et vérifiez que le groupe d'utilisateurs pour le service [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] a les autorisations adéquates pour écrire dans le répertoire de sauvegarde. L'utilisation d'un lecteur mappé pour les répertoires de sauvegarde n'est pas prise en charge.|  
  
## <a name="notes"></a>Notes  
  
-   Les instances d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] déployées sur une batterie de serveurs SharePoint stockent des fichiers d'application, des fichiers de données et des propriétés dans les bases de données de contenu et les bases de données d'application de service.  
  
-   Lors de l'ajout de fonctionnalités à une installation existante, vous ne pouvez ni modifier l'emplacement d'une fonctionnalité précédemment installée, ni spécifier l'emplacement d'une nouvelle fonctionnalité.  
  
-   Si vous spécifiez des répertoires d'installation autres que les répertoires par défaut, assurez-vous que les dossiers d'installation sont uniques à cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Aucun des répertoires dans cette boîte de dialogue ne doit être partagé avec des répertoires d'autres instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les composants [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent également être installés dans des répertoires distincts.  
  
-   Les fichiers programmes et les fichiers de données ne peuvent pas être installés aux emplacements suivants :  
  
    -   sur un lecteur de disque amovible ;  
  
    -   dans un système de fichiers utilisant la compression ;  
  
    -   dans un répertoire où figurent des fichiers système ;  
  
## <a name="see-also"></a>Voir aussi  
 [Emplacements des fichiers pour les instances par défaut et les instances nommées de SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)  
  
  
