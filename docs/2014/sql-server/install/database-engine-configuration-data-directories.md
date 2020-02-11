---
title: Configuration de la Moteur de base de données-répertoires de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 9b1fa0fc-623b-479a-afc3-4f13bd850487
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bfb62ec0bbd16a2b77e2f05f64d36ef31498a100
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66095898"
---
# <a name="database-engine-configuration---data-directories"></a>Configuration du moteur de base de données – Répertoires de données
  Cette page vous permet de spécifier l’emplacement d’installation pour les fichiers programme et les fichiers de données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Selon le type d'installation, le stockage pris en charge peut inclure un disque local, un stockage partagé ou un serveur de fichiers SMB.  
  
 Pour spécifier un partage de fichiers SMB comme répertoire, vous devez taper manuellement le chemin d'accès UNC pris en charge. La navigation vers un partage de fichiers SMB n'est pas prise en charge. Vous trouverez ci-dessous un format de chemin UNC pris en charge d’un partage de fichiers SMB : \\\NomServeur\NomPartage\\….  
  
## <a name="stand-alone-instance-of-includessnoversionincludesssnoversion-mdmd"></a>Instance autonome de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Le tableau suivant répertorie les types de stockage pris en charge et les répertoires par défaut pour une instance autonome de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont configurables par l'utilisateur pendant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
  
