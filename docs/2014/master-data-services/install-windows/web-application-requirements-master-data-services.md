---
title: Configuration requise pour l’application web (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9455d3cf-c1b7-4d48-8aff-7dc636ed5dc3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 15b394c836cb24229944f4e0775dfccad847a32b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65482885"
---
# <a name="web-application-requirements-master-data-services"></a>Configuration requise pour l'application Web (Master Data Services)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] est une application web hébergée par IIS (Internet Information Services). [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] fonctionne uniquement dans Internet Explorer 7 ou version ultérieure. Internet Explorer 7 et versions antérieures, Microsoft Edge et Chrome ne sont pas pris en charge.  
  
 Utilisez [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] pour créer et configurer l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] configure IIS sur l'ordinateur local, il est dont le mieux adapté aux tâches de configuration Web initiales. Par exemple, configurez un environnement [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] avec une application web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] unique, ou configurez la première application web dans un déploiement par montée en puissance parallèle de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Utilisez les outils IIS pour effectuer des tâches plus complexes, telles que la configuration de plusieurs serveurs Web dans un déploiement avec montée en puissance parallèle.  
  
> [!NOTE]  
>  Tout ordinateur sur lequel vous installez les composants de [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] doit disposer d'une licence. Pour plus d'informations, reportez-vous au Contrat de Licence Utilisateur Final (CLUF).  
  
## <a name="requirements"></a>Configuration requise  
  
### <a name="operating-system"></a>Système d'exploitation  
 Les systèmes d'exploitation Windows suivants incluent les fonctionnalités des services Internet (IIS) requises pour l'application Web [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] et le service Web.  
  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Developer (64 bits) x64|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Entreprise (64 bits) x64|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Business Intelligence (64 bits) x64|  
|-------------------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------|  
|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2<br /><br /> Windows Server 2008 R2 SP1<br /><br /> Windows 7 Professionnel, Entreprise et Édition Intégrale<br /><br /> Windows 8.0 Professionnel, Entreprise et Édition Intégrale|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2<br /><br /> Windows Server 2008 R2 SP1<br /><br /> Windows Server 2012|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2<br /><br /> Windows Server 2008 R2 SP1<br /><br /> Windows Server 2012|  
  
 Pour obtenir une liste complète des systèmes d’exploitation Windows pris en charge pour votre édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
