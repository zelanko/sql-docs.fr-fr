---
title: Ajouter des Types de contenu de serveur de rapports à une bibliothèque (Reporting Services en Mode intégré SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: ac9136c8-9ef4-484c-8e9d-05008a186db5
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 50ff2626108c26ca5cee3845da437b27dbfcade0
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56030850"
---
# <a name="add-report-server-content-types-to-a-library-reporting-services-in-sharepoint-integrated-mode"></a>Ajouter des types de contenu de serveur de rapports à une bibliothèque (Reporting Services en mode intégré SharePoint)
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] fournit des types de contenu prédéfinis SharePoint qui sont utilisés pour gérer les fichiers de sources de données partagées (.rsds), les modèles de rapports (.smdl) et les fichiers de définitions de rapports (.rdl) du Générateur de rapports. L'ajout à une bibliothèque des types de contenu **Rapport du Générateur de rapports**, **Modèle de rapport**et **Source de données du rapport** active la commande **Nouveau** , qui permet de créer de nouveaux documents de ce type.  
  
 **[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode SharePoint  
  
 Pour ajouter des types de contenu à une bibliothèque, vous devez être administrateur de site ou bénéficier du niveau d'autorisation Contrôle total.  
  
 Les types de contenu et la gestion des types de contenu [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] seront automatiquement activés dans toutes les bibliothèques de documents pour les collections de sites existantes créées à partir du modèle de site **Business Intelligence Center** suivant :  
  
 Les sites créés après l'intégration de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] n'auront pas les types de contenu [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] activés.  
  
> [!TIP]  
>  Si vous **n'avez pas** configuré au préalable les types de contenus d'une bibliothèque, commencez par activer la gestion des types de contenu, puis activez les types de contenu [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Reportez-vous aux procédures d'activation de la gestion de type de contenu dans une seule bibliothèque de documents.  
  
 **Courte vidéo :** [(SSRS) L’activation de Content Types in SharePoint2010.wmv](http://www.youtube.com/watch?v=yqhm3DrtT1w) (http://www.youtube.com/watch?v=yqhm3DrtT1w).  
  
 **Dans cette rubrique :**  
  
-   [Activer les types de contenu dans toutes les bibliothèques de documents dans un BI center existant](#bkmk_enable_all)  
  
-   [Pour activer la gestion des types de contenu pour une bibliothèque de documents (SharePoint 2013)](#bkmk_enable_content_management)  
  
-   [Pour ajouter des types de contenu Reporting Services (SharePoint 2013)](#bkmk_add_single)  
  
-   [Pour activer la gestion des types de contenu pour une bibliothèque de documents (SharePoint 2010)](#bkmk_enable_content_management_2010)  
  
-   [Pour ajouter des types de contenu de serveur de rapports (SharePoint 2010)](#bkmk_add_single_2010)  
  
-   [Pour activer les types de contenu et la gestion du contenu pour plusieurs sites BI](#bkmk_enable_multiple_sites)  
  
##  <a name="bkmk_enable_all"></a> Activer les types de contenu dans toutes les bibliothèques de documents dans un BI center existant  
  
1.  Pour activer les types de contenu et la gestion du contenu dans toutes les bibliothèques de documents dans un site **Business Intelligence Center** existant, utilisez la fonction d'intégration [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
2.  Allez à **Paramètres du site**.  
  
    -   Dans SharePoint 2013, cliquez sur l'icône **Paramètres** . ![Paramètres SharePoint](../analysis-services/media/as-sharepoint2013-settings-gear.gif "Paramètres SharePoint")  
  
    -   Dans SharePoint 2010, cliquez sur **Actions du site**, puis sur **Paramètre du site**.  
  
3.  Cliquez sur **Fonctionnalités de la collection de sites**.  
  
4.  Recherchez **Fonctionnalité d'intégration Report Server** dans la liste et cliquez sur **Désactiver**.  
  
     ![rs_reportserver_integration_active](media/rs-reportserver-integration-active.gif "rs_reportserver_integration_active")  
  
5.  Actualisez le navigateur, puis cliquez sur **Activer** pour la **Fonctionnalité d'intégration Report Server**.  
  
    ![Deactivate](media/rs-reportserver-integration-deactivate.gif "rs_reportserver_integration_deactive")  
  
##  <a name="bkmk_enable_content_management"></a> Pour activer la gestion des types de contenu pour une bibliothèque de documents (SharePoint 2013)  
  
1.  Ouvrez la bibliothèque pour laquelle activer plusieurs types de contenu.  
  
2.  Dans le ruban, cliquez sur **Bibliothèque** .  
  
     ![rs_SharePoint2013_LibraryRibbon](media/rs-sharepoint2013-libraryribbon.gif "rs_SharePoint2013_LibraryRibbon")  
  
3.  Dans le ruban **Bibliothèque** , cliquez sur **Paramètres de la bibliothèque**. Si **Paramètres de la bibliothèque** n'est pas visible, ou si le bouton est désactivé, vous n'êtes pas autorisé à configurer les paramètres de la bibliothèque, ni les types de contenu.  
  
     ![rs_SharePoint2013_LibrarySettings](media/rs-sharepoint2013-librarysettings.gif "rs_SharePoint2013_LibrarySettings")  
  
4.  Dans la section **Paramètres généraux** , cliquez sur **Paramètres avancés**.  
  
     ![rs_SharePoint2013_LibrarySettings_AdvancedSettings](media/rs-sharepoint2013-librarysettings-advancedsettings.gif "rs_SharePoint2013_LibrarySettings_AdvancedSettings")  
  
5.  Dans la section **Types de contenu** , sélectionnez **Oui** pour autoriser la gestion des types de contenu.  
  
6.  Cliquez sur **OK**.  
  
##  <a name="bkmk_add_single"></a> Pour ajouter des types de contenu Reporting Services (SharePoint 2013)  
  
1.  Ouvrez la bibliothèque pour laquelle vous voulez ajouter des types de contenu Reporting Services.  
  
2.  Dans le ruban, cliquez sur **Bibliothèque**.  
  
3.  Cliquez sur **Paramètres de la bibliothèque**.  
  
4.  Sous **Types de contenu**, cliquez sur **Ajouter à partir de types de contenu de site existants**.  
  
5.  Dans **Sélectionner des types de contenu dans**, sélectionnez **Types de contenu SQL Server Reporting Services**.  
  
6.  Dans la liste **Types de contenu de site disponibles** , cliquez sur **Générateur de rapports**, puis sur **Ajouter** pour déplacer le type de contenu sélectionné dans la liste **Type de contenu à ajouter** .  
  
7.  Pour ajouter les types de contenu **Modèle de rapport** et **Source de données du rapport** , répétez l'étape précédente.  
  
8.  Lorsque vous avez terminé d'ajouter les types de contenu, cliquez sur **OK**.  
  
9. > [!NOTE]  
    >  Si le groupe de types de contenu [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] **Types de contenu SQL Server Reporting Services** n’est pas visible dans la page **Ajouter des types de contenu** , l’une des conditions suivantes est remplie :  
  
    -   Le complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour les produits SharePoint n'est pas installé. Pour plus d’informations, consultez [installer ou désinstaller le logiciel complément Reporting Services pour SharePoint &#40;SharePoint 2010 et SharePoint 2013&#41;](install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md). Cette rubrique contient des informations sur l'installation du complément et les étapes de l'installation uniquement des fichiers du complément afin de contourner les problèmes.  
  
    -   Le complément est installé, mais la fonctionnalité de collection de sites **Fonctionnalité d’intégration du serveur de rapports** n’est pas active. Vérifiez la fonctionnalité de collection de sites dans **Paramètres du site**.  
  
    -   Tous les types de contenu [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ont déjà été ajoutés à la bibliothèque. Si tous les types de contenu font partie de la bibliothèque, alors le groupe est supprimé de la page **Ajouter des types de contenu** . Si vous supprimez un ou plusieurs types de contenu [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] , alors le groupe **Types de contenu SQL Server Reporting Services** est visible sur la page **Ajouter des types de contenu** .  
  
##  <a name="bkmk_enable_content_management_2010"></a> Pour activer la gestion des types de contenu pour une bibliothèque de documents (SharePoint 2010)  
  
1.  Ouvrez la bibliothèque pour laquelle activer plusieurs types de contenu. Dans la barre de menus de la bibliothèque, vous devez voir les menus suivantes : **Nouvelle**, **télécharger**, **Actions**, et **paramètres**. Si le menu **Paramètres**n'est pas visible, vous n'êtes pas autorisé à ajouter un type de contenu.  
  
2.  Dans le ruban **Outils de bibliothèque** , cliquez sur **Bibliothèque**.  
  
     ![rs_SharePoint2010_LibraryRibbon](media/rs-sharepoint2010-libraryribbon.gif "rs_SharePoint2010_LibraryRibbon")  
  
3.  Dans le groupe du ruban **Paramètres** , cliquez sur **Paramètres de la bibliothèque**.  
  
4.  Sous **Paramètres généraux**, cliquez sur **Paramètres avancés**.  
  
5.  Dans la section **Types de contenu** , sélectionnez **Oui** pour autoriser la gestion des types de contenu.  
  
6.  Cliquez sur **OK**.  
  
##  <a name="bkmk_add_single_2010"></a> Pour ajouter des types de contenu de serveur de rapports (SharePoint 2010)  
  
1.  Ouvrez la bibliothèque pour laquelle vous voulez ajouter des types de contenu Reporting Services.  
  
2.  Sous les onglets du ruban **Outils de bibliothèque** , cliquez sur l'onglet **Bibliothèque**.  
  
3.  Dans le groupe du ruban **Paramètres** , cliquez sur **Paramètres de la bibliothèque**.  
  
4.  Sous **Types de contenu**, cliquez sur **Ajouter à partir de types de contenu de site existants**.  
  
5.  Dans la section **Sélectionner des types de contenu** , dans **Sélectionner des types de contenu dans**, cliquez sur la flèche pour sélectionner **Types de contenu SQL Server Reporting Services**.  
  
6.  Dans la liste **Types de contenu de site disponibles** , cliquez sur **Générateur de rapports**, puis sur **Ajouter** pour déplacer le type de contenu sélectionné dans la liste **Type de contenu à ajouter** .  
  
7.  Pour ajouter les types de contenu **Modèle de rapport** et **Source de données du rapport** , répétez l'étape précédente.  
  
8.  Lorsque vous avez terminé d'ajouter les types de contenu, cliquez sur **OK**.  
  
##  <a name="bkmk_enable_multiple_sites"></a> Pour activer les types de contenu et la gestion du contenu pour plusieurs sites BI  
  
1.  Pour les serveurs de rapports SQL Server Reporting Services 2008 et 2008 R2, vous pouvez activer les types de contenu et la gestion du contenu pour plusieurs sites Business Intelligence Center :  
  
2.  Dans Administration centrale de SharePoint, cliquez sur **Paramètres généraux de l'application**. Dans la section **SQL Server Reporting Services (2008 et 2008 R2)** , cliquez sur **Intégration de Reporting Services**.  
  
     ![rs_general_app_settings](media/rs-general-app-settings.gif "rs_general_app_settings")  
  
3.  Cliquez sur **Activer la fonctionnalité dans toutes les collections de sites existantes**.  
  
     ![rs_general_app_settings_old_integrations](media/rs-general-app-settings-old-integrations.gif "rs_general_app_settings_old_integrations")  
  
4.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Article de référence sur les autorisations de site SharePoint et de listes pour les éléments de serveur de rapports](security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)   
 [Démarrer le Générateur de &#40;Générateur de rapports&#41;](report-builder/start-report-builder.md)  
  
  
