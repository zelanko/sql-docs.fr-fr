---
title: "Visionneuse d’aide et contenu hors connexion pour SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 06/27/2017
ms.prod: sql-non-specified
ms.technology: server-general
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2014
- SQL Server 2016
- SQL Server 2017
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
caps.latest.revision: "8"
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80f13a760e8176eb0d0bafbac29cf162f473caf4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="help-viewer-and-offline-content-for-sql-server"></a>Visionneuse d’aide et contenu hors connexion pour SQL Server
  
  
  
Cet article décrit comment installer la visionneuse d’aide et consulter la documentation SQL Server hors connexion. L’article s’applique à la documentation de [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)], SQL Server 2016 et SQL Server 2017. 

## <a name="install-help-viewer"></a>Installer la visionneuse d’aide
Le tableau suivant répertorie les outils qui installent la visionneuse d’aide, en fonction de la version de SQL Server que vous utilisez. Installez l’un des outils répertoriés pour installer la visionneuse d’aide.


|**Version de SQL Server**|**Outils qui installent la visionneuse d’aide**|**Version de la visionneuse d’aide installée**|
|---------|---------|---------|
|SQL Server 2017<br>SQL Server 2016     |   [Dernière version de SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)<br><br>[Dernière version de SQL Server Data Tools pour Visual Studio 2015](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt)<br><br>Visual Studio 2017 (*prend en charge uniquement SQL Server 2016*)  |  v2.x       |
|SQL Server 2014    | SQL Server 2014 Management Studio<br><br>Versions de Visual Studio antérieures à Visual Studio 2012        |  v1.x       |


> [!IMPORTANT]
> SQL Server 2016 installe la visionneuse d’aide version 1.1 qui ne peut pas être utilisée pour afficher la documentation de SQL Server 2016 et 2017.
> <br>
> <br>
> SQL Server 2017 n’installe pas la visionneuse d’aide.
> <br>
> <br>
> Pour installer la visionneuse d’aide avec Visual Studio 2017, cliquez sur l’onglet **Composants individuels** dans le **programme d’installation de Visual Studio**, sur **Visionneuse d’aide** dans la catégorie **Outils de code**, puis sur **Installer**. 
> <br>
> <br>
> Vous pouvez aussi afficher l’aide locale de [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] avec la visionneuse d’aide version 2.x à la seule condition de choisir l’option **Installer du contenu à partir du disque**. 


## <a name="sql-server-2016-sql-server-2017-offline-content"></a>Contenu hors connexion pour SQL Server 2016, SQL Server 2017  
 
**Pour installer le contenu hors connexion**  
1. Ouvrez la visionneuse d’aide en lançant SQL Server Management Studio ou Visual Studio, puis en cliquant sur **Ajouter et supprimer le contenu d’aide** dans le menu **Aide**.  
2. Cliquez sur l’onglet **Gérer le contenu**.  
3. Pour installer l’aide à partir d’une source en ligne, cliquez sur **En ligne** dans la zone **Source d’installation**.  
![HelpViewer2_ManageContent_OnlineSource](../sql-server/media/helpviewer2-managecontent-onlinesource.png)  
7. Cliquez sur **Ajouter** en regard de la documentation que vous voulez installer, puis cliquez sur **Mettre à jour**.  
![HelpViewer2_ManageContent_AddContent](../sql-server/media/helpviewer2-managecontent-addcontent.png)     
  
   >[!IMPORTANT] 
   >Dans SQL Server Management Studio et Visual Studio, l’application Visionneuse d’aide peut se figer (se bloquer) pendant l’ajout de la documentation. Pour résoudre ce problème, procédez comme indiqué ci-dessous. Pour plus d’informations sur ce problème, consultez [La visionneuse d’aide Visual Studio se fige sur l’écran de démarrage](https://msdn.microsoft.com/library/mt654096.aspx).  
   >>Ouvrez le fichier %LOCALAPPDATA%\Microsoft\HelpViewer2.3\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio15_en-US.settings dans le Bloc-notes et remplacez la date dans le code ci-dessous par une date future. Ce fichier n’est disponible sur votre ordinateur local qu’à partir du moment où vous avez installé Visual Studio. 
   >>>Dernière actualisation du cache = « 31/12/2017 00:00:00 »  
  
    La table des matières figurant dans le volet gauche se met automatiquement à jour pour inclure la documentation que vous avez ajoutée.  
![HelpViewer2_withContentInstalled](../sql-server/media/helpviewer2-withcontentinstalled.png)

1. (Facultatif) La zone **Chemin d’accès au stockage local** sous l’onglet **Gérer le contenu** indique l’emplacement où est installée la documentation sur l’ordinateur local. Pour déplacer la documentation vers un autre emplacement, cliquez sur **Déplacer**, entrez un chemin de dossier dans le champ **Vers** de la boîte de dialogue **Déplacer le contenu**, puis cliquez sur **OK**.

   ![HelpViewer2_Move Content Dialog](../sql-server/media/helpviewer2-move-content-dialog.png)

   Une fois que le contenu est déplacé, le nouvel emplacement s’affiche dans **Chemin d’accès au stockage local**.
      
   >[!IMPORTANT]
   > Si un message s’affiche indiquant que l’opération de déplacement a échoué, fermez la boîte de message, puis fermez et rouvrez la visionneuse d’aide. Le nouvel emplacement du contenu doit à présent figurer dans **Chemin d’accès au stockage local**.   
 
## <a name="includesssql14mdincludessssql14-mdmd-offline-content"></a>Contenu hors connexion pour [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] 
 
  
**Pour installer le contenu hors connexion**  
1. Accédez au [site de téléchargement](https://www.microsoft.com/en-us/download/details.aspx?id=42557) du contenu d’aide, puis cliquez sur **Télécharger**.  
2. Cliquez sur **Enregistrer** dans la boîte de message pour enregistrer le fichier SQLServer2014Documentation_*.exe sur votre ordinateur.  

 Pour les environnements protégés par un pare-feu et un proxy, enregistrez le fichier téléchargé sur un lecteur USB ou tout autre média amovible pouvant être amené dans l’environnement.   

3. Double-cliquez sur le fichier .exe pour décompresser le fichier de contenu d’aide, puis enregistrez le fichier dans un dossier local ou partagé.  
4. Ouvrez le **Gestionnaire de bibliothèque d’aide** en lançant SQL Server Management Studio ou Visual Studio, puis en cliquant sur **Gérer les paramètres de l’aide** dans le menu **Aide**.  
5. Cliquez sur **Installer du contenu à partir du disque** et accédez au dossier dans lequel vous avez décompressé le fichier de contenu d’aide.  
  
     Sélectionnez Installer du contenu à partir du disque  |Accédez au fichier de contenu d’aide   
     ---------|---------  
     ![HelpLibraryManager_MainPage_InstallFromDisk](../sql-server/media/helplibrarymanager-mainpage-installfromdisk.png)    | ![HelpLibraryManager_InstallContentFromDisk_dialog1](../sql-server/media/helplibrarymanager-installcontentfromdisk-dialog1.png)          
  
     >[!IMPORTANT]
     > Pour éviter d’installer du contenu d’aide locale qui ne présente qu’une table des matières partielle, utilisez l’option **Installer du contenu à partir du disque** dans le **Gestionnaire de bibliothèque d’aide**.  
     >>Si vous avez utilisé l’option **Installer du contenu à partir d’une source en ligne** et que la visionneuse d’aide affiche une table des matières partielle, consultez ce [billet de blog](https://blogs.msdn.microsoft.com/womeninanalytics/2016/06/21/troubleshoot-local-help-for-sql-server-2014/) pour savoir comment résoudre ce problème. 

8. Cliquez successivement sur le fichier HelpContentSetup.msha, sur **Ouvrir**, puis sur **Suivant**.  
9. Cliquez sur **Ajouter** en regard de la documentation que vous voulez installer, puis cliquez sur **Mettre à jour**.  
  
   ![HelpLibraryManager_InstallContentFromDisk_dialog2](../sql-server/media/helplibrarymanager-installcontentfromdisk-dialog2.png)  
10. Cliquez sur **Terminer**, puis sur **Quitter**.
11. Rouvrez le **Gestionnaire de bibliothèque d’aide**, cliquez sur **Choisir l’aide en ligne ou locale**, puis sur **Utiliser l’aide locale**.
12. Ouvrez la visionneuse d’aide pour afficher le contenu en cliquant sur **Afficher l’aide** dans le menu **Aide**. Le contenu que vous avez installé doit figurer dans la table des matières, dans le volet gauche.  
  
    ![HelpViewer1_withContentInstalled_ZoomedIn](../sql-server/media/helpviewer1-withcontentinstalled-zoomedin.png)  
  
## <a name="view-online-content-in-help-viewer"></a>Afficher le contenu en ligne dans la visionneuse d’aide

Dans la visionneuse d’aide v2.x, vous pouvez afficher le contenu en ligne en effectuant l’une des opérations suivantes.

- Dans SQL Server Management Studio, cliquez sur **Afficher l’aide** dans le menu **Aide**. La documentation s’affiche dans un navigateur.
![HelpViewer2_SSMS_ChooseOnlineORLocalHelp](../sql-server/media/helpviewer2-ssms-chooseonlineorlocalhelp.png)

- Dans Visual Studio, cliquez sur **Définir les préférences d’aide** dans le menu **Aide**, puis sur **Lancer dans le navigateur**. Quand vous cliquez sur **Afficher l’aide** dans le menu **Aide**, la documentation s’affiche dans un navigateur.

![HelpViewer2_VisualStudio_ChooseOnlineORLocalHelp](../sql-server/media/helpviewer2-visualstudio-chooseonlineorlocalhelp.png)   

Dans la visionneuse d’aide v1.x, vous pouvez afficher le contenu en ligne en effectuant l’une des opérations suivantes.
1. Ouvrez le **Gestionnaire de bibliothèque d’aide** en cliquant sur **Gérer les paramètres de l’aide** dans le menu **Aide**.  
2. Dans la boîte de dialogue **Gestionnaire de bibliothèque d’aide**, cliquez sur **Choisir l’aide en ligne ou locale**.  
  
   ![HelpLibraryManager_MainPage_ChooseOnlineORLocal.png](../sql-server/media/helplibrarymanager-mainpage-chooseonlineorlocal.png.png)  
3. Cliquez sur **Utiliser l’aide en ligne**, sur **OK**, puis sur **Quitter**.  

   ![HelpLibraryManager_ChooseOnlineORLocalHelp_OnlineHelpSelected_dialog](../sql-server/media/helplibrarymanager-chooseonlineorlocalhelp-onlinehelpselected-dialog.png)

## <a name="f1-help-and-other-tips"></a>Aide F1 et autres conseils

Quand vous appuyez sur la touche F1, la rubrique correspondante s’affiche en ligne. Il n’est pas possible d’afficher la rubrique dans l’aide locale.

Par ailleurs, la visionneuse d’aide ne prend en charge ni les paramètres proxy ni le format ISO. 

## <a name="additional-information"></a>Autres informations
[Microsoft Help Viewer - Visual Studio](/visualstudio/ide/microsoft-help-viewer)  
[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
