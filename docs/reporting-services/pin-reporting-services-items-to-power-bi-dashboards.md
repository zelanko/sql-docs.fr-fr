---
title: Épingler des éléments de rapport paginé à des tableaux de bord Power BI - Reporting Services | Microsoft Docs
ms.date: 01/14/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
description: Vous pouvez épingler des éléments de rapport paginé Reporting Services en local à un tableau de bord dans le service Power BI, sous la forme de nouvelle vignette.
ms.topic: conceptual
helpviewer_keywords:
- pbi
- dashboard
- pin
- powerbi
- power bi integration
ms.assetid: 1d96c3f7-2fd4-40f7-8d1c-14a7f54cdb15
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: da984efa4e0b4d964cf947929094ee7b392063f2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75952478"
---
# <a name="pin-reporting-services-paginated-report-items-to-dashboards-in-power-bi"></a>Épingler des éléments de rapport paginé Reporting Services à des tableaux de bord dans Power BI

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

Vous pouvez épingler un élément de rapport paginé de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] local à un tableau de bord dans le service [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)], sous la forme d’une nouvelle vignette.   Pour que vous puissiez épingler des éléments, il faut que votre administrateur intègre au préalable votre serveur de rapports à Azure Active Directory et [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].  
  
##  <a name="requirements-to-pin"></a><a name="bkmk_requirements_to_pin"></a> Conditions requises pour pouvoir épingler  
  
-   Le serveur de rapports est configuré pour l’intégration de [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] . Pour plus d’informations, consultez [Intégration du serveur de rapports Power BI &#40;Gestionnaire de configuration&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md). Si le serveur de rapports n’a pas été configuré, vous ne voyez pas le bouton **Épingler au tableau de bord Power BI** dans la barre d’outils de la visionneuse de rapports.  
  
     ![Barre d’outils de la visionneuse de rapports](../reporting-services/media/ssrs-report-powerbi.png)  
  
-   Vous épinglez à partir de la visionneuse de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] dans le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], par exemple `https://myserver/Reports`.  Vous ne pouvez pas épingler à partir de [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)], à partir du Concepteur de rapports dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ou à partir d’une URL de serveur de rapports.  Par exemple : `https://myserver/ReportServer`.  
  
-   Vous devez configurer votre navigateur pour autoriser l’affichage des fenêtres contextuelles en provenance du site de votre serveur de rapports.  
  
