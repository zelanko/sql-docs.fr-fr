---
title: "Installer le moteur de base de donn&#233;es SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Moteur de base de données [SQL Server], installation"
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
caps.latest.revision: 45
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 45
---
# Installer le moteur de base de donn&#233;es SQL Server
  Le composant [!INCLUDE[ssDE](../../includes/ssde-md.md)] de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est le service de base pour le stockage, le traitement et la protection des données. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] fournit un accès contrôlé et un traitement transactionnel rapide qui répondent aux exigences des applications les plus gourmandes en termes de données dans votre entreprise.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge jusqu’à 50 instances du [!INCLUDE[ssDE](../../includes/ssde-md.md)] sur un seul ordinateur. Pour créer une installation par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Installer SQL Server 2016 avec l’Assistant Installation &#40;programme d’installation&#41;](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md).  
  
 **Important** Pour des installations locales, vous devez exécuter le programme d’installation en tant qu’administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.  
  
 Les fonctionnalités suivantes sont installées quand vous sélectionnez **Moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** dans la page Composants à installer de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   Réplication (composant facultatif)  
  
-   Recherche en texte intégral (composant facultatif)  
  
-   Data Quality Services. est un composant facultatif  
  
    > [!NOTE]  
    >  Dans cette version, le fait de cocher la case **Data Quality Services** au moment de l’installation n’installe pas le serveur Data Quality Services (DQS). Vous devrez procéder à des étapes supplémentaires après l'installation pour installer le serveur DQS. Pour plus d’informations, consultez [Installer Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
 Les fonctionnalités supplémentaires suivantes sont des options pour un grand nombre de scénarios utilisateur classiques :  
  
-   Data Quality Client  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Composants de connectivité  
  
-   Modèles de programmation  
  
-   Outils d'administration  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   Composants de documentation  
  
> [!NOTE]  
>  Par défaut, les exemples de bases de données et les exemples de code ne sont pas installés dans le cadre de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour installer les exemples de bases de données et les exemples de code, consultez le [site web CodePlex](http://go.microsoft.com/fwlink/?LinkId=87843).  
  
## Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)   
 [Éditions et composants de SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)   
 [Planification d'une installation SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Solutions haute disponibilité &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [Effectuer une mise à niveau vers SQL Server 2016 à l’aide de l’Assistant Installation &#40;programme d’installation&#41;](../../database-engine/install-windows/upgrade-to-sql-server-2016-using-the-installation-wizard-setup.md)  
  
  