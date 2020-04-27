---
title: Fournisseur WMI pour les concepts de gestion de configuration | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management
- SQL Server WMI Provider
- configuration management [WMI]
- WMI Provider for Configuration Management, about WMI Provider for Configuration Management
ms.assetid: 7e41db24-b915-4eb8-a1d6-e6948ee915b7
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ac064258da9ae55039c350f50d153d0c60323621
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "68211621"
---
# <a name="wmi-provider-for-configuration-management-concepts"></a>Fournisseur WMI pour les concepts de gestion de configuration
  Le fournisseur WMI est une couche publiée qui est utilisée avec le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] composant logiciel enfichable Configuration Manager [!INCLUDE[msCoName](../../includes/msconame-md.md)] pour la console MMC (Management Console [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ) et le Configuration Manager. Il offre une méthode d'interface unifiée avec les appels API qui gèrent les opérations de registre requises par le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il permet également un contrôle et une manipulation avancés des services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sélectionnés.  
  
 Le fournisseur WMI [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se compose d'une DLL et d'un fichier MOF, compilés automatiquement par le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le fournisseur WMI [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contient un jeu de classes d'objets utilisé pour contrôler les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide des méthodes suivantes :  
  
-   Langage de script tel que VBScript, [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] ou Perl, dans lequel le langage WQL (Windows Query Language) peut être incorporé.  
  
-   Objet <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> d'un programme de code managé SMO.  
  
-   Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou MMC avec le composant logiciel enfichable du fournisseur WMI de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="using-a-script-language"></a>Utilisation d'un langage de script  
 Les avantages de l'utilisation d'un langage de script sont les suivants :  
  
-   Environnement de développement non obligatoire.  
  
-   Vaste disponibilité des fichiers qui prennent en charge le langage de script.  
  
 Le script peut également fonctionner avec d'autres fournisseurs WMI en plus du fournisseur WMI [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un administrateur de domaine peut utiliser un script pour installer les services, les paramètres réseau et les paramètres d'alias sur plusieurs ordinateurs d'un réseau.  
  
 Cette section traite plus en détail de l'accès au fournisseur WMI de la gestion de la configuration à partir de scripts.  
  
## <a name="using-the-smo-managedcomputer-object"></a>Utilisation de l'objet SMO ManagedComputer  
 L'objet <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> est un objet SMO managé qui fournit l'accès au fournisseur WMI de la gestion de la configuration. En utilisant un programme SMO, l'objet <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> peut être utilisé pour afficher et modifier les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les paramètres réseau et les paramètres d'alias. Pour plus d’informations, consultez [gestion des services et des paramètres réseau à l’aide du fournisseur WMI](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).  
  
## <a name="using-the-microsoft-management-console-or-sql-server-configuration-manager"></a>Utilisation de la console MMC (Microsoft Management Console) ou du Gestionnaire de configuration SQL Server  
 La console MMC fournit une interface pour gérer les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], par opposition à un langage de script ou à un programme de code managé. Le composant logiciel enfichable MMC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management peut être utilisé pour arrêter ou démarrer les services, et pour modifier les comptes de service.  
  
 Le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permet aussi de gérer les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les protocoles client et serveur, et les alias serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre le fournisseur WMI pour la gestion de la configuration](understanding-the-wmi-provider-for-configuration-management.md)   
 [Utilisation du fournisseur WMI pour la gestion de la configuration](working-with-the-wmi-provider-for-configuration-management.md)   
 [Utilisation des langages WQL et de script avec le fournisseur WMI pour la gestion de configuration](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
