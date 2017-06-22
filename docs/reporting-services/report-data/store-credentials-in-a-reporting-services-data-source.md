---
title: "Stocker des informations d’identification dans une Source de données Reporting Services | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 09/23/2015
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- credentials [Reporting Services]
- security [Analysis Services], data sources
- stored credentials [Reporting Services]
- data sources [Reporting Services], stored credentials
ms.assetid: dc700922-97fa-4b30-9547-05bbbec4f09c
caps.latest.revision: 42
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6ca8d81025d48af07b5e2ce9336a8e031ea4fb1a
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="store-credentials-in-a-reporting-services-data-source"></a>Store Credentials in a Reporting Services Data Source
  Vous pouvez configurer des informations d'identification stockées pour permettre à un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] d'accéder aux données externes d'un rapport. Les informations d'identification stockées sont utilisées si le rapport s'exécute sans assistance, par exemple dans le cas d'un abonnement [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui publie un rapport sous forme d'e-mail. Le serveur de rapports récupère et utilise les informations d'identification quand le traitement du rapport est planifié ou déclenché. Cette rubrique vous guide tout au long de la configuration des informations d'identification stockées pour les serveurs de rapports en mode natif et en mode SharePoint.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint|  
  
-   [Configurer les informations d'identification stockées pour une source de données spécifique à un rapport (mode natif)](#bkmk_stored_credentials_data_source_native)  
  
-   [Configurer les informations d'identification stockées pour une source de données spécifique à un rapport (mode SharePoint)](#bkmk_stored_credentials_data_source_sharepoint)  
  
-   [Configurer les informations d'identification stockées pour une source de données partagée (mode natif)](#bkmk_stored_credentials_shared_data_source_native)  
  
-   [Configurer les informations d'identification stockées pour une source de données partagée (mode SharePoint)](#bkmk_stored_credentials_shared_data_source_sharepoint)  
  
##  <a name="bkmk_top"></a> Conditions requises en matière de stratégie de sécurité pour les informations d'identification stockées  
 ![as_powerpivot_refresh_sss_set_key](../../analysis-services/power-pivot-sharepoint/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key") qu’il est nécessaire que le compte que vous utilisez les informations d’identification stockées, est configuré pour l’une des stratégies de sécurité suivantes sur le serveur de rapports. Il est recommandé de sélectionner la stratégie avec le niveau minimal d'autorisations dont vous avez besoin pour votre environnement.  
  
1.  **Permettre l'ouverture d'une session locale**. Pour plus d'informations, consultez [Permettre l'ouverture d'une session locale](http://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx).  
  
2.  **Ouvrir une session en tant que tâche**. Pour plus d'informations, consultez [Ouvrir une session en tant que tâche](http://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx).  
  
3.  Pour obtenir des informations générales sur les stratégies, consultez [Modifier les paramètres de sécurité d'un objet de stratégie de groupe](http://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx).  
  
##  <a name="bkmk_stored_credentials_data_source_native"></a> Configurer les informations d'identification stockées pour une source de données spécifique à un rapport (mode natif)  
  
1.  Dans le Gestionnaire de rapports en mode natif, accédez au dossier qui contient le rapport. Cliquez sur le menu contextuel d’élément ![menu contextuel dans le Gestionnaire de rapports pour les éléments ssrs](../../reporting-services/report-data/media/ssrs-report-manager-item-context-menu.png "menu contextuel dans le Gestionnaire de rapports pour les éléments ssrs").  
  
2.  Cliquez sur **Gérer** , puis sur **Sources de données**.  
  
3.  Sélectionnez l'option **Source de données personnalisée**.  
  
4.  Dans la liste **Type de source de données** , sélectionnez l'extension pour le traitement des données utilisée pour traiter les données de la source de données.  
  
5.  Dans la zone **Chaîne de connexion**, spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. L'exemple suivant illustre l'utilisation d'une chaîne de connexion pour se connecter à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] :  
  
    ```  
    data source=<servername>;initial catalog=AdventureWorks2012  
    ```  
  
6.  Pour l'option **Se connecter avec**, sélectionnez **Informations d'identification stockées en sécurité dans le serveur de rapports**.  
  
7.  Tapez un nom d'utilisateur et un mot de passe.  
  
    -   Si le compte est un compte d’utilisateur de domaine Windows, spécifiez-le dans ce format : \<domaine >\\< compte\>, puis sélectionnez **utiliser comme informations d’identification Windows lors de la connexion à la source de données.**  
  
    -   Si le nom d'utilisateur et le mot de passe sont des informations d'identification de base de données, ne sélectionnez pas **Utiliser comme informations d'identification Windows lors de la connexion à la source de données**. Si le serveur de base de données prend en charge l'emprunt d'identité ou la délégation, sélectionnez **Emprunter l'identité de l'utilisateur authentifié une fois la connexion établie à la source de données**.  
  
8.  Cliquez sur **Appliquer**.  
  
     ![Icône de flèche utilisée avec différée lien en haut](../../analysis-services/instances/media/uparrow16x16.gif "icône de flèche utilisée avec différée lien en haut") [les exigences de stratégie de sécurité pour les informations d’identification stockées](#bkmk_top)  
  
##  <a name="bkmk_stored_credentials_data_source_sharepoint"></a> Configurer les informations d'identification stockées pour une source de données spécifique à un rapport (mode SharePoint)  
  
1.  Accédez à la bibliothèque de documents qui contient le rapport et cliquez sur le menu Ouvrir ![menu de contexte de bibliothèque de documents pour les éléments ssrs](../../reporting-services/report-data/media/ssrs-sharepoint-item-context-menu.png "menu de contexte de bibliothèque de documents pour les éléments ssrs").  
  
2.  Cliquez sur le second menu Ouvrir ![menu de contexte de bibliothèque de documents pour les éléments ssrs](../../reporting-services/report-data/media/ssrs-sharepoint-item-context-menu.png "menu de contexte de bibliothèque de documents pour les éléments ssrs") puis cliquez sur **gérer les Sources de données**.  
  
3.  Cliquez sur le nom de la source de données de type **Personnalisé** pour laquelle vous souhaitez configurer des informations d'identification stockées.  
  
4.  Dans la liste **Type de source de données** , sélectionnez l'extension pour le traitement des données utilisée pour traiter les données de la source de données.  
  
5.  Dans la zone **Chaîne de connexion**, spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. L'exemple suivant illustre l'utilisation d'une chaîne de connexion pour se connecter à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] :  
  
    ```  
    data source=<servername>;initial catalog=AdventureWorks2012  
    ```  
  
6.  Pour **Informations d'identification**, sélectionnez **Informations d'identification stockées**.  
  
7.  Tapez un **nom d'utilisateur** et un **mot de passe**.  
  
    -   Si le compte est un compte d’utilisateur de domaine Windows, spécifiez-le dans ce format : \<domaine >\\< compte\>, puis sélectionnez **utiliser comme informations d’identification Windows lors de la connexion à la source de données.**  
  
    -   Si le nom d'utilisateur et le mot de passe sont des informations d'identification de base de données, ne sélectionnez pas **Utiliser comme informations d'identification Windows**. Si le serveur de base de données prend en charge l'emprunt d'identité ou la délégation, vous pouvez sélectionner **Définir le contexte d'exécution pour ce compte**.  
  
8.  Cliquez sur **OK**.  
  
     ![Icône de flèche utilisée avec différée lien en haut](../../analysis-services/instances/media/uparrow16x16.gif "icône de flèche utilisée avec différée lien en haut") [les exigences de stratégie de sécurité pour les informations d’identification stockées](#bkmk_top)  
  
##  <a name="bkmk_stored_credentials_shared_data_source_native"></a> Configurer les informations d'identification stockées pour une source de données partagée (mode natif)  
  
1.  Dans le Gestionnaire de rapports en mode natif, accédez à l'élément de source de données partagée. ![Icône de source de données partagée](../../reporting-services/report-data/media/hlp-16datasource.png "icône de source de données partagée")  
  
2.  Cliquez sur le menu contextuel ![menu contextuel dans le Gestionnaire de rapports pour les éléments ssrs](../../reporting-services/report-data/media/ssrs-report-manager-item-context-menu.png "menu contextuel dans le Gestionnaire de rapports pour les éléments ssrs") puis cliquez sur **gérer**.  
  
3.  Dans la liste **Type de source de données** , spécifiez l'extension pour le traitement des données utilisée pour traiter les données de la source de données.  
  
4.  Dans la zone **Chaîne de connexion**, spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande de n'indiquer aucune information d'identification dans la chaîne de connexion.  
  
     L'exemple suivant illustre l'utilisation d'une chaîne de connexion pour se connecter à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] locale :  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
5.  Tapez un nom d'utilisateur et un mot de passe.  
  
    -   Si le compte est un compte d’utilisateur de domaine Windows, spécifiez-le dans ce format : \<domaine >\\< compte\>, puis sélectionnez **utiliser comme informations d’identification Windows lors de la connexion à la source de données.**  
  
    -   Si le nom d'utilisateur et le mot de passe sont des informations d'identification de base de données, ne sélectionnez pas **Utiliser comme informations d'identification Windows lors de la connexion à la source de données**. Si le serveur de base de données prend en charge l'emprunt d'identité ou la délégation, sélectionnez **Emprunter l'identité de l'utilisateur authentifié une fois la connexion établie à la source de données**.  
  
6.  Cliquez sur **Appliquer**.  
  
     ![Icône de flèche utilisée avec différée lien en haut](../../analysis-services/instances/media/uparrow16x16.gif "icône de flèche utilisée avec différée lien en haut") [les exigences de stratégie de sécurité pour les informations d’identification stockées](#bkmk_top)  
  
##  <a name="bkmk_stored_credentials_shared_data_source_sharepoint"></a> Configurer les informations d'identification stockées pour une source de données partagée (mode SharePoint)  
  
1.  Dans la bibliothèque de documents, accédez à l’élément de source de données partagée. ![Icône de source de données partagée](../../reporting-services/report-data/media/hlp-16datasource.png "icône de source de données partagée")  
  
2.  Cliquez sur le menu contextuel ![menu de contexte de bibliothèque de documents pour les éléments ssrs](../../reporting-services/report-data/media/ssrs-sharepoint-item-context-menu.png "menu de contexte de bibliothèque de documents pour les éléments ssrs") puis cliquez sur le second menu contextuel ![menu de contexte de bibliothèque de documents pour les éléments ssrs](../../reporting-services/report-data/media/ssrs-sharepoint-item-context-menu.png "menu de contexte de bibliothèque de documents pour les éléments ssrs").  
  
3.  Cliquez sur **Modifier la définition de la source de données**.  
  
4.  Dans la liste **Type de source de données** , spécifiez l'extension pour le traitement des données utilisée pour traiter les données de la source de données.  
  
5.  Dans la zone **Chaîne de connexion**, spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande de n'indiquer aucune information d'identification dans la chaîne de connexion.  
  
     L'exemple suivant illustre l'utilisation d'une chaîne de connexion pour se connecter à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] locale :  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
6.  Tapez un nom d'utilisateur et un mot de passe.  
  
    -   Si le compte est un compte d’utilisateur de domaine Windows, spécifiez-le dans ce format : \<domaine >\\< compte\>, puis sélectionnez **utiliser comme informations d’identification Windows.**  
  
    -   Si le nom d'utilisateur et le mot de passe sont des informations d'identification de base de données, ne sélectionnez pas **Utiliser comme informations d'identification Windows**. Si le serveur de base de données prend en charge l'emprunt d'identité ou la délégation, vous pouvez sélectionner **Définir le contexte d'exécution pour ce compte**.  
  
7.  Cliquez sur **OK**.  
  
     ![Icône de flèche utilisée avec différée lien en haut](../../analysis-services/instances/media/uparrow16x16.gif "icône de flèche utilisée avec différée lien en haut") [les exigences de stratégie de sécurité pour les informations d’identification stockées](#bkmk_top)  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapport](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Configurer les propriétés de la source de données d’un rapport &#40;Gestionnaire de rapports&#41;](../../reporting-services/report-data/configure-data-source-properties-for-a-report-report-manager.md)   
 [Créer, supprimer ou modifier une source de données partagée &#40;Gestionnaire de rapports&#41;](http://msdn.microsoft.com/library/cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2)   
 [Page des propriétés des sources de données &#40;Gestionnaire de rapports&#41;](http://msdn.microsoft.com/library/f37edda0-19e6-489e-b544-8751fa6b6cfb)   
 [Page Nouvelle source de données &#40;Gestionnaire de rapports&#41;](http://msdn.microsoft.com/library/35563d4c-a3d5-4f95-bf46-605da9dfcbb8)  
  
  

