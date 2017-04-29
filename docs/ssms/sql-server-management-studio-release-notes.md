---
title: SQL Server Management Studio - Notes de publication | Microsoft Docs
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b95337b-80bf-4624-8f5d-cdaf6181d3b8
caps.latest.revision: 51
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 51e336a22d0c1052c48b8e569330aef26f2af094
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-management-studio----release-notes"></a>SQL Server Management Studio - Notes de publication
Bienvenue dans notre version généralement disponible de SQL Server Management Studio !  Cette version de SQL Server Management Studio (SSMS) est une installation autonome indépendante de la version de SQL Server. Nous envisageons de la mettre à jour fréquemment en ajoutant des fonctionnalités, des correctifs et la prise en charge des fonctionnalités les plus récentes dans SQL Server et Azure SQL Database.  
  
Pour installer la version la plus récente de SQL Server Management Studio, voir [Download SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md).  
  
Les problèmes et limitations constatés dans cette version de SQL Server Management Studio sont les suivants :  

1. **Un seul compte Azure Active Directory peut se connecter à une instance SSMS en utilisant l’authentification Active Directory universelle.**  
    Cette restriction est limitée à l’authentification Active Directory universelle : vous pouvez vous connecter à différents serveurs en utilisant l’authentification Active Directory par mot de passe, l’authentification Active Directory intégrée ou l’authentification SQL Server.
    
    Une solution de contournement consiste à utiliser une autre instance de SSMS pour se connecter sous un autre compte Azure Active Directory. 
    
2. **Les commandes de Data-Tier Application Framework (DACFx) et le Concepteur de schémas dans SSMS ne prennent pas en charge l’authentification Active Directory universelle.**  
    Les commandes qui utilisent DACFx (par exemple, l’importation et l’exportation) et le Concepteur de schémas dans SSMS ne prennent pas actuellement en charge l’authentification Active Directory universelle.
    
    Une solution de contournement consiste à utiliser les autres formes d’authentification fournies dans SSMS : authentification Active Directory par mot de passe, authentification Active Directory intégrée ou authentification SQL Server.

3. **SSMS peut se connecter uniquement à des instances de SQL Server Integrated Services 2016 (SSIS 2016).**  
    Il existe une limitation de compatibilité connue avec SQL Server Integration Services, qui empêche la connexion aux versions précédentes.
    
    Une solution de contournement de ce problème consiste à vous connecter à votre instance SQL Server Integration Services à l’aide de la [version de SSMS correspondant à votre instance SSIS.](../ssms/previous-sql-server-management-studio-releases.md) 
  
4. **SSMS n’enregistre pas les plans de maintenance de SQL Server 2008 R2 et versions antérieures de SQL Server.**  
    Il s’agit d’une limitation connue que nous espérons pouvoir résoudre à l’avenir. En attendant, vous pouvez utiliser la [version SSMS 2014](../ssms/previous-sql-server-management-studio-releases.md) pour enregistrer les plans de maintenance.  
    
5. **Les installations non anglaises de SSMS peuvent nécessiter l’installation d’un package de sécurité supplémentaire.**  
Les versions localisées dans des langues autres que l’anglais nécessitent la [mise à jour de sécurité KB 2862966](https://support.microsoft.com/en-us/kb/2862966) si l’installation est effectuée sous Windows 8, Windows 7, Windows Server 2012 et Windows Server 2008 R2.
  
6. **Le démarrage du module Gestionnaire de configuration SQL Server échoue si aucun serveur SQL Server n’est installé sur l’ordinateur client**  
    Si SQL Server n’est pas installé sur votre ordinateur client, lorsque vous démarrez le module Gestionnaire de configuration SQL Server, le message d’erreur suivant s’affiche :   
     `Cannot connect to WMI provider. You do not have permission or the server is unreachable. Note that you can only manage SQL Server 2005 and later servers with SQL Server Configuration Manager. Invalid namespace \[0x8004100e]`,   
   
     * Si vous avez ajouté vos instances SQL Server à la liste « Serveurs inscrits » dans SSMS :  
        1. Accédez à la vue « Serveurs inscrits » dans SSMS.  
        2. Cliquez avec le bouton droit sur l’instance SQL Server que vous souhaitez configurer.  
        3. Sélectionnez « Gestionnaire de configuration SQL Server... » dans le menu contextuel.    
          
      * Si vous n’avez pas ajouté d’instance SQL Server à la liste « Serveurs inscrits » dans SSMS :  
        1. Ouvrez une invite de commandes en tant qu’administrateur.  
        2. Exécutez l’outil Mofcomp à l’aide de la commande suivante :  
    `mofcomp "%programfiles(x86)%\Microsoft SQL Server\130\Shared\sqlmgmproviderxpsp2up.mof"`  
        3. Après avoir exécuté l’outil Mofcomp, pour que les modifications prennent effet, redémarrez le service WMI à l’aide de la commande suivante :  
        `net stop "Windows Management Instrumentation"`  
        `net start “Windows Management Instrumentation”`  

## <a name="feedback"></a>Commentaires  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [Forum des outils clients SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Signaler un problème ou faire une suggestion sur Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback).  
  
## <a name="see-also"></a>Voir aussi  
[Didacticiel de SQL Server Management Studio](../ssms/use-sql-server-management-studio.md)  
[Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
[Versions antérieures de SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  

  

