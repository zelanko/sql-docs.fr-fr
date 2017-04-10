---
title: "Travaux de l&#39;Agent SQL&#160;Server pour les packages | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "travaux [Integration Services]"
  - "exécution automatique de packages"
  - "planification de packages [Integration Services]"
  - "Agent SQL Server [Integration Services]"
ms.assetid: ecf7a5f9-b8a7-47f1-9ac0-bac07cb89e31
caps.latest.revision: 54
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 53
---
# Travaux de l&#39;Agent SQL&#160;Server pour les packages
  Automatisez et planifiez l’exécution des packages [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à l’aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Vous pouvez planifier les packages qui sont déployés sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et sont stockés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le magasin de packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] et le système de fichiers.  
  
## Rubriques de cette section  
 Cette rubrique contient les sections suivantes :  
  
-   [Planification de travaux dans l'Agent SQL Server](#jobs)  
  
-   [Planification de packages Integration Services](#packages)  
  
-   [Dépannage de packages planifiés](#trouble)  
  
##  <a name="jobs"></a> Planification de travaux dans SQL Server Agent  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent est le service installé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui vous permet d’automatiser et de planifier des tâches en exécutant les travaux de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Agent. Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit s’exécuter avant que les travaux puissent s’exécuter automatiquement. Pour plus d’informations, consultez [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md).  
  
 Le nœud **SQL Server Agent** s’affiche dans l’Explorateur d’objets dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] quand vous vous connectez à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Pour automatiser une tâche récurrente, créez un travail à l’aide de la boîte de dialogue **Nouveau travail**. Pour plus d’informations, consultez [Implémenter des travaux](../../ssms/agent/implement-jobs.md).  
  
 Après avoir créé le travail, vous devez ajouter au moins une étape. Un travail peut inclure plusieurs étapes, et chaque étape peut effectuer une tâche différente. Pour plus d’informations, consultez [Gérer les étapes de travail](../../ssms/agent/manage-job-steps.md).  
  
 Après avoir créé le travail et les étapes du travail, vous pouvez créer une planification d'exécution du travail. Cependant, vous pouvez également créer un travail non planifié que vous exécutez manuellement. Pour plus d’informations, consultez [Créer des planifications et les attacher à des travaux](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
 Vous pouvez améliorer le travail en définissant des options de notification, par exemple en spécifiant l'envoi de messages électroniques à un opérateur à la fin du travail ou en ajoutant des alertes. Pour plus d’informations, consultez [Alertes](../../ssms/agent/alerts.md).  
  
##  <a name="packages"></a> Planification de packages Integration Services  
 Quand vous créez un travail [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour planifier des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous devez ajouter au moins une étape et affecter à son type la valeur **Package SQL Server Integration Services**. Un travail peut inclure plusieurs étapes, et chaque étape peut exécuter un package différent.  
  
 L’exécution d’un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] à partir d’une étape du travail revient à exécuter un package à l’aide des utilitaires **dtexec** (dtexec.exe) et **DTExecUI** (dtexecui.exe). Au lieu de définir les options d’exécution pour un package à l’aide des options de ligne de commande ou de la boîte de dialogue **Utilitaire d’exécution de package**, vous définissez les options d’exécution dans la boîte de dialogue **Nouvelle étape de travail**. Pour plus d’informations sur les options de ligne de commande pour l’exécution d’un package, consultez [Utilitaire dtexec](../../integration-services/packages/dtexec-utility.md).  
  
 Pour plus d’informations, consultez [Planifier un package à l’aide de SQL Server Agent](../../integration-services/packages/schedule-a-package-by-using-sql-server-agent.md).  
  
 Pour visionner une vidéo qui montre comment utiliser [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour exécuter un package, consultez la page [Procédure : automatiser l’exécution du package SSIS à l’aide de l’Agent SQL Server (vidéo de SQL Server)](http://go.microsoft.com/fwlink/?LinkId=141771), dans MSDN Library.  
  
##  <a name="trouble"></a> Dépannage  
 Une étape de travail de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent peut ne pas démarrer un package même si le package est exécuté correctement dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] et à partir de la ligne de commande. Ce problème est connu et plusieurs solutions sont recommandées. Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] Article de la Base de connaissances intitulé [Un package SSIS n’est pas exécuté quand vous appelez le package SSIS à partir d’une étape de travail de SQL Server Agent](http://support.microsoft.com/kb/918760)  
  
-   Vidéo intitulée [Résolution des problèmes : exécution du package SSIS à l’aide de l’Agent SQL Server (vidéo de SQL Server)](http://go.microsoft.com/fwlink/?LinkId=141772), dans MSDN Library.  
  
 Lorsqu'une étape de travail de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent démarre un package, l'exécution du package peut échouer ou le package peut s'exécuter correctement mais avec des résultats inattendus. Vous pouvez utiliser les outils suivants pour résoudre ces problèmes.  
  
-   Pour les packages enregistrés dans la base de données MSDB de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dans le magasin de packages d’[!INCLUDE[ssIS](../../includes/ssis-md.md)] ou dans un dossier sur votre ordinateur local, vous pouvez utiliser la **Visionneuse du fichier journal** ainsi que tous les journaux et les fichiers de vidage du débogage générés pendant l’exécution du package.  
  
     **Pour utiliser la Visionneuse du fichier journal, procédez comme suit.**  
  
    1.  Cliquez avec le bouton droit sur le travail de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans l’Explorateur d’objets, puis cliquez sur **Afficher l’historique**.  
  
    2.  Dans la zone **Résumé du fichier journal**, recherchez l’exécution du travail qui présente le message **Travail échoué** dans la colonne **Message**.  
  
    3.  Développez le nœud de travail, puis cliquez sur l’étape de travail pour afficher les détails du message dans la zone sous le **Résumé du fichier journal**.  
  
-   Pour les packages enregistrés dans la base de données SSISDB, vous pouvez également utiliser la **Visionneuse du fichier journal** ainsi que tous les journaux et les fichiers de vidage du débogage générés pendant l’exécution du package. En outre, vous pouvez utiliser les rapports pour le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
     **Pour rechercher des informations dans les rapports sur l'exécution du package associée à une exécution de travail, procédez comme suit.**  
  
    1.  Suivez les étapes ci-dessus pour afficher les détails du message de l'étape de travail.  
  
    2.  Recherchez l'ID d'exécution répertorié dans le message.  
  
    3.  Développez le nœud du catalogue Integration Services dans l'Explorateur d'objets.  
  
    4.  Cliquez avec le bouton droit sur SSISDB, pointez sur Rapports, puis sur Rapports standard, et cliquez sur Toutes les exécutions.  
  
    5.  Dans le rapport **Toutes les exécutions**, recherchez l’ID d’exécution dans la colonne **ID**. Cliquez sur **Vue d’ensemble**, **Tous les messages**, ou **Performances de l’exécution** pour afficher des informations sur cette exécution du package.  
  
         Pour plus d’informations sur les rapports Vue d’ensemble, Tous les messages et Performances de l’exécution, consultez [Rapports du serveur Integration Services](../../integration-services/performance/reports-for-the-integration-services-server.md).  
  
## Ressources externes  
  
-   Article de la Base de connaissances intitulé [Un package SSIS n’est pas exécuté lorsque vous appelez le package SSIS à partir d’une étape de travail de SQL Server Agent](http://support.microsoft.com/kb/918760) sur le site web [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
-   Vidéo intitulée [Résolution des problèmes : exécution du package SSIS à l’aide de l’Agent SQL Server (vidéo de SQL Server)](http://go.microsoft.com/fwlink/?LinkId=141772) dans MSDN Library  
  
-   Vidéo intitulée [Procédure : automatiser l’exécution du package SSIS à l’aide de l’Agent SQL Server (vidéo de SQL Server)](http://go.microsoft.com/fwlink/?LinkId=141771) dans MSDN Library  
  
-   Article technique intitulé [Checking SQL Server Agent jobs using Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=165675) sur mssqltips.com  
  
-   Article technique intitulé [Auto alert for SQL Agent jobs when they are enabled or disabled](http://go.microsoft.com/fwlink/?LinkId=165676) sur mssqltips.com  
  
-   Entrée de blog intitulée [Configuring SQL Agent Jobs to Write to Windows Event Log](http://go.microsoft.com/fwlink/?LinkId=220745) sur mssqltips.com  
  
  