-   Vous devez configurer les rapports pour les informations d’identification stockées si vous voulez que l’élément épinglé s’actualise.  Quand vous épinglez un élément, un abonnement [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est automatiquement créé pour gérer l’actualisation des données de l’élément sur le tableau de bord.  Si le rapport n’utilise pas d’informations d’identification stockées, une fois l’abonnement actif, la page **Mes abonnements** affiche un message d’erreur similaire à celui-ci.  
  
    « Erreur de livraison Power BI : tableau de bord : Exemple Analyse des dépenses informatiques, élément visuel : Chart2, erreur : Impossible de terminer l’action en cours. Les informations d’identification de la source de données de l’utilisateur ne répondent pas à la configuration requise pour exécuter ce rapport ou ce dataset partagé. Elles ne sont pas stockées dans... »
 
    Consultez la section « Configurer des informations d’identification stockées pour une source de données propre à un rapport (mode natif) » dans [Stocker les informations d’identification dans une source de données Reporting Services](../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md).  
  
##  <a name="items-you-can-pin"></a><a name="bkmk_supported_items"></a> Éléments que vous pouvez épingler  
 Vous pouvez épingler les éléments de rapport suivants à un tableau de bord [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] .  Vous ne pouvez pas épingler des éléments imbriqués à l’intérieur d’une région de données. Par exemple, vous ne pouvez pas épingler un élément imbriqué à l’intérieur d’une table ou d’une liste [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
-   Graphiques  
-   Panneaux de jauge  
-   Cartes  
-   Images  
-   Les éléments doivent se trouver dans le corps du rapport.  Vous ne pouvez pas épingler des éléments figurant dans l’en-tête ou le pied de page.  
-   Vous pouvez épingler des éléments figurant à l’intérieur d’un rectangle de plus haut niveau, mais vous ne pouvez pas les épingler tous comme un seul groupe.  
  
##  <a name="to-pin-a-report-item"></a><a name="bkmk_to_pin"></a> Pour épingler un élément de rapport  
  
1. Vérifiez que vous êtes connecté à [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], sélectionnez l’élément de menu **Mes paramètres** et connectez-vous. Pour plus d'informations, consultez [Mes paramètres pour l’intégration de Power BI &#40;portail web&#41;](my-settings-for-power-bi-integration-web-portal.md).

    ![ssRS_WebPortal_MySettings](../reporting-services/media/ssrs-webportal-mysettings.png)  
  
2. Accédez au dossier du [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] contenant votre rapport, puis affichez le rapport.  
  
3. Une fois le rapport affiché, cliquez sur le bouton **Épingler à Power BI** dans la barre d’outils.  Si vous n’êtes pas connecté, vous êtes invité à le faire.  Si le bouton [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] n’est pas visible, cela signifie que le serveur de rapports n’a pas été intégré à [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Pour plus d’informations, consultez [Intégration du serveur de rapports Power BI &#40;Gestionnaire de configuration&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
    ![ssRS_Report_PowerBI](../reporting-services/media/ssrs-report-powerbi.png)  
  
4. Sélectionnez l’élément de rapport que vous voulez épingler à [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Vous ne pouvez épingler qu’un seul élément à la fois.  La visionneuse de rapports présente un affichage ombré de votre rapport. Les éléments que vous pouvez épingler apparaissent en surbrillance, tandis que ceux que vous ne pouvez pas épingler sont ombrés en foncé.  
  
    **(1)** Sélectionnez le groupe qui contient le tableau de bord sur lequel vous souhaitez épingler l’élément, **(2)** sélectionnez le tableau de bord sur lequel vous souhaitez épingler l’élément et **(3)** sélectionnez la fréquence à laquelle vous voulez que la vignette soit mise à jour sur le tableau de bord.   ![remarque](https://docs.microsoft.com/analysis-services/analysis-services/instances/install-windows/media/ssrs-fyi-note.png "remarque") L’actualisation est gérée par les abonnements [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et, une fois l’élément épinglé, vous pouvez modifier l’abonnement et configurer une autre planification de l’actualisation.  
  
    ![ssRS_Pin_to_PowerBI](../reporting-services/media/ssrs-pin-to-powerbi.png)  
  
5. Sélectionnez **Épingler**.  
  
    Dans la boîte de dialogue **Épinglé avec succès** , vous pouvez sélectionnez le lien **Retrouvez-le ici dans Power BI** pour accéder au tableau de bord et voir l’élément que vous venez d’épingler.  
  
6. Sélectionnez **Fermer** pour revenir à l’affichage normal du rapport.  
  
##  <a name="in-the-dashboard"></a><a name="bkmk_in_the_dashboard"></a> Dans le tableau de bord

Une fois votre élément de rapport épinglé sur le tableau de bord, la vignette ressemble aux autres, rien n’indiquant qu’elle provient de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. La liste suivante récapitule la manière dont les propriétés de vignette sont définies à partir de l’élément de rapport.  
  
Dans le tableau de bord [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] , l’élément de rapport épinglé se comporte comme d’autres vignettes :

**(1)** Vous pouvez épingler la vignette à d’autres tableaux de bord.

**(2)** Dans les **Détails de la vignette**, vous pouvez constater que le titre du rapport [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] est utilisé comme titre par défaut de la vignette.

**(3)** Le sous-titre de la vignette est basé sur les date et heure auxquelles la vignette a été épinglée ou auxquelles les données ont été actualisées pour la dernière fois à partir de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. La planification de l’actualisation est gérée par l’abonnement [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] créé automatiquement lors de l’épinglage de l’élément de rapport.

**(5)** Si vous sélectionnez la vignette elle-même, [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] utilise le **(4) lien personnalisé** pour accéder à la page [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] du serveur de rapports inscrit. Le lien a été défini lors de l’épinglage de l’élément à partir de [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Si vous n’avez pas de connectivité Internet au serveur de rapports, une erreur s’affiche dans le navigateur.  

![ssrs_pinned_tile_details](../reporting-services/media/ssrs-pinned-tile-details.png "ssrs_pinned_tile_details")  
  
##  <a name="troubleshoot-issues"></a><a name="bkmk-troubleshoot"></a> Résoudre les problèmes  
  
-   **Pas de bouton [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] dans la barre d’outils de la visionneuse de rapports :**  Ce message indique que le serveur de rapports n’a pas été intégré à [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. Pour plus d’informations, consultez [Intégration du serveur de rapports Power BI &#40;Gestionnaire de configuration&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md).  
  
- **Impossible d’épingler** : Quand vous tentez d’épingler un élément, le message d’erreur suivant s’affiche : Consultez la section [Éléments que vous pouvez épingler](#bkmk_supported_items).  
  
    « Impossible d’épingler : Cette page ne contient aucun élément de rapport que vous puissiez épingler sur [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]. »  
  
-   **Les éléments épinglés affichent des données caduques** dans un tableau de bord [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] n’ont pas été mises à jour depuis un certain temps.  Le jeton d’informations d’identification de l’utilisateur a expiré et vous devez vous reconnecter.  L’inscription des informations d’identification de l’utilisateur auprès d’Azure et de [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] est valable pendant 90 jours. Dans le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], cliquez sur **Mes paramètres**. Pour plus d’informations, consultez [Mes paramètres pour l’intégration de Power BI &#40;portail web&#41;](my-settings-for-power-bi-integration-web-portal.md).  
  
-   **Les éléments épinglés affichent des données caduques** dans un tableau de bord [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] et elle n’ont jamais été actualisées.  Le problème est que le rapport n’est pas configuré pour utiliser des informations d’identification stockées. Un rapport doit utiliser des informations d’identification stockées, car l’action d’épinglage d’un élément de rapport crée un abonnement [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour gérer la planification de l’actualisation des vignettes. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] nécessitent des informations d’identification stockées. La page **Mes abonnements** affiche une message d’erreur similaire à celui-ci :  
  
    « Erreur de livraison Power BI : tableau de bord : Éléments SSRS, visuel : Image3, erreur : Impossible de terminer l’action en cours. Les informations d’identification de la source de données de l’utilisateur ne répondent pas à la configuration requise pour exécuter ce rapport ou ce dataset partagé. Elles ne sont pas stockées dans la base de données du serveur de rapports ou la source de données de l’utilisateur est configurée pour ne pas exiger d’informations d’identification, mais le compte d’exécution sans assistance n’est pas spécifié. (rsInvalidDataSourceCredentialSetting) »
  
-   **Informations d’identification Power BI expirées :**  Vous tentez d’épingler un élément et vous voyez le message d’erreur suivant. Dans le [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)], cliquez sur **Mes paramètres** , puis, dans la page Mes paramètres, cliquez sur **Se connecter**. Pour plus d'informations, consultez [Mes paramètres pour l’intégration de Power BI &#40;portail web&#41;](my-settings-for-power-bi-integration-web-portal.md).  
  
    « Impossible d’épingler : Erreur serveur inattendue : Informations d'identification Power BI manquantes, non valides ou expirées. »  
  
-   **Impossible d’épingler** : Si vous tentez d’épingler un élément à un tableau de bord qui est en lecture seule, vous voyez un message d’erreur similaire à celui-ci :  
  
    « Erreur de serveur : L’élément « Tableau de bord supprimé 015cf022-8e2f-462e-88e5-75ab0a04c4d0 » est introuvable. (rsItemNotFound) »  

-   **Les vignettes dans les applications Power BI affichent des données obsolètes :** Si vous épinglez un élément de rapport Reporting Services à un tableau de bord, puis que vous distribuez celui-ci dans une application, l’élément de rapport épinglé dans ce tableau de bord ne sera pas mis à jour. 

##  <a name="subscription-management"></a><a name="bkmk_subscription_management"></a> Gestion des abonnements  
 En plus des problèmes d’abonnement décrits dans la section de dépannage, les informations suivantes vous aideront à gérer les abonnements liés à [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)].
  
-   **Nom de l’élément modifié :** Si un élément de rapport épinglé est renommé ou supprimé, la vignette [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] n’est plus mise à jour et vous voyez un message d’erreur similaire au suivant.  Si vous rétablissez le nom d’origine de l’élément, l’abonnement opère à nouveau et la vignette s’actualise conformément à la planification de celui-ci.  
  
    « Erreur de livraison Power BI : tableau de bord : Éléments SSRS, visuel : Image1, erreur : Erreur : L’élément de rapport 'Image1' est introuvable. »  
  
    Vous pouvez également modifier les propriétés de l’abonnement et remplacer le **Nom de l’élément visuel du rapport** par le nom d’élément de rapport approprié. ![modifier le visuel utilisé pour l’actualisation de Power BI](../reporting-services/media/ssrs-powerbi-subscription-visual.png "modifier le visuel utilisé pour l’actualisation de Power BI")  
  
-   **Supprimer une vignette**. Si vous supprimez une vignette dans [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)], l’abonnement associé n’est pas supprimé dans [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] et dans la page **Mes abonnements**. Un message d’erreur similaire au suivant s’affiche. Vous pouvez supprimer l’abonnement  
  
    « Erreur de livraison Power BI : tableau de bord : Éléments SSRS, visuel : Image3, erreur : L’élément 'Vignette supprimée af7131d9-5eaf-480f-ba45-943a07d19c9f' est introuvable. »  

## <a name="video"></a>Vidéo

<iframe width="560" height="315" src="https://www.youtube.com/embed/QhPQObqmMPc" frameborder="0" allowfullscreen></iframe>

## <a name="see-also"></a>Voir aussi  
 [Intégration du serveur de rapports Power BI &#40;Gestionnaire de configuration&#41;](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md)   
 [Mes paramètres pour l’intégration de Power BI &#40;portail web&#41;](my-settings-for-power-bi-integration-web-portal.md)  
 [Tableaux de bord dans Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  
  
  
[!INCLUDE[feedback_stackoverflow_msdn_connect_md](../includes/feedback-stackoverflow-msdn-connect-md.md)]

