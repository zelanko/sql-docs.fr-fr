---
title: Configurer les propriétés de la source de données d’un rapport (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
ms.assetid: 27af5195-c845-40e0-9a9c-efe569424022
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98916a7e6a9247661fdefe3a779e08f255d56ac8
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59959685"
---
# <a name="configure-data-source-properties-for-a-report--report-manager"></a>Configurer les propriétés de la source de données d’un rapport (Gestionnaire de rapports)
  Lorsque vous exécutez un rapport, le serveur de rapports récupère les informations de propriété pour déterminer le mode de connexion à une source de données. Le type de source de données, la chaîne de connexion et les informations d'identification sont spécifiés dans les pages de propriétés de la source de données du rapport publié. Vous pouvez définir les propriétés de manière à changer les informations de connexion à la source de données par rapport aux valeurs d'origine spécifiées lors de la création du rapport.  
  
 Sinon, si vous disposez d'une source de données partagée prédéfinie qui indique déjà les informations de connexion à utiliser, vous pouvez spécifier une source de données partagée à la place. Pour utiliser une source de données partagée, cliquez sur **Source de données partagée** dans la page de propriétés de la source de données du rapport.  
  
### <a name="to-configure-an-embedded-data-source"></a>Pour configurer une source de données incorporée  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Dans le Gestionnaire de rapports, parcourez l'arborescence jusqu'à la page **Contenu** . Repérez le rapport pour lequel vous souhaitez configurer une source de données spécifique, puis cliquez sur cet élément pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Propriétés** . La page **Propriétés générales** s’affiche.  
  
4.  Cliquez sur l'onglet **Sources de données** . Cela entraîne l'affichage de la page de propriétés de la source de données du rapport.  
  
5.  Cliquez sur **Source de données personnalisée** pour spécifier les informations de connexion à la source de données dans le rapport.  
  
6.  Dans la liste **Type de connexion** , spécifiez l’extension pour le traitement des données qui est utilisée en vue d’exploiter les informations à partir de la source de données.  
  
7.  Dans la zone **Chaîne de connexion**, spécifiez la chaîne de connexion utilisée par le serveur de rapports pour se connecter à la source de données. Il est recommandé de n'indiquer aucune information d'identification ici.  
  
     L'exemple suivant illustre l'utilisation d'une chaîne de connexion pour se connecter à la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] locale :  
  
    ```  
    data source=<localservername>; initial catalog=AdventureWorks2012  
    ```  
  
8.  Pour **Se connecter en utilisant**, précisez comment les informations d'identification sont obtenues lorsque le rapport s'exécute :  
  
    -   Si vous voulez demander à l'utilisateur un nom de connexion et un mot de passe, cliquez sur **Informations d'identification fournies par l'utilisateur qui exécute le rapport**.  
  
    -   Si vous avez l’intention d’utiliser la source de données pour les rapports prenant en charge des abonnements ou d’autres opérations planifiées (par exemple, la création automatique d’historiques de rapports), cliquez sur **Informations d’identification stockées de manière sécurisée sur le serveur de rapports**.  
  
    -   Si vous souhaitez que le serveur de rapports transmette les informations d'identification de l'utilisateur du rapport au serveur qui héberge la source de données externe, cliquez sur **Sécurité intégrée de Windows**. Dans ce cas, l'utilisateur n'est pas invité à taper son nom d'utilisateur ou son mot de passe.  
  
    -   Si la source de données n’utilise pas d’informations d’identification (par exemple, si la source de données est un fichier XML accessible à partir du le système de fichiers), cliquez sur **Informations d’identification non requises**. Spécifiez uniquement ce type d'informations d'identification s'il est valide pour la source de données. Si vous sélectionnez cette option pour une source de données qui requiert l'authentification, la connexion échoue. Si vous sélectionnez cette option, veillez à configurer le compte d'exécution sans assistance, qui permet au serveur de rapports de se connecter à d'autres ordinateurs pour récupérer des données ou des fichiers lorsque les informations d'identification de l'utilisateur ne sont pas disponibles.  
  
 Pour plus d’informations sur la configuration des informations d’identification, consultez [Spécifier des informations d’identification et de connexion pour les sources de données de rapport](specify-credential-and-connection-information-for-report-data-sources.md). Pour plus d’informations sur le compte d’exécution sans assistance, consultez [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Page Contenu &#40;Gestionnaire de rapports&#41;](../contents-page-report-manager.md)   
 [Page Nouvelle source de données &#40;Gestionnaire de rapports&#41;](../new-data-source-page-report-manager.md)   
 [Créer, modifier et supprimer des sources de données partagées &#40;SSRS&#41;](create-modify-and-delete-shared-data-sources-ssrs.md)   
 [Gérer des sources de données de rapports](manage-report-data-sources.md)   
 [Créer, supprimer ou modifier une source de données partagée &#40;Gestionnaire de rapports&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Page des propriétés des sources de données &#40;Gestionnaire de rapports&#41;](../data-sources-properties-page-report-manager.md)  
  
  
