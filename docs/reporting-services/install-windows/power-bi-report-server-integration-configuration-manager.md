---
description: Intégration du serveur de rapports Power BI (Gestionnaire de configuration)
title: Intégration de Power BI Report Server (Gestionnaire de configuration) | Microsoft Docs
author: maggiesMSFT
ms.author: maggies
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
ms.date: 09/17/2017
ms.openlocfilehash: 47964ebf5702542452227589e1426948825cc216
ms.sourcegitcommit: 22e97435c8b692f7612c4a6d3fe9e9baeaecbb94
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92678875"
---
# <a name="power-bi-report-server-integration-configuration-manager"></a>Intégration du serveur de rapports Power BI (Gestionnaire de configuration)

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

La page  **Intégration de Power BI** du Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sert à inscrire le serveur de rapports auprès du client géré Azure Active Directory (AD) souhaité pour permettre aux utilisateurs du serveur de rapports d’épingler les éléments de rapports pris en charge à des tableaux de bord [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] . Pour obtenir la liste des éléments pris en charge que vous pouvez épingler, consultez [Épingler des éléments Reporting Services aux tableaux de bord Power BI](../../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md).

## <a name="requirements-for-power-bi-integration"></a><a name="bkmk_requirements"></a> Configuration requise pour l’intégration de Power BI

Outre une connexion Internet active pour pouvoir accéder au service [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] , voici la configuration requise pour effectuer l’intégration [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)].

- **Azure Active Directory :** votre organisation doit utiliser Azure Active Directory, qui fournit la gestion des annuaires et des identités pour les services et applications web Azure. Pour plus d’informations, consultez [Qu’est-ce qu’Azure Active Directory ?](/azure/active-directory/fundamentals/active-directory-whatis)

- **Client géré :** le tableau de bord [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] auquel vous voulez épingler des éléments de rapport doit faire partie d’un client géré Azure AD.  Un client managé est créé automatiquement la première fois que votre organisation s’abonne à des services Azure tels que Microsoft 365 et Microsoft Intune.   Les clients viraux ne sont pas pris en charge pour le moment.  Pour plus d’informations, consultez les sections « Qu’est-ce qu’un client Azure AD ?» et « Obtention d’un annuaire Azure AD » de la rubrique [Qu’est-ce qu’un annuaire Azure AD ?](/previous-versions/azure/azure-services/jj573650(v=azure.100)#BKMK_WhatIsAnAzureADTenant)

- L’intégration de [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] doit être effectuée par un utilisateur membre du client Azure AD, un administrateur système [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et un administrateur système pour la base de données de catalogues ReportServer.

- L’utilisateur effectuant l’intégration de [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] doit démarrer le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] avec le compte utilisé pour installer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ou le compte avec lequel fonctionne le service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]

- Les rapports dont vous voulez épingler des éléments doivent utiliser des informations d’identification stockées. Ce n’est pas une exigence pour l’intégration de [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] en soi, mais pour le processus d’actualisation des éléments épinglés.  L’action d’épingler un élément de rapport crée un abonnement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour gérer la planification de l’actualisation des vignettes dans [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)]. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nécessitent des informations d’identification stockées. Si un rapport n’utilise pas des informations d’identification stockées, un utilisateur peut toujours épingler des éléments de rapport, mais un message d’erreur similaire à celui ci-dessous apparaît dans la page [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)]Mes abonnements **lorsque l’abonnement associé tente d’actualiser les données dans** .

    PowerBI Delivery error: dashboard: IT Spend Analysis Sample, visual: Chart2, error: Impossible de terminer l’action en cours. Les informations d’identification de la source de données de l’utilisateur ne répondent pas à la configuration requise pour exécuter ce rapport ou ce dataset partagé. Les informations d’identification de la source de données de l’utilisateur.

Pour en savoir plus sur le stockage d’informations d’identification, consultez la section « Configurer des informations d’identification stockées pour une source de données propre à un rapport » dans [Stocker les informations d’identification dans une source de données Reporting Services](../../reporting-services/report-data/store-credentials-in-a-reporting-services-data-source.md).

