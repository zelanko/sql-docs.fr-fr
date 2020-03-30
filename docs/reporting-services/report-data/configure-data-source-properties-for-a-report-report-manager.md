---
title: Configurer les propriétés de la source de données d’un rapport paginé - SSRS | Microsoft Docs
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-data
ms.topic: conceptual
helpviewer_keywords:
- data sources [Reporting Services], embedded
ms.assetid: 27af5195-c845-40e0-9a9c-efe569424022
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5e134c81fd697d4aa6fc7e5b620c1a71ff462b73
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "65573192"
---
# <a name="configure-data-source-properties-for-a-paginated-report"></a>Configurer les propriétés de la source de données d’un rapport paginé
  Quand vous exécutez un rapport paginé, le serveur de rapports récupère les informations de propriété pour déterminer le mode de connexion à une source de données. Le type de source de données, la chaîne de connexion et les informations d'identification sont spécifiés dans les pages de propriétés de la source de données du rapport publié. Vous pouvez définir les propriétés de manière à changer les informations de connexion à la source de données par rapport aux valeurs d'origine spécifiées lors de la création du rapport.  
  
 Sinon, si vous disposez d'une source de données partagée prédéfinie qui indique déjà les informations de connexion à utiliser, vous pouvez spécifier une source de données partagée à la place. Pour utiliser une source de données partagée, cliquez sur **Source de données partagée** dans la page de propriétés de la source de données du rapport.  
  
## <a name="to-configure-an-embedded-data-source"></a>Pour configurer une source de données incorporée  
  
1.  Dans le portail web, accédez au rapport pour lequel vous souhaitez configurer une source de données spécifique.  
  
3.  Sélectionnez les points de suspension ( **...** ) dans le coin supérieur droit > **Gérer**.  
  
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
  
 Pour plus d’informations sur la configuration des informations d’identification, consultez [Spécifier des informations d’identification et de connexion pour les sources de données de rapport](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md). Pour plus d’informations sur le compte d’exécution sans assistance, consultez [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).  
  
## <a name="see-also"></a>Voir aussi  
[Créer, modifier et supprimer des sources de données partagées &#40;SSRS&#41;](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)   
[Gérer des sources de données de rapports](../../reporting-services/report-data/manage-report-data-sources.md)
  