|Description|Type de stockage pris en charge|Annuaire par défaut|Recommandations|  
|-----------------|----------------------------|-----------------------|---------------------|  
|Répertoire de données racine|Disque local, serveur de fichiers SMB, stockage partagé <sup>1</sup>|C:\Program\\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Files\| Setup configure les listes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de contrôle d’accès pour les répertoires et interrompt l’héritage dans le cadre de la configuration.[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Répertoire de base de données utilisateur|Disque local, serveur de fichiers SMB, stockage partagé <sup>1</sup>|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12. \<InstanceId> \MSSQL\DATA|Les meilleures pratiques recommandées pour les répertoires de données utilisateur dépendent de la charge de travail et des exigences en matière de performances.|  
|Répertoire du journal de la base de données utilisateur|Disque local, serveur de fichiers SMB, stockage partagé <sup>1</sup>|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12. \<InstanceId> \MSSQL\DATA|Assurez-vous que le répertoire du journal a un espace adéquat.|  
|Répertoire Temp de base de données|Disque local, serveur de fichiers SMB, stockage partagé <sup>1</sup>|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12. \<InstanceId> \MSSQL\DATA|Les meilleures pratiques recommandées pour le répertoire Temp dépendent de la charge de travail et des exigences en matière de performances.|  
|Répertoire Temp du journal de base de données|Disque local, serveur de fichiers SMB, stockage partagé <sup>1</sup>|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12. \<InstanceId> \MSSQL\DATA|Assurez-vous que le répertoire du journal a un espace adéquat.|  
|Répertoire de sauvegarde|Disque local, serveur de fichiers SMB, stockage partagé <sup>1</sup>|C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12. \<InstanceId> \mssql\backup|Définissez les autorisations appropriées pour empêcher la perte de données et vérifiez que le compte d'utilisateur pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a les autorisations adéquates pour écrire dans le répertoire de sauvegarde. L'utilisation d'un lecteur mappé pour les répertoires de sauvegarde n'est pas prise en charge.|  
  
 <sup>1</sup> bien que les disques partagés soient pris en charge, il n’est pas recommandé pour une instance autonome [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de.  
  
## <a name="failover-cluster-instance-of-includessnoversionincludesssnoversion-mdmd"></a>Instance de cluster de basculement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Le tableau suivant répertorie les types de stockage pris en charge et les répertoires par défaut pour une instance de cluster de basculement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont configurables par l'utilisateur pendant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Description|Type de stockage pris en charge|Répertoire par défaut|Recommandations|  
|-----------------|----------------------------|-----------------------|---------------------|  
|Répertoire de données racine|Stockage partagé, serveur de fichiers SMB|
  \<Lecteur:>\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\<br /><br /> Conseil : si le disque partagé a été sélectionné à la page **Sélection du disque du cluster** , la valeur par défaut est le premier disque partagé. La valeur par défaut de ce champ est vide si aucune sélection n'a été effectuée à la page **Sélection du disque du cluster** .|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Le programme d’installation configure les ACL pour les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] répertoires et interrompt l’héritage dans le cadre de la configuration.|  
|Répertoire de base de données utilisateur|Stockage partagé, serveur de fichiers SMB|\<Lecteur : >Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12. \<InstanceId> \MSSQL\DATA<br /><br /> Conseil : si le disque partagé a été sélectionné à la page **Sélection du disque du cluster** , la valeur par défaut est le premier disque partagé. La valeur par défaut de ce champ est vide si aucune sélection n'a été effectuée à la page **Sélection du disque du cluster** .|Les meilleures pratiques recommandées pour les répertoires de données utilisateur dépendent de la charge de travail et des exigences en matière de performances.|  
|Répertoire du journal de la base de données utilisateur|Stockage partagé, serveur de fichiers SMB|\<Lecteur : > \Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12. \<InstanceId> \MSSQL\DATA<br /><br /> Conseil : si le disque partagé a été sélectionné à la page **Sélection du disque du cluster** , la valeur par défaut est le premier disque partagé. La valeur par défaut de ce champ est vide si aucune sélection n'a été effectuée à la page **Sélection du disque du cluster** .|Assurez-vous que le répertoire du journal a un espace adéquat.|  
|Répertoire Temp de base de données|Disque local, stockage partagé, serveur de fichiers SMB|\<Lecteur : > \Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12. \<InstanceId> \MSSQL\DATA<br /><br /> Conseil : si le disque partagé a été sélectionné à la page **Sélection du disque du cluster** , la valeur par défaut est le premier disque partagé. La valeur par défaut de ce champ est vide si aucune sélection n'a été effectuée à la page **Sélection du disque du cluster** .|Assurez-vous que le répertoire spécifié est valide pour tous les nœuds du cluster. Pendant le basculement, si les répertoires tempdb ne sont pas disponibles sur le nœud de basculement cible, la ressource [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sera pas en ligne.|  
|Répertoire Temp du journal de base de données|Disque local, stockage partagé, serveur de fichiers SMB|\<Lecteur : > \Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12. \<InstanceId> \MSSQL\DATA<br /><br /> Conseil : si le disque partagé a été sélectionné à la page **Sélection du disque du cluster** , la valeur par défaut est le premier disque partagé. La valeur par défaut de ce champ est vide si aucune sélection n'a été effectuée à la page **Sélection du disque du cluster** .|Assurez-vous que le répertoire spécifié est valide pour tous les nœuds du cluster. Pendant le basculement, si les répertoires tempdb ne sont pas disponibles sur le nœud de basculement cible, la ressource [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sera pas en ligne.|  
|Répertoire de sauvegarde|Disque local, stockage partagé, serveur de fichiers SMB|\<Lecteur : > \Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12. \<InstanceId> \mssql\backup<br /><br /> Conseil : si le disque partagé a été sélectionné à la page **Sélection du disque du cluster** , la valeur par défaut est le premier disque partagé. La valeur par défaut de ce champ est vide si aucune sélection n'a été effectuée à la page **Sélection du disque du cluster** .|Définissez les autorisations appropriées pour empêcher la perte de données et vérifiez que le compte d'utilisateur pour le service SQL Server a les autorisations adéquates pour écrire dans le répertoire de sauvegarde. L'utilisation d'un lecteur mappé pour les répertoires de sauvegarde n'est pas prise en charge.|  
  
## <a name="security-considerations"></a>Considérations relatives à la sécurité  
 Le programme d'installation configurera les listes de contrôle d'accès pour les répertoires [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et rompra l'héritage dans le cadre de la configuration.  
  
 Les recommandations suivantes s'appliquent au serveur de fichiers SMB :  
  
-   Le compte de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être un compte de domaine si un serveur de fichiers SMB est utilisé.  
  
-   Le compte utilisé pour installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit avoir des autorisations FULL CONTROL NTFS sur le dossier de partage de fichiers SMB utilisé comme répertoire de données.  
  
-   Des privilèges SeSecurityPrivilege sur le serveur de fichiers SMB doivent être accordés au compte utilisé pour installer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour accorder ce privilège, utilisez la console de stratégie de sécurité locale sur le serveur de fichiers pour ajouter le compte utilisé pour l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à la stratégie **Gérer le journal d'audit et de la sécurité** . Ce paramètre est disponible dans la section **Attribution des droits utilisateur** sous **Stratégies locales** dans la console **Stratégie de sécurité locale** .  
  
## <a name="notes"></a>Notes  
  
-   Lors de l'ajout de fonctionnalités à une installation existante, vous ne pouvez ni modifier l'emplacement d'une fonctionnalité précédemment installée, ni spécifier l'emplacement d'une nouvelle fonctionnalité.  
  
-   Si vous spécifiez des répertoires d'installation autres que les répertoires par défaut, assurez-vous que les dossiers d'installation sont uniques à cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Aucun des répertoires dans cette boîte de dialogue ne doit être partagé avec des répertoires d'autres instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les composants [!INCLUDE[ssDE](../../includes/ssde-md.md)] et [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] d'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doivent également être installés dans des répertoires distincts.  
  
-   Les fichiers programmes et les fichiers de données ne peuvent pas être installés aux emplacements suivants :  
  
    -   sur un lecteur de disque amovible ;  
  
    -   dans un système de fichiers utilisant la compression ;  
  
    -   dans un répertoire où figurent des fichiers système ;  
  
    -   sur un lecteur réseau mappé sur une instance de cluster de basculement.  
  
## <a name="see-also"></a>Voir aussi  
 [Emplacements des fichiers pour les instances par défaut et nommées de SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)   
 [Partager des autorisations NTFS sur un serveur de fichiers](https://go.microsoft.com/fwlink/?LinkID=206571)  
  
  
