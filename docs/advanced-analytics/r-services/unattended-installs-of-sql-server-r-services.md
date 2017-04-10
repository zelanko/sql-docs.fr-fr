---
title: "Installations sans assistance de SQL Server R Services | Microsoft Docs"
ms.custom: ""
ms.date: "02/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77e92b2d-5777-4c31-bf02-f931ed54a247
caps.latest.revision: 18
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 14
---
# Installations sans assistance de SQL Server R Services
    
Avant de commencer le processus d’installation, notez ces exigences :

+ Vous devez installer le moteur de base de données sur chaque instance d’utilisation de Services de R (de base de données) dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
+ Si vous effectuez une installation en mode hors connexion, vous devez télécharger les composants requis de R à l’avance et les copier dans un dossier local. Pour les emplacements de téléchargement, consultez [installation des composants R sans accès à Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md).   
+ Il existe un nouveau paramètre, */IACCEPTROPENLICENSETERMS*, qui indique que vous avez accepté les termes du contrat de licence pour l’utilisation des composants open source de R. Si vous n’incluez pas ce paramètre dans votre ligne de commande, le programme d’installation échoue.  
  
## Effectuer une installation sans assistance de R Services (dans la base de données)  
 L’exemple suivant illustre les fonctionnalités minimales requises à spécifier dans la ligne de commande lorsque vous effectuez une installation sans assistance de R Services dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
###  <a name="bkmk_Unattended"></a>  
  
1.  Exécutez la commande suivante à partir d’une invite de commandes avec élévation de privilèges :  
  
    ```  
    Setup.exe /q /ACTION=Install /FEATURES=SQL,AdvancedAnalytics /INSTANCENAME=MSSQLSERVER /SECURITYMODE=SQL /SAPWD="%password%" /SQLSYSADMINACCOUNTS="<username>" /IACCEPTSQLSERVERLICENSETERMS /IACCEPTROPENLICENSETERMS  
    ```  
  
2.  Une fois l’installation terminée, dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], exécutez la commande suivante pour activer la fonctionnalité.  
  
    ```  
    Exec sp_configure  'external scripts enabled', 1  
    Reconfigure  with  override  
  
    ```  
  
    > [!NOTE]  
    >  Vous devez explicitement activer la fonctionnalité du moteur. Dans le cas contraire, il ne sera pas possible d’appeler des scripts R, même si la fonctionnalité a été installée et configurée par le programme d’installation.  
  
3.  Redémarrez l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Cette opération redémarre automatiquement le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] .  
  
## Voir aussi  
 [Résoudre les problèmes d’installation liés à R Services](../Topic/Troubleshooting%20R%20Services%20Setup.md)  
  
  