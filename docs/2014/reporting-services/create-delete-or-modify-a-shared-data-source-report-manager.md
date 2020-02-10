---
title: Créer, supprimer ou modifier une source de données partagée (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- shared data sources [Reporting Services]
- removing shared data sources
- data sources [Reporting Services], shared
- deleting shared data sources
- modifying shared data sources
ms.assetid: cd7bace3-f8ec-4ee3-8a9f-2f217cdca9f2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c554215ba716a35f3e2851a5042be1989ee5648c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109612"
---
# <a name="create-delete-or-modify-a-shared-data-source-report-manager"></a>Créer, supprimer ou modifier une source de données partagée (Gestionnaire de rapports)
  Une source de données partagée spécifie les propriétés de connexion d'une source de données. Si une source de données est utilisée par un grand nombre de rapports, de modèles ou d'abonnements pilotés par les données, songez à créer une source de données partagée pour éliminer le temps de traitement nécessaire à la gestion des mêmes informations de connexion à plusieurs emplacements.  
  
 L'icône suivante indique une source de données partagée dans l'arborescence des dossiers du Gestionnaire de rapports :  
  
 ![Icône de source de données partagée](media/hlp-16datasource.png "Icône de source de données partagée")  
icône de source de données partagée  
  
### <a name="to-create-a-shared-data-source"></a>Pour créer une source de données partagée  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md).  
  
2.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'à la page **Contenu** .  
  
3.  Cliquez sur **Nouvelle source de données**. La page **Nouvelle source de données** s’ouvre.  
  
4.  Tapez le nom de l'élément. Le nom doit contenir au moins un caractère et il doit commencer par une lettre. Il peut également comprendre des symboles, à l'exception des espaces ou des caractères ; ? : \@ & = +, $/* \< > | " /.  
  
5.  Si vous le souhaitez, entrez une description renseignant les utilisateurs sur la connexion. Ce descriptif s'affiche dans la page **Contenu** du Gestionnaire de rapports.  
  
6.  Dans la liste **Type de source de données** , spécifiez l'extension pour le traitement des données qui est utilisée en vue d'exploiter les informations à partir de la source de données.  
  
7.  Dans la zone **Chaîne de connexion**, spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. Il est recommandé de n'indiquer aucune information d'identification ici.  
  
     L’exemple suivant illustre une chaîne de connexion pour la connexion à la [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] base de données locale :  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  Pour **Se connecter en utilisant**, précisez comment les informations d'identification sont obtenues lorsque le rapport s'exécute :  
  
    -   Si vous voulez demander à l'utilisateur un nom de connexion et un mot de passe, cliquez sur **Informations d'identification fournies par l'utilisateur qui exécute le rapport**. Pour utiliser les informations d'identification fournies par l'utilisateur en tant qu'informations d'identification Windows, activez la case à cocher **Utiliser comme informations d'identification Windows lors de la connexion à la source de données**. Si le nom d'utilisateur et le mot de passe sont des informations d'identification de base de données, ne sélectionnez pas cette option.  
  
    -   Si vous avez l’intention d’utiliser la source de données comme source de données partagée avec des informations d’identification enregistrées gérées par le propriétaire de la source de données ou pour des rapports prenant en charge les abonnements ou d’autres opérations planifiées (par exemple, la création automatique d’un historique de rapport), cliquez sur **Informations d’identification stockées de manière sécurisée sur le serveur de rapports**. Si le serveur de base de données prend en charge l'emprunt d'identité ou la délégation, sélectionnez **Emprunter l'identité de l'utilisateur authentifié une fois la connexion établie à la source de données**.  
  
    -   Si vous souhaitez que le serveur de rapports transmette les informations d'identification de l'utilisateur du rapport au serveur qui héberge la source de données externe, cliquez sur **Sécurité intégrée de Windows**. Dans ce cas, l'utilisateur n'est pas invité à taper son nom d'utilisateur ou son mot de passe.  
  
    -   Si la source de données n’utilise pas d’informations d’identification (par exemple, si la source de données est un fichier XML accessible à partir du le système de fichiers), cliquez sur **Informations d’identification non requises**. Spécifiez uniquement ce type d'informations d'identification s'il est valide pour la source de données. Si vous sélectionnez cette option pour une source de données qui requiert l'authentification, la connexion échoue. Si vous sélectionnez cette option, veillez à configurer le compte d'exécution sans assistance, qui permet au serveur de rapports de se connecter à d'autres ordinateurs pour récupérer des données ou des fichiers lorsque les informations d'identification de l'utilisateur ne sont pas disponibles.  
  
     Pour plus d’informations sur la configuration d’informations d’identification, consultez [Spécifier des informations d’identification et de connexion pour les sources de données de rapport](report-data/specify-credential-and-connection-information-for-report-data-sources.md). Pour plus d’informations sur le compte d’exécution sans assistance, consultez [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
9. Cliquez sur le bouton **Tester la connexion** pour valider la configuration de la source de données.  
  
    > [!NOTE]  
    >  Le bouton Tester la connexion n'est pas pris en charge pour le type de source de données XML.  
  
10. Cliquez sur **OK** .  
  
### <a name="to-modify-a-shared-data-source"></a>Pour modifier une source de données partagée  
  
1.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'à la page Contenu.  
  
2.  Accédez à l’élément de source de données partagée, pointez sur l’élément, cliquez sur la liste déroulante, puis dans le menu contextuel, cliquez sur **Gérer**. La page de **propriétés** s'ouvre.  
  
3.  Modifiez la source de données, puis cliquez sur **Appliquer**.  
  
### <a name="to-delete-a-shared-data-source"></a>Pour supprimer une source de données partagée  
  
-   Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'à la page **Contenu** et effectuez l'une des opérations suivantes :  
  
    -   Naviguez jusqu'à l'élément de source de données partagée.  
  
         Cliquez sur l'élément pour l'ouvrir. La page des propriétés générales s'ouvre.  
  
         Cliquez sur **Supprimer**, puis sur **OK**.  
  
    -   Dans la page **Contenu** , parcourez l'arborescence jusqu'au dossier contenant la source de données à supprimer.  
  
         Pointez sur l’élément, cliquez sur la liste déroulante, puis dans le menu contextuel, cliquez sur **Supprimer**.  
  
         [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions de données, sources de données et chaînes de connexion dans Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Page contenu &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/contents-page-report-manager.md)   
 [Créer, modifier et supprimer des sources de données partagées &#40;SSRS&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md)   
 [Gérer des sources de données de rapports](report-data/manage-report-data-sources.md)   
 [Configurer les propriétés de la source de données d’un rapport &#40;Gestionnaire de rapports&#41;](report-data/configure-data-source-properties-for-a-report-report-manager.md)  
  
  