### <a name="microsoft-silverlight"></a>Microsoft Silverlight  
 Pour travailler dans l'application Web de [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , Silverlight 5 doit être installé sur l'ordinateur client. Si vous n'avez pas la version requise de Silverlight, vous êtes invité à l'installer lorsque vous accédez à une partie de l'application Web qui l'utilise. Vous pouvez installer Silverlight 5 à partir de [cet emplacement](https://go.microsoft.com/fwlink/?LinkId=243096).  
  
### <a name="role-and-role-services-windows-server-2008-or-windows-server-2008-r2-windows-7-operating-systems"></a>Rôle et services de rôle (systèmes d'exploitation Windows Server 2008 ou Windows Server 2008 R2, Windows 7)  
 Sur Windows Server 2008 R2, vous pouvez utiliser le **Gestionnaire de serveur**, disponible dans Microsoft Management Console (MMC), pour installer le rôle **Serveur Web (IIS)** et les services de rôle requis suivants :  
  
> [!NOTE]  
>  Sur les systèmes d'exploitation [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] et Windows 7, utilisez **Programmes et fonctionnalités** dans le Panneau de configuration pour activer ces options dans la boîte de dialogue **Fonctionnalités de Windows** .  
  
||  
|-|  
|Serveur Web<br /><br /> Fonctionnalités HTTP communes<br /><br /> Contenu statique<br /><br /> Document par défaut<br /><br /> Exploration de répertoire<br /><br /> Erreurs HTTP<br /><br /> Développement d'applications<br /><br /> ASP.NET<br /><br /> Extensibilité .NET<br /><br /> Extensions ISAPI<br /><br /> Filtres ISAPI<br /><br /> Intégrité et diagnostics<br /><br /> Journalisation HTTP<br /><br /> Observateur de demandes<br /><br /> Sécurité<br /><br /> Authentification Windows<br /><br /> Filtrage des demandes<br /><br /> Performance<br /><br /> Compression du contenu statique<br /><br /> Outils de gestion<br /><br /> Console de gestion IIS|  
  
### <a name="role-and-role-services-windows-server-2012-or-windows-8-operating-systems"></a>Rôle et services de rôle (systèmes d'exploitation Windows Server 2012 ou Windows 8)  
 Sur Windows Server 2012, vous pouvez utiliser le **Gestionnaire de serveur**, disponible dans Microsoft Management Console (MMC), pour installer le rôle **Serveur Web (IIS)** et les services de rôle requis suivants :  
  
> [!NOTE]  
>  Sur le système d'exploitation Windows 8, utilisez **Programmes et fonctionnalités** dans le Panneau de configuration pour activer ces options dans la boîte de dialogue **Fonctionnalités de Windows** .  
  
||  
|-|  
|Services Internet (IIS)<br /><br /> Outils de gestion Web<br /><br /> Console de gestion IIS<br /><br /> Services World Wide Web<br /><br /> Développement d'applications<br /><br /> Extensibilité .NET 3.5<br /><br /> Extensibilité .NET 4.5<br /><br /> ASP.NET 3.5<br /><br /> ASP.NET 4.5<br /><br /> Extensions ISAPI<br /><br /> Filtres ISAPI<br /><br /> Fonctionnalités HTTP communes<br /><br /> Document par défaut<br /><br /> Exploration de répertoire<br /><br /> Erreurs HTTP<br /><br /> Contenu statique<br /><br /> [Remarque : N’installez pas publication WebDAV]<br /><br /> Intégrité et diagnostics<br /><br /> Journalisation HTTP<br /><br /> Observateur de demandes<br /><br /> Performances<br /><br /> Compression du contenu statique<br /><br /> Sécurité<br /><br /> Filtrage des demandes<br /><br /> Authentification Windows|  
  
### <a name="features-windows-server-2008-or-windows-server-2008-r2-windows-7-operating-systems"></a>Fonctionnalités (systèmes d'exploitation Windows Server 2008 ou Windows Server 2008 R2, Windows 7)  
 Sur [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] ou Windows Server 2008 R2, vous pouvez utiliser le **Gestionnaire de serveur** pour installer les fonctionnalités requises suivantes :  
  
> [!NOTE]  
>  Sur les systèmes d'exploitation [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] et Windows 7, utilisez **Programmes et fonctionnalités** dans le Panneau de configuration pour activer ces options dans la boîte de dialogue **Fonctionnalités de Windows** .  
  
||  
|-|  
|Fonctionnalités .NET Framework 3.0<br /><br /> Activation de Windows Communication Foundation<br /><br /> Activation HTTP<br /><br /> Activation non-HTTP<br /><br /> Service d’activation des processus Windows<br /><br /> Modèle de processus<br /><br /> Environnement .NET<br /><br /> API de configuration|  
  
### <a name="features-windows-server-2012-or-windows-8-operating-systems"></a>Fonctionnalités (systèmes d'exploitation Windows Server 2012 ou Windows 8)  
 Sur Windows Server 2012, vous pouvez utiliser le **Gestionnaire de serveur** pour installer les fonctionnalités requises suivantes :  
  
> [!NOTE]  
>  Sur le système d'exploitation Windows 8, utilisez **Programmes et fonctionnalités** dans le Panneau de configuration pour activer ces options dans la boîte de dialogue **Fonctionnalités de Windows** .  
  
||  
|-|  
|.NET Framework 3.5 (inclut .NET 2.0 et 3.0)<br /><br /> .NET Framework 4.5 Advanced Services<br /><br /> ASP.NET 4.5<br /><br /> Services WCF<br /><br /> Activation HTTP [Remarque : Cela est nécessaire.]<br /><br /> Partage de ports TCP<br /><br /> Service d’activation des processus Windows<br /><br /> Modèle de processus<br /><br /> Environnement .NET<br /><br /> API de configuration|  
  
### <a name="accounts-and-permissions"></a>Comptes et autorisations  
  
|type|Description|  
|----------|-----------------|  
|Compte Windows|Vous devez ouvrir une session sur l'ordinateur serveur Web avec un compte Windows qui a l'autorisation de configurer des rôles, des services de rôle et des fonctionnalités Windows, et créer et gérer des pools d'applications, des sites Web et des applications Web dans IIS sur l'ordinateur local.|  
|Compte de service|Lorsque vous créez l'application Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] dans [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], vous devez spécifier une identité pour le pool d'applications dans lequel elle s'exécute. Ce compte peut être différent du compte de service spécifié lors de la création de la base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .<br /><br /> Cette identité doit être un compte d'utilisateur de domaine et est ajoutée au rôle de base de données mds_exec dans la base de données [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] pour l'accès aux bases de données. Pour plus d’informations, consultez [Connexions, utilisateurs et rôles de base de données &#40;Master Data Services&#41;](../database-logins-users-and-roles-master-data-services.md). Ce compte est également ajouté à un groupe Windows [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], **MDS_ServiceAccounts**, qui est autorisé à accéder au répertoire de compilation temporaire, **MDSTempDir**, dans le système de fichiers. Pour plus d’informations, consultez [Autorisations d’accès aux dossiers et aux fichiers &#40;Master Data Services&#41;](../folder-and-file-permissions-master-data-services.md).<br /><br /> Le compte du pool d'applications a besoin de l'autorisation VIEW SERVER STATE pour éviter les erreurs de serveur. Par exemple, la commande MDS Validate Version échoue avec une erreur de serveur. Pour plus d'informations, consultez [Échec de la commande MDS Validate Version avec une erreur de serveur dans SQL Server 2012 et SQL Server 2014](https://go.microsoft.com/fwlink/p/?LinkId=526304)|  
  
## <a name="see-also"></a>Voir aussi  
 [Installer Master Data Services](install-master-data-services.md)   
 [Créer une application web Master Data Manager &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md)   
 [Page Configuration web &#40;Gestionnaire de configuration de Master Data Services&#41;](../web-configuration-page-master-data-services-configuration-manager.md)  
  
  