Un administrateur peut consulter les fichiers de journaux  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour plus d’informations.  Il y trouvera des messages semblables au suivant : Pour consulter et surveiller les fichiers journaux [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vous pouvez utiliser [!INCLUDE[msCoName](../../includes/msconame-md.md)] Power Query sur les fichiers.  Pour en savoir plus et visionner une courte vidéo, consultez [Report Server Service Trace Log](../../reporting-services/report-server/report-server-service-trace-log.md).

- subscription!WindowsService_1!1458!09/24/2015-00:09:27:: e ERROR: Erreur de remise Power BI : tableau de bord : IT Spend Analysis Sample, élément visuel : Chart2, erreur : Impossible de terminer l’action en cours. Les informations d’identification de la source de données de l’utilisateur ne répondent pas à la configuration requise pour exécuter ce rapport ou ce dataset partagé. Elles ne sont pas stockées dans la base de données du serveur de rapports ou la source de données de l’utilisateur est configurée pour ne pas exiger d’informations d’identification, mais le compte d’exécution sans assistance n’est pas spécifié.

- notification!WindowsService_1!1458!09/24/2015-00:09:27:: e ERROR: Une erreur s’est produite lors du traitement de l’abonnement fcdb8581-d763-4b3b-ba3e-8572360df4f9 : Erreur de remise Power BI : tableau de bord : IT Spend Analysis Sample, élément visuel : Chart2, erreur : Impossible de terminer l’action en cours. Les informations d’identification de la source de données de l’utilisateur ne répondent pas à la configuration requise pour exécuter ce rapport ou dataset partagé. Elles ne sont pas stockées dans la base de données du serveur de rapports ou la source de données de l’utilisateur est configurée pour ne pas exiger d’informations d’identification, mais le compte d’exécution sans assistance n’est pas spécifié.

## <a name="to-integrate-and-register-the-report-server"></a><a name="bkmk_steps2integrate"></a> Pour intégrer et inscrire le serveur de rapports

Exécutez la procédure suivante dans le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour plus d’informations, consultez [Gestionnaire de configuration du serveur de rapports](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).

1. Sélectionnez la page d’intégration de [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] .

2. Sélectionnez **S’inscrire auprès de Power BI** .

    >[!Note]
    > Assurez-vous que le port 443 n’est pas bloqué.

3. Dans la boîte de dialogue de connexion de [!INCLUDE[msCoName](../../includes/msconame-md.md)] , entrez les informations d’identification que vous utilisez pour vous connecter à [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)].

4. Une fois l’inscription terminée, la section **Détails de l’inscription auprès de Power BI** présente l’ID de client Azure et les URL de redirection.  Les URL sont utilisées dans le cadre du processus de connexion et de communication pour permettre au tableau de bord [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] de répondre au serveur de rapports inscrit.

5. Cliquez sur le bouton **Copier** dans la fenêtre **Résultats** pour copier les détails de l’inscription dans le Presse-papiers Windows afin de les conserver pour référence ultérieure.

## <a name="unregister-with-power-bi"></a><a name="bkmk_unregister"></a> Se désinscrire de Power BI

**Se désinscrire :** la désinscription du serveur de rapports d’Azure Active Directory a les conséquences suivantes :

- Le lien **Mes paramètres** n’est plus visible dans la barre de menus du portail web.

- Les éléments de rapport déjà épinglés à des tableaux de bord sont conservés, mais les vignettes ne sont plus mises à jour sur le tableau de bord.

- Les abonnements [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui mettaient à jour les vignettes figurent toujours sur le serveur de rapports, mais un message d’erreur similaire à celui ci-dessous apparaît lors de l’exécution de leur planification configurée.

    **Impossible de charger l’extension de remise pour cet abonnement.**

Dans la page **Power BI** du Gestionnaire de configuration, cliquez sur le bouton **Se désinscrire de Power BI** .

##  <a name="update-registration"></a><a name="bkmk_updateregistration"></a> Mettre à jour l’inscription

Utilisez l’option **Mettre à jour l’inscription** si la configuration de votre serveur de rapports est modifiée. Par exemple, si vous voulez ajouter ou supprimer les URL que vos utilisateurs emploient pour accéder au [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)].

- Dans le Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , sélectionnez l’ **URL du portail web** .

     Sélectionnez **Avancé** .

- Sélectionnez **Ajouter** pour ajouter une nouvelle identité HTTP pour le [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] , puis sélectionnez **OK** .

     L’icône [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] change pour indiquer que la configuration du serveur a été modifiée.  ![ssrs_powebi_icon_warning](../../reporting-services/install-windows/media/ssrs-powebi-icon-warning.png "ssrs_powebi_icon_warning")

- Dans la page **Intégration de Power BI** , sélectionnez **Mettre à jour l’inscription** .

     Vous êtes invité à vous connecter à Azure AD. La page est actualisée et la nouvelle URL apparaît dans la liste **URL de redirection** .

##  <a name="summary-of-the-power-bi-integration-and-pin-process"></a><a name="bkmk_integration_process"></a> Résumé de l’intégration de Power BI et du processus d’épinglage

Cette section présente les étapes de base et les technologies impliquées dans l’intégration de votre serveur de rapports à [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] et l’épinglage d’un élément de rapport à un tableau de bord.

 **Intégration :**

1. Dans le Gestionnaire de configuration, lorsque vous cliquez sur le bouton **Inscrire sur Power BI** , vous êtes invité à vous connecter à Azure Active Directory.

2. L’application cliente [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] est inscrite auprès de votre client géré.

