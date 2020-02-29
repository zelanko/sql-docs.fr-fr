---
title: Stocker des informations d’identification dans une source de données Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 09/23/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- credentials [Reporting Services]
- security [Analysis Services], data sources
- stored credentials [Reporting Services]
- data sources [Reporting Services], stored credentials
ms.assetid: dc700922-97fa-4b30-9547-05bbbec4f09c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d70d5570735d2861f8cf62d3b8c0c61a3bae938
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78173008"
---
# <a name="store-credentials-in-a-reporting-services-data-source"></a>Store Credentials in a Reporting Services Data Source
  Vous pouvez configurer des informations d'identification stockées pour permettre à un serveur de rapports [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] d'accéder aux données externes d'un rapport. Les informations d'identification stockées sont utilisées si le rapport s'exécute sans assistance, par exemple dans le cas d'un abonnement [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] qui publie un rapport sous forme d'e-mail. Le serveur de rapports récupère et utilise les informations d'identification quand le traitement du rapport est planifié ou déclenché. Cette rubrique vous guide tout au long de la configuration des informations d'identification stockées pour les serveurs de rapports en mode natif et en mode SharePoint.

||
|-|
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]Mode natif &#124; [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] mode SharePoint|

 **Dans cette rubrique :**

-   [Configurer les informations d’identification stockées pour une source de données spécifique à un rapport (mode natif)](#bkmk_stored_credentials_data_source_native)

-   [Configurer les informations d’identification stockées pour une source de données spécifique à un rapport (mode SharePoint)](#bkmk_stored_credentials_data_source_sharepoint)

-   [Configurer les informations d’identification stockées pour une source de données partagée (mode natif)](#bkmk_stored_credentials_shared_data_source_native)

-   [Configurer les informations d’identification stockées pour une source de données partagée (mode SharePoint)](#bkmk_stored_credentials_shared_data_source_sharepoint)

##  <a name="bkmk_top"></a>Conditions de la stratégie de sécurité pour les informations d’identification stockées
 ![as_powerpivot_refresh_sss_set_key](https://docs.microsoft.com/analysis-services/analysis-services/media/as-powerpivot-refresh-sss-set-key.gif "as_powerpivot_refresh_sss_set_key") Il est nécessaire que le compte que vous utilisez pour les informations d’identification stockées soit configuré pour l’une des stratégies de sécurité suivantes sur le serveur de rapports. Il est recommandé de sélectionner la stratégie avec le niveau minimal d'autorisations dont vous avez besoin pour votre environnement.

1.  **Autoriser l’ouverture d’une session locale**. Pour plus d'informations, consultez [Permettre l'ouverture d'une session locale](https://technet.microsoft.com/library/cc756809\(v=WS.10\).aspx).

2.  **Ouvrir une session en tant que tâche**. Pour plus d'informations, consultez [Ouvrir une session en tant que tâche](https://technet.microsoft.com/library/cc755659\(v=ws.10\).aspx).

3.  Pour obtenir des informations générales sur les stratégies, consultez [Modifier les paramètres de sécurité d'un objet de stratégie de groupe](https://technet.microsoft.com/library/cc736516\(v=ws.10\).aspx).

##  <a name="bkmk_stored_credentials_data_source_native"></a>Configurer les informations d’identification stockées pour une source de données spécifique à un rapport (mode natif)

1.  Dans le Gestionnaire de rapports en mode natif, accédez au dossier qui contient le rapport. Cliquez sur le menu contextuel de l’élément dans le menu contextuel du ![Gestionnaire de rapports pour les éléments SSRS](../media/ssrs-report-manager-item-context-menu.png "menu contextuel du gestionnaire de rapports pour les éléments ssrs").

2.  Cliquez sur **Gérer** , puis sur **Sources de données**.

3.  Sélectionnez l'option **Source de données personnalisée**.

4.  Dans la liste **Type de source de données** , sélectionnez l'extension pour le traitement des données utilisée pour traiter les données de la source de données.

5.  Pour **chaîne de connexion**, spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. L’exemple suivant illustre une chaîne de connexion utilisée pour se connecter à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] la base de données :

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  Pour l'option **Se connecter avec**, sélectionnez **Informations d'identification stockées en sécurité dans le serveur de rapports**.

7.  Tapez un nom d'utilisateur et un mot de passe.

    -   Si le compte est un compte d’utilisateur de domaine Windows, spécifiez-le en respectant le format suivant : \<domaine>\\<compte\>, puis sélectionnez **Utiliser comme informations d’identification Windows lors de la connexion à la source de données**.

    -   Si le nom d'utilisateur et le mot de passe sont des informations d'identification de base de données, ne sélectionnez pas **Utiliser comme informations d'identification Windows lors de la connexion à la source de données**. Si le serveur de base de données prend en charge l'emprunt d'identité ou la délégation, sélectionnez **Emprunter l'identité de l'utilisateur authentifié une fois la connexion établie à la source de données**.

8.  Cliquez sur **Appliquer**.

     ![Icône de flèche utilisée avec le lien retour au début](../../2014-toc/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour en haut") [Configuration requise de la stratégie de sécurité pour les informations d’identification stockées](#bkmk_top)

##  <a name="bkmk_stored_credentials_data_source_sharepoint"></a>Configurer les informations d’identification stockées pour une source de données spécifique à un rapport (mode SharePoint)

1.  Accédez à la bibliothèque de documents qui contient le rapport, puis cliquez sur Ouvrir le menu ![contextuel de la bibliothèque de documents pour les éléments SSRS](../media/ssrs-sharepoint-item-context-menu.png "menu contextuel de la bibliothèque de documents pour les éléments ssrs").

2.  Cliquez sur le menu ![contextuel de la bibliothèque de documents du menu Ouvrir pour les éléments SSRS](../media/ssrs-sharepoint-item-context-menu.png "menu contextuel de la bibliothèque de documents pour les éléments ssrs") , puis cliquez sur **gérer les sources de données**.

3.  Cliquez sur le nom de la source de données de type **Personnalisé** pour laquelle vous souhaitez configurer des informations d'identification stockées.

4.  Dans la liste **Type de source de données** , sélectionnez l'extension pour le traitement des données utilisée pour traiter les données de la source de données.

5.  Pour **chaîne de connexion**, spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. L’exemple suivant illustre une chaîne de connexion utilisée pour se connecter à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] la base de données :

    ```
    data source=<servername>;initial catalog=AdventureWorks2012
    ```

6.  Pour les **informations d’identification**, sélectionnez **informations d’identification stockées**.

7.  Tapez un **nom d’utilisateur** et un **mot de passe**.

    -   Si le compte est un compte d’utilisateur de domaine Windows, spécifiez-le en respectant le format suivant : \<domaine>\\<compte\>, puis sélectionnez **Utiliser comme informations d’identification Windows lors de la connexion à la source de données**.

    -   Si le nom d'utilisateur et le mot de passe sont des informations d'identification de base de données, ne sélectionnez pas **Utiliser comme informations d'identification Windows**. Si le serveur de base de données prend en charge l'emprunt d'identité ou la délégation, vous pouvez sélectionner **Définir le contexte d'exécution pour ce compte**.

8.  Cliquez sur **OK**.

     ![Icône de flèche utilisée avec le lien retour au début](../../2014-toc/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour en haut") [Configuration requise de la stratégie de sécurité pour les informations d’identification stockées](#bkmk_top)

##  <a name="bkmk_stored_credentials_shared_data_source_native"></a>Configurer les informations d’identification stockées pour une source de données partagée (mode natif)

1.  Dans le Gestionnaire de rapports en mode natif, accédez à l'élément de source de données partagée. ![Icône de source de données partagée](../media/hlp-16datasource.png "Icône de source de données partagée")

2.  Cliquez sur le menu contextuel du menu contextuel du ![Gestionnaire de rapports pour les éléments SSRS](../media/ssrs-report-manager-item-context-menu.png "menu contextuel du gestionnaire de rapports pour les éléments ssrs") , puis cliquez sur **gérer**.

3.  Dans la liste **type de source de données** , spécifiez l’extension pour le traitement des données utilisée pour traiter les données de la source de données.

4.  Pour **chaîne de connexion**, spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. 
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] recommande de n'indiquer aucune information d'identification dans la chaîne de connexion.

     L’exemple suivant illustre une chaîne de connexion utilisée pour se connecter à la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] base de données locale :

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

5.  Tapez un nom d'utilisateur et un mot de passe.

    -   Si le compte est un compte d’utilisateur de domaine Windows, spécifiez-le en respectant le format suivant : \<domaine>\\<compte\>, puis sélectionnez **Utiliser comme informations d’identification Windows lors de la connexion à la source de données**.

    -   Si le nom d'utilisateur et le mot de passe sont des informations d'identification de base de données, ne sélectionnez pas **Utiliser comme informations d'identification Windows lors de la connexion à la source de données**. Si le serveur de base de données prend en charge l'emprunt d'identité ou la délégation, sélectionnez **Emprunter l'identité de l'utilisateur authentifié une fois la connexion établie à la source de données**.

6.  Cliquez sur **Appliquer**.

     ![Icône de flèche utilisée avec le lien retour au début](../../2014-toc/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour en haut") [Configuration requise de la stratégie de sécurité pour les informations d’identification stockées](#bkmk_top)

##  <a name="bkmk_stored_credentials_shared_data_source_sharepoint"></a>Configurer les informations d’identification stockées pour une source de données partagée (mode SharePoint)

1.  Dans la bibliothèque de documents, accédez à l’élément de source de données partagée. ![Icône de source de données partagée](../media/hlp-16datasource.png "Icône de source de données partagée")

2.  Cliquez sur le menu contextuel ![de la bibliothèque de documents menu contextuel pour les éléments SSRS](../media/ssrs-sharepoint-item-context-menu.png "menu contextuel de la bibliothèque de documents pour les éléments ssrs") , puis cliquez sur le second menu contextuel ![de la bibliothèque de documents menu contextuel pour les éléments SSRS](../media/ssrs-sharepoint-item-context-menu.png "menu contextuel de la bibliothèque de documents pour les éléments ssrs").

3.  Cliquez sur **Modifier la définition de la source de données**.

4.  Dans la liste **type de source de données** , spécifiez l’extension pour le traitement des données utilisée pour traiter les données de la source de données.

5.  Pour **chaîne de connexion**, spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. 
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] recommande de n'indiquer aucune information d'identification dans la chaîne de connexion.

     L’exemple suivant illustre une chaîne de connexion utilisée pour se connecter à la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] base de données locale :

    ```
    data source=<localservername>; initial catalog=AdventureWorks2012
    ```

6.  Tapez un nom d'utilisateur et un mot de passe.

    -   Si le compte est un compte d’utilisateur de domaine Windows, spécifiez-le en respectant le format suivant : \<domaine>\\<compte\>, puis sélectionnez **Utiliser comme informations d’identification Windows**.

    -   Si le nom d'utilisateur et le mot de passe sont des informations d'identification de base de données, ne sélectionnez pas **Utiliser comme informations d'identification Windows**. Si le serveur de base de données prend en charge l’emprunt d’identité ou la délégation, vous pouvez sélectionner **définir le contexte d’exécution pour ce compte**.

7.  Cliquez sur **OK**.

     ![Icône de flèche utilisée avec le lien retour au début](../../2014-toc/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour en haut") [Configuration requise de la stratégie de sécurité pour les informations d’identification stockées](#bkmk_top)

## <a name="see-also"></a>Voir aussi
 [Spécifiez les informations d’identification et de connexion pour les sources de données de rapport](../../integration-services/connection-manager/data-sources.md) [configurer les propriétés de la source de données d’un rapport &#40;gestionnaire de rapports&#41;](configure-data-source-properties-for-a-report-report-manager.md) [créer, supprimer ou modifier une source de données partagée &#40;gestionnaire de rapports](../create-delete-or-modify-a-shared-data-source-report-manager.md)&#41;[page de propriétés des sources de données](../data-sources-properties-page-report-manager.md) &#40;gestionnaire de rapports&#41;&#40;[nouvelle page de source de données](../new-data-source-page-report-manager.md) gestionnaire de rapports&#41;


