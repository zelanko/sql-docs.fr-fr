---
title: "Démarrez SQL Server, Assistant Importation et exportation | Documents Microsoft"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Import and Export Wizard
- starting SQL Server Import and Export Wizard
- Import and Export Wizard
- starting Import and Export Wizard
ms.assetid: 5fc4f6d1-1f6f-444e-9aeb-827f85e1c405
caps.latest.revision: 130
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: 4fd91a36594a8d0d50e3f4eb8490497d6fe0e172
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---
# <a name="start-the-sql-server-import-and-export-wizard"></a>Démarrer l’Assistant Importation et Exportation SQL Server

 > Pour obtenir un contenu pour les versions précédentes de SQL Server, consultez [exécuter le SQL Server Assistant Importation et exportation](https://msdn.microsoft.com/en-US/library/ms140052(SQL.120).aspx).

Démarrer le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation de l’une des méthodes décrites dans cette rubrique pour importer les données et exporter des données vers n’importe quelle source de données pris en charge.

> [!IMPORTANT]
> Cette rubrique explique seulement comment **démarrer** l’Assistant. Si vous avez besoin d’un autre élément, consultez [les tâches et contenu](#related).

Vous pouvez démarrer l’Assistant :
-   À partir du [menu Démarrer](#startStart).
-   À partir du [invite de commandes](#startCmd). 
-   À partir de [SQL Server Management Studio (SSMS)](#startSSMS).
-   À partir de [Visual Studio avec SQL Server Data Tools (SSDT)](#startVS).

## <a name="prerequisite---is-the-wizard-installed-on-your-computer"></a>Condition préalable - correspond à l’Assistant installé sur votre ordinateur ?
Si vous souhaitez exécuter l’Assistant, mais [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas installé sur votre ordinateur, vous pouvez installer l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en installant SSDT (SQL Server Data Tools). Pour plus d’informations, consultez [Télécharger SSDT (SQL Server Data Tools)](https://msdn.microsoft.com/library/mt204009.aspx).

> [!NOTE]
> Pour utiliser la version 64 bits du SQL Server Assistant Importation et exportation, vous devez installer SQL Server. SQL Server Data Tools (SSDT) et SQL Server Management Studio (SSMS) sont des applications 32 bits et installent uniquement les fichiers de 32 bits, y compris la version 32 bits de l’Assistant.

## <a name="startStart"></a> menu Démarrer  
### <a name="start-the-sql-server-import-and-export-wizard-from-the-start-menu"></a>Démarrer le SQL Server Assistant Importation et exportation à partir du menu Démarrer
1.  Sur le **Démarrer** menu, recherchez et développez **Microsoft SQL Server 2016**.
3.  Cliquez sur l’une des options suivantes :
  
    -   **Importer-exporter des données SQL Server 2016 (64 bits)**
          
    -   **Importer-exporter des données SQL Server 2016 (32 bits)**  
  
    Exécutez la version 64 bits de l’Assistant, sauf si vous savez que votre source de données a besoin d’un fournisseur de données 32 bits.
 
    ![Démarrer l’Assistant (Démarrer)](../../integration-services/import-export-data/media/start-wizard-start.jpg)
  
## <a name="startCmd"></a> Command prompt
### <a name="start-the-sql-server-import-and-export-wizard-from-the-command-prompt"></a>Démarrer le SQL Server Assistant Importation et exportation à partir de l’invite de commandes  
Dans une fenêtre d’invite de commandes, exécutez **DTSWizard.exe** à partir d’un des emplacements suivants :  
  
-   **C:\Program Files\Microsoft SQL Server\130\DTS\Binn** pour la version 64 bits.  
  
-   **C:\Program Files (x86)\Microsoft SQL Server\130\DTS\Binn** pour la version 32 bits.  
  
Exécutez la version 64 bits de l’Assistant, sauf si vous savez que votre source de données a besoin d’un fournisseur de données 32 bits.

![Démarrer l’Assistant (cmd)](../../integration-services/import-export-data/media/start-wizard-cmd.jpg)  
  
## <a name="startSSMS"></a> SQL Server Management Studio (SSMS)
### <a name="start-the-sql-server-import-and-export-wizard-from-sql-server-management-studio-ssms"></a>Démarrer le SQL Server Assistant Importation et exportation à partir de SQL Server Management Studio (SSMS)    
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à une instance du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)].
    
2.  Développez **Bases de données**.
3.  Cliquez avec le bouton droit sur le nom d’une base de données.
4.  Pointez sur **Tâches**.
5.  Cliquez sur l’une des options suivantes :
  
    -   **Importer des données**
      
    -   **Exporter des données**  

    ![Démarrer l’Assistant SSMS](../../integration-services/import-export-data/media/start-wizard-ssms.jpg) 

Si vous n’avez pas installé SQL Server, ou que vous avez installé SQL Server mais pas SQL Server Management Studio, consultez [Télécharger SQL Server Management Studio (SSMS)](../../ssms/download-sql-server-management-studio-ssms.md).
  
## <a name="startVS"></a>Visual Studio
### <a name="start-the-sql-server-import-and-export-wizard-from-visual-studio-with-sql-server-data-tools-ssdt"></a>Démarrer le SQL Server Assistant Importation et exportation à partir de Visual Studio avec SQL Server Data Tools (SSDT) 
 Dans Visual Studio avec [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], après avoir ouvert un projet Integration Services, effectuez l’une des opérations suivantes. 
  
-   Dans le menu **Projet** , cliquez sur **Assistant d’importation et d’exportation SSIS**. 

    ![Démarrer l’Assistant (projet)](../../integration-services/import-export-data/media/start-wizard-project.jpg) 
    
    \- ou -
    
-   Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le dossier **Packages SSIS** , puis cliquez sur **Assistant d’importation et d’exportation SSIS**.

    ![Démarrer l’Assistant (packages)](../../integration-services/import-export-data/media/start-wizard-packages.jpg)

Si vous n’avez pas installé Visual Studio, ou que vous avez installé Visual Studio mais pas SQL Server Data Tools, consultez [Télécharger SSDT (SQL Server Data Tools)](../../ssdt/download-sql-server-data-tools-ssdt.md).

## <a name="get-the-wizard"></a>Obtenir de l’Assistant
Si vous souhaitez exécuter l’Assistant, mais [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas installé sur votre ordinateur, vous pouvez installer l’Assistant Importation et Exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en installant SSDT (SQL Server Data Tools). Pour plus d’informations, consultez [Télécharger SSDT (SQL Server Data Tools)](https://msdn.microsoft.com/library/mt204009.aspx).

## <a name="get-help-while-the-wizard-is-running"></a>Obtenir de l’aide pendant l’exécution de l’Assistant
> [!TIP]
> Pour afficher la documentation sur une page ou une boîte de dialogue déterminée de l’Assistant, appuyez sur la touche F1 à partir de cette page.   

 ## <a name="whats-next"></a>Étape suivante  
 Quand vous démarrez l’Assistant, la première page est **Assistant Importation et Exportation SQL Server**. Vous n’avez aucune action à effectuer dans cette page. Pour plus d’informations, consultez [Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md).  
  
## <a name="related"></a>Contenu et des tâches connexes  
 Voici quelques autres tâches de base.
-   **Voir un exemple rapide du fonctionne de l’Assistant.**

    -   **Si vous préférez afficher les captures d’écran.** Examinez cet exemple de bout en bout simple sur une seule page - [prise en main avec cet exemple simple de l’Assistant Importation et exportation](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md).

    -   **Si vous préférez regarder une vidéo.** Regardez cette vidéo de quatre minutes à partir de YouTube qui montre l’Assistant et explique clairement et simplement comment exporter des données vers Excel - [à l’aide du SQL Server Assistant Importation et exportation pour l’exportation vers Excel](https://go.microsoft.com/fwlink/?linkid=829049).

-   **En savoir plus sur le fonctionne de l’Assistant.**

    -   **En savoir plus sur l’Assistant.** Si vous recherchez une vue d’ensemble de l’Assistant, consultez [Importer et exporter des données avec l’Assistant Importation et Exportation SQL Server](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

    -   **En savoir plus sur les étapes de l’Assistant.** Si vous recherchez des informations sur les étapes de l’Assistant, consultez [les étapes dans le SQL Server Assistant Importation et exportation](../../integration-services/import-export-data/steps-in-the-sql-server-import-and-export-wizard.md). Il existe également une page distincte de la documentation pour chaque page de l’Assistant.

    -   **Découvrez comment se connecter à des destinations et des sources de données.** Si vous recherchez des informations sur la façon de se connecter à vos données, sélectionnez la page à partir de la liste ici - [se connecter aux sources de données avec le SQL Server Assistant Importation et exportation](../../integration-services/import-export-data/connect-to-data-sources-with-the-sql-server-import-and-export-wizard.md). Il existe une page distincte de la documentation pour chacun de plusieurs sources de données couramment utilisées.



