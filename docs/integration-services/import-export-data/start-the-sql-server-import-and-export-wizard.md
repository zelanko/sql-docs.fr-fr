---
title: "D&#233;marrer l’Assistant Importation et Exportation SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assistant Importation et Exportation SQL Server"
  - "démarrage de l'Assistant Importation et Exportation SQL Server"
  - "Assistant Importation et Exportation"
  - "démarrage de l'Assistant Importation et Exportation"
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
caps.latest.revision: 130
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 112
---
# D&#233;marrer l’Assistant Importation et Exportation SQL Server
Vous pouvez démarrer l’Assistant Importation et exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’une des manières suivantes.
-   À partir du [menu Démarrer](#startStart) ou d’une [invite de commandes](#startCmd), pour importer depuis ou exporter vers n’importe quelle source de données prise en charge.
-   À partir de [SQL Server Management Studio (SSMS)](#startSSMS), si vous importez vers ou exportez depuis SQL Server.
-   À partir de [Visual Studio avec SQL Server Data Tools (SSDT)](#startVS), si vous avez un projet SQL Server Integration Services ouvert.

Cette rubrique explique seulement comment **démarrer** l’Assistant.
-   Si vous recherchez une vue d’ensemble de l’Assistant, consultez [Importer et exporter des données avec l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).
-   Si vous recherchez des informations sur les étapes de l’Assistant, sélectionnez la page voulue dans le menu de navigation du contenu. Il existe une page distincte de documentation pour chaque page de l’Assistant. Sinon, pour afficher la documentation sur une page ou une boîte de dialogue déterminée de l’Assistant, appuyez sur la touche F1 à partir de cette page.

**Procurez-vous l’Assistant.** Si vous souhaitez exécuter l’Assistant, mais [!INCLUDE[msCoName] (../Token/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas installé sur votre ordinateur, vous pouvez installer l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en installant SSDT (SQL Server Data Tools). Pour plus d’informations, consultez [Télécharger SSDT (SQL Server Data Tools)](https://msdn.microsoft.com/library/mt204009.aspx).  

## <a name="a-namestartstarta-start-the-wizard-from-the-start-menu"></a><a name="startStart"></a> Démarrer l’Assistant à partir du menu Démarrer  
1.  Dans le menu **Démarrer**, cliquez sur **Toutes les applications**.
2.  Recherchez et développez **Microsoft SQL Server 2016**.
3.  Cliquez sur l’une des options suivantes :
  
    -   **Importer-exporter des données SQL Server 2016 (64 bits)**
          
    -   **Importer-exporter des données SQL Server 2016 (32 bits)**  
  
Exécutez la version 64 bits de l’Assistant, sauf si vous savez que votre source de données a besoin d’un fournisseur de données 32 bits.
 
![Démarrer l’Assistant (Démarrer)](../../integration-services/import-export-data/media/start-wizard-start.jpg)
  
## <a name="a-namestartcmda-start-the-wizard-from-the-command-prompt"></a><a name="startCmd"></a> Démarrer l’Assistant à partir d’une invite de commandes  
Dans une fenêtre d’invite de commandes, exécutez **DTSWizard.exe** à partir d’un des emplacements suivants :  
  
-   **C:\Program Files\Microsoft SQL Server\130\DTS\Binn** pour la version 64 bits.  
  
-   **C:\Program Files (x86)\Microsoft SQL Server\130\DTS\Binn** pour la version 32 bits.  
  
Exécutez la version 64 bits de l’Assistant, sauf si vous savez que votre source de données a besoin d’un fournisseur de données 32 bits.

![Démarrer l’Assistant (cmd)](../../integration-services/import-export-data/media/start-wizard-cmd.jpg)  
  
## <a name="a-namestartssmsa-start-the-wizard-from-sql-server-management-studio-ssms"></a><a name="startSSMS"></a> Démarrer l’Assistant à partir de SQL Server Management Studio (SSMS)  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
2.  Développez **Bases de données**.
3.  Cliquez avec le bouton droit sur le nom d’une base de données.
4.  Pointez sur **Tâches**.
5.  Cliquez sur l’une des options suivantes :
  
    -   **Importer des données**
      
    -   **Exporter des données**  

![Démarrer l’Assistant SSMS](../../integration-services/import-export-data/media/start-wizard-ssms.jpg) 

Si vous n’avez pas installé SQL Server, ou que vous avez installé SQL Server mais pas SQL Server Management Studio, consultez [Télécharger SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx).
    
## <a name="a-namestartvsa-start-the-wizard-from-visual-studio-with-sql-server-data-tools-ssdt"></a><a name="startVS"></a> Démarrer l’Assistant à partir de Visual Studio avec SQL Server Data Tools (SSDT)  
 Dans Visual Studio avec [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], après avoir ouvert un projet Integration Services, effectuez l’une des opérations suivantes.  
  
-   Dans le menu **Projet**, cliquez sur **Assistant d’importation et d’exportation SSIS**. 

    ![Démarrer l’Assistant (projet)](../../integration-services/import-export-data/media/start-wizard-project.jpg) 
    
    \- ou -
    
-   Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier **Packages SSIS**, puis cliquez sur **Assistant d’importation et d’exportation SSIS**.

    ![Démarrer l’Assistant (packages)](../../integration-services/import-export-data/media/start-wizard-packages.jpg)

Si vous n’avez pas installé Visual Studio, ou que vous avez installé Visual Studio mais pas SQL Server Data Tools, consultez [Télécharger SSDT (SQL Server Data Tools)](https://msdn.microsoft.com/library/mt204009.aspx). 

## <a name="get-help-while-the-wizard-is-running"></a>Obtenir de l’aide pendant l’exécution de l’Assistant
> [!TIP] Pour afficher la documentation sur une page ou une boîte de dialogue déterminée de l’Assistant, appuyez sur la touche F1 à partir de cette page.   

 ## <a name="whats-next"></a>Étape suivante  
 Quand vous démarrez l’Assistant, la première page est **Assistant Importation et Exportation SQL Server**. Vous n’avez aucune action à effectuer dans cette page. Pour plus d’informations, consultez [Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md).  
  
  