3. Votre client géré dans Azure Active Directory se trouve là où l’application cliente Power BI est créée.

4. L’inscription comprend une ou plusieurs URL de redirection utilisées en cas de connexion depuis le serveur de rapports.  L’ID d’application et les URL sont enregistrés dans la base de données ReportServer. L’URL de redirection est utilisée lors des appels d’authentification à Azure de sorte que l’appel puisse répondre au serveur de rapports. Par exemple, lorsque les utilisateurs se connectent ou épinglent des éléments à un tableau de bord.

5. L’ID d’application et les URL sont affichés dans le Gestionnaire de configuration.

 ![ssrs_pbiflow_integration](../../reporting-services/install-windows/media/ssrs-pbiflow-integration.png "ssrs_pbiflow_integration")

 **Lorsqu’un utilisateur épingle un élément de rapport à un tableau de bord :**

1. Les utilisateurs prévisualisent les rapports dans le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] la première fois qu’ils cliquent pour épingler un élément de rapport dans le [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)].

2. Ils sont redirigés vers la page de connexion Azure AD. Ils peuvent également se connecter à partir de la page [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] **Mes paramètres** . Lorsque des utilisateurs se connectent au client géré Azure, une relation est établie entre leur compte Azure et les autorisations [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  Pour plus d’informations, consultez [Mes paramètres pour l’intégration de Power BI &#40;portail web&#41;](../my-settings-for-power-bi-integration-web-portal.md).

3. Un jeton de sécurité utilisateur est renvoyé au serveur de rapports.

4. Le jeton de sécurité utilisateur est enregistré dans la base de données ReportServer.

5. Une liste des tableaux de bord auxquels l’utilisateur a accès est récupérée auprès du service [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] .  L’utilisateur sélectionne le groupe de destination et le tableau de bord de destination, puis configure la fréquence à laquelle les données doivent être actualisées sur la vignette [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)] .

6. L’élément de rapport est épinglé au tableau de bord.

7. Un abonnement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est créé pour gérer l’actualisation planifiée de l’élément de rapport sur la vignette de tableau de bord. L’abonnement utilise le jeton de sécurité créé lors de la connexion de l’utilisateur.

     Le jeton est valable **90 jours** , après quoi les utilisateurs doivent se reconnecter pour en créer un. Une fois le jeton expiré, les vignettes épinglées restent affichées sur le tableau de bord, mais les données ne sont plus actualisées.  Les abonnements [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilisés pour les éléments épinglés génèrent une erreur tant qu’un nouveau jeton n’est pas créé. Consultez [Mes paramètres pour l’intégration de Power BI &#40;portail web&#41;](../my-settings-for-power-bi-integration-web-portal.md). pour plus d’informations.

Lorsqu’un utilisateur épingle un élément pour la deuxième fois, les étapes 1 à 4 sont ignorées. L’ID d’application et les URL sont récupérés auprès de la base de données ReportServer et la procédure reprend à l’étape 5.

![Diagramme montrant ce qui se passe lorsqu’un utilisateur épingle un élément de rapport à un tableau de bord.](../../reporting-services/install-windows/media/ssrs-pin-to-powerbi-flow.png)

 **Lorsqu’un abonnement se déclenche pour actualiser une vignette de tableau de bord :**

1. Lorsque l’abonnement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] se déclenche, le rapport est rendu.

2. Le jeton utilisateur est récupéré auprès de la base de données ReportServer.

3. L’état et les données de l’élément de rapport sont envoyés avec le jeton au service [!INCLUDE[sspowerbi](../../includes/sspowerbi-md.md)].

4. Le jeton est envoyé à Azure AD pour validation. Si le jeton est valide, les données de l’élément de rapport sont envoyées à la vignette de tableau de bord et la propriété de date de la vignette est mise à jour.

5. Si le jeton n’est pas valide, une erreur est renvoyée et consignée avec le serveur de rapports.  Aucun état ou autre information n’est envoyé au tableau de bord.

![Diagramme montrant ce qui se passe lorsqu’un abonnement se déclenche pour actualiser une vignette de tableau de bord.](../../reporting-services/install-windows/media/ssrs-subscription-to-powerbi-flow.png)

   <iframe width="560" height="315" src="https://www.youtube.com/embed/QhPQObqmMPc" frameborder="0" allowfullscreen></iframe>

## <a name="considerations-and-limitations"></a>Considérations et limitations

* Les locataires viraux et gouvernementaux ne sont pas pris en charge.

## <a name="next-steps"></a>Étapes suivantes

[Mes paramètres pour l’intégration de Power BI &#40;portail web&#41;](../my-settings-for-power-bi-integration-web-portal.md)  
[Épingler des éléments Reporting Services aux tableaux de bord Power BI](../../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md)
[Tableaux de bord Power BI](https://powerbi.microsoft.com/documentation/powerbi-service-dashboards/)  

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)