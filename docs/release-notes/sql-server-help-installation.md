---
title: "Visionneuse d’aide pour SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 02/15/2017
ms.prod: sql-non-specified
ms.technology: server-general
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2014
- SQL Server 2016
ms.assetid: 51f8a08c-51d0-41d8-8bc5-1cb4d42622fb
caps.latest.revision: 8
author: sabotta
ms.author: carlasab
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fc2435ccea3b01328c3c4623e62fbf12ee53e400
ms.lasthandoff: 04/11/2017

---
# <a name="help-viewer-for-sql-server"></a>Visionneuse d’aide pour SQL Server
  
  
  
Cet article vous explique en détail comment installer l’aide locale et comment afficher l’aide en ligne et locale. Cet article porte sur les versions 1.1 et 2.2 de la visionneuse d’aide Microsoft et inclut la documentation pour [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] et [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)]. 

>[!IMPORTANT]
>La visionneuse d’aide ne prend en charge ni les paramètres proxy ni le format ISO.  

>**Touche F1 et aide**
>>Quand vous appuyez sur la touche F1, la rubrique correspondante s’affiche en ligne. Il n’est pas possible d’afficher la rubrique dans l’aide locale.

## <a name="includesscurrentmdincludessscurrent-mdmd-and-help-viewer-22"></a>[!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] et la visionneuse d’aide version 2.2  
La visionneuse d’aide version 2.2 est disponible dans [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] Management Studio à compter de la préversion d’avril 2016 (13.0.12500.29) et dans Visual Studio 2015.  

> [![Télécharger SSMS](../release-notes/media/download.png)](https://msdn.microsoft.com/library/mt238290.aspx) **[Télécharger la dernière version de SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx)**  

**Pour installer l’aide locale à utiliser avec la visionneuse d’aide version 2.2**  
1. Ouvrez la visionneuse d’aide version 2.2 en lançant SQL Server Management Studio ou Visual Studio, puis en cliquant sur **Ajouter et supprimer le contenu d’aide** dans le menu **Aide**.  
2. Cliquez sur l’onglet **Gérer le contenu**.  
3. Pour installer l’aide à partir d’une source en ligne, cliquez sur **En ligne** dans la zone **Source d’installation**.  
![HelpViewer2_ManageContent_OnlineSource](../release-notes/media/helpviewer2-managecontent-onlinesource.png)  
7. Cliquez sur **Ajouter** en regard de la documentation que vous voulez installer, puis cliquez sur **Mettre à jour**.  
![HelpViewer2_ManageContent_AddContent](../release-notes/media/helpviewer2-managecontent-addcontent.png)     
  
   >[!IMPORTANT] 
   >Dans SQL Server Management Studio et Visual Studio, l’application Visionneuse d’aide peut se figer (se bloquer) pendant l’ajout de la documentation. Pour résoudre ce problème, procédez comme indiqué ci-dessous. Pour plus d’informations sur ce problème, consultez [La visionneuse d’aide Visual Studio se fige sur l’écran de démarrage](https://msdn.microsoft.com/library/mt654096.aspx).  
   >>Ouvrez le fichier %LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio14_en-US.settings dans le Bloc-notes et remplacez la date dans le code ci-dessous par une date future. Ce fichier n’est disponible sur votre ordinateur local qu’à partir du moment où vous avez installé Visual Studio. 
   >>>Dernière actualisation du cache = « 31/12/2017 00:00:00 »  
  
    La table des matières figurant dans le volet gauche se met automatiquement à jour pour inclure la documentation que vous avez ajoutée.  
![HelpViewer2_withContentInstalled](../release-notes/media/helpviewer2-withcontentinstalled.png)

1. (Facultatif) La zone **Chemin d’accès au stockage local** sous l’onglet **Gérer le contenu** indique l’emplacement où est installée la documentation sur l’ordinateur local. Pour déplacer la documentation vers un autre emplacement, cliquez sur **Déplacer**, entrez un chemin de dossier dans le champ **Vers** de la boîte de dialogue **Déplacer le contenu**, puis cliquez sur **OK**.

   ![HelpViewer2_Move Content Dialog](../release-notes/media/helpviewer2-move-content-dialog.png)

   Une fois que le contenu est déplacé, le nouvel emplacement s’affiche dans **Chemin d’accès au stockage local**.
      
   >[!IMPORTANT]
   > Si un message s’affiche indiquant que l’opération de déplacement a échoué, fermez la boîte de message, puis fermez et rouvrez la visionneuse d’aide. Le nouvel emplacement du contenu doit à présent figurer dans **Chemin d’accès au stockage local**.   
  
**Pour afficher l’aide locale ou l’aide en ligne dans SQL Server Management Studio**  
* Pour afficher l’aide locale, cliquez sur **Ajouter et supprimer le contenu d’aide** dans le menu **Aide**, puis cliquez sur l’onglet **Accueil Visionneuse d’aide** pour afficher la documentation.  
    >[!NOTE]
    >Le texte **Accueil Visionneuse d’aide** change en fonction de la rubrique sur laquelle vous avez cliqué dans la table des matières.   
* Pour afficher l’aide en ligne, cliquez sur **Afficher l’aide** dans le menu **Aide**. La documentation s’affiche dans un navigateur.  
![HelpViewer2_SSMS_ChooseOnlineORLocalHelp](../release-notes/media/helpviewer2-ssms-chooseonlineorlocalhelp.png)  
  
  
**Pour afficher l’aide locale ou l’aide en ligne dans Visual Studio**  
* Cliquez sur **Définir les préférences pour l’aide** dans le menu **Aide**, puis effectuez l’une des opérations suivantes.  
   * Cliquez sur **Lancer dans le navigateur** pour afficher l’aide en ligne. Quand vous cliquez sur **Afficher l’aide** dans le menu **Aide**, la documentation s’affiche dans un navigateur.  
   * Cliquez sur **Lancer dans la visionneuse d’aide** pour afficher l’aide locale. Quand vous cliquez sur **Afficher l’aide** dans le menu **Aide**, la documentation s’affiche dans la visionneuse d’aide.  
     
     ![HelpViewer2_VisualStudio_ChooseOnlineORLocalHelp](../release-notes/media/helpviewer2-visualstudio-chooseonlineorlocalhelp.png)  
  
  
## <a name="includesssql14mdincludessssql14-mdmd-and-help-viewer-11"></a>[!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] et la visionneuse d’aide version 1.1  
 La visionneuse d’aide version 1.1 est disponible dans [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] Management Studio et les versions de Visual Studio antérieures à Visual Studio 2012.   
 
>[!NOTE]
> Vous pouvez aussi afficher l’aide locale de [!INCLUDE[ssSQL14_md](../includes/sssql14-md.md)] avec la visionneuse d’aide version 2.2 à la seule condition de choisir l’option **Installer du contenu à partir du disque**. La visionneuse d’aide version 2.2 est disponible dans [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] Management Studio à compter de la préversion d’avril 2016 (13.0.12500.29) et dans Visual Studio 2015. 
   
**Pour installer l’aide locale à utiliser avec la visionneuse d’aide version 1.1**  
1. Accédez au [site de téléchargement](https://www.microsoft.com/en-us/download/details.aspx?id=42557) du contenu d’aide, puis cliquez sur **Télécharger**.  
2. Cliquez sur **Enregistrer** dans la boîte de message pour enregistrer le fichier SQLServer2014Documentation_*.exe sur votre ordinateur.  
   >[!NOTE]
   >Pour les environnements protégés par un pare-feu et un proxy, enregistrez le fichier téléchargé sur un lecteur USB ou tout autre média amovible pouvant être amené dans l’environnement.   
3. Double-cliquez sur le fichier .exe pour décompresser le fichier de contenu d’aide, puis enregistrez le fichier dans un dossier local ou partagé.  
4. Ouvrez le **Gestionnaire de bibliothèque d’aide** en lançant SQL Server Management Studio ou Visual Studio, puis en cliquant sur **Gérer les paramètres de l’aide** dans le menu **Aide**.  
7. Cliquez sur **Installer du contenu à partir du disque** et accédez au dossier dans lequel vous avez décompressé le fichier de contenu d’aide.  
  
Sélectionnez Installer du contenu à partir du disque  |Accédez au fichier de contenu d’aide   
---------|---------  
![HelpLibraryManager_MainPage_InstallFromDisk](../release-notes/media/helplibrarymanager-mainpage-installfromdisk.png)    | ![HelpLibraryManager_InstallContentFromDisk_dialog1](../release-notes/media/helplibrarymanager-installcontentfromdisk-dialog1.png)          
  
>[!IMPORTANT]
> Pour éviter d’installer du contenu d’aide locale qui ne présente qu’une table des matières partielle, utilisez l’option **Installer du contenu à partir du disque** dans le **Gestionnaire de bibliothèque d’aide**.  
>>Si vous avez utilisé l’option **Installer du contenu à partir d’une source en ligne** et que la visionneuse d’aide affiche une table des matières partielle, consultez ce [billet de blog](https://blogs.msdn.microsoft.com/womeninanalytics/2016/06/21/troubleshoot-local-help-for-sql-server-2014/) pour savoir comment résoudre ce problème. 

8. Cliquez successivement sur le fichier HelpContentSetup.msha, sur **Ouvrir**, puis sur **Suivant**.  
9. Cliquez sur **Ajouter** en regard de la documentation que vous voulez installer, puis cliquez sur **Mettre à jour**.  
  
   ![HelpLibraryManager_InstallContentFromDisk_dialog2](../release-notes/media/helplibrarymanager-installcontentfromdisk-dialog2.png)  
10. Cliquez sur **Terminer**, sur **Quitter**, puis ouvrez la visionneuse d’aide pour afficher le contenu en cliquant sur **Afficher l’aide** dans le menu **Aide**. Le contenu que vous avez installé doit figurer dans la table des matières, dans le volet gauche.  
  
    ![HelpViewer1_withContentInstalled_ZoomedIn](../release-notes/media/helpviewer1-withcontentinstalled-zoomedin.png)  
  
**Pour afficher l’aide locale ou l’aide en ligne**  
1. Ouvrez le **Gestionnaire de bibliothèque d’aide** en cliquant sur **Gérer les paramètres de l’aide** dans le menu **Aide**.  
2. Dans la boîte de dialogue **Gestionnaire de bibliothèque d’aide**, cliquez sur **Choisir l’aide en ligne ou locale**.  
  
   ![HelpLibraryManager_MainPage_ChooseOnlineORLocal.png](../release-notes/media/helplibrarymanager-mainpage-chooseonlineorlocal.png.png)  
3. Effectuez l’une des opérations suivantes, puis cliquez sur **OK**, puis sur **Quitter**.  
   * Cliquez sur **Utiliser l’aide en ligne**.  
   * Cliquez sur **Utiliser l’aide locale**.  
  
   ![HelpLibraryManager_ChooseOnlineORLocalHelp_OnlineHelpSelected_dialog](../release-notes/media/helplibrarymanager-chooseonlineorlocalhelp-onlinehelpselected-dialog.png)  
  
Si vous avez choisi d’utiliser l’aide en ligne, quand vous cliquez sur **Afficher l’aide** dans le menu **Aide**, le navigateur démarre et affiche l’article [Documentation en ligne de SQL Server 2014](https://msdn.microsoft.com/library/ms130214(v=sql.120).aspx) sur MSDN. Si vous avez choisi d’utiliser l’aide locale, quand vous cliquez sur **Afficher l’aide**, la visionneuse d’aide démarre.  

## <a name="additional-information"></a>Autres informations
[Visionneuse d’aide Microsoft - Visual Studio 2015](https://msdn.microsoft.com/library/hh580782.aspx)

