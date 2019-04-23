---
title: Créer, modifier, puis supprimer des sources de données partagées (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- modifying data source properties
- shared data sources [Reporting Services]
- removing shared data sources
- roles [Reporting Services], shared data sources
- data sources [Reporting Services], shared
- data sources [Reporting Services], modifying properties
- deleting shared data sources
ms.assetid: 1e58c1c2-5ecf-4ce6-9d04-0a8acfba17be
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 26bc12ce8c685c4aeb119f43ab594d920a6cef9f
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59934745"
---
# <a name="create-modify-and-delete-shared-data-sources-ssrs"></a>Créer, modifier, puis supprimer des sources de données partagées (SSRS)
  Une source de données partagée est un ensemble de propriétés de connexion à la source de données pouvant être référencées par plusieurs rapports, modèles et abonnements pilotés par les données qui s’exécutent sur un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Les sources de données partagées permettent de gérer facilement des propriétés de source de données qui changent souvent dans le temps. Si le compte ou le mot de passe d'un utilisateur change ou bien si vous déplacez la base de données sur un serveur différent, vous pouvez mettre à jour les informations de connexion à un seul endroit.  
  
 Les sources de données partagées sont obligatoires pour les modèles de rapports et facultatives pour les rapports et les abonnements pilotés par les données. Si vous envisagez d'utiliser des modèles de rapports pour la génération d'états ad hoc, vous devez créer et gérer un élément de source de données partagée pour fournir des informations de connexion au modèle.  
  
 Une source de données partagée se compose des éléments suivants :  
  
|Élément|Description|  
|----------|-----------------|  
|Nom|Nom qui identifie l'élément au sein de la hiérarchie des dossiers du serveur de rapports.|  
|Description|Description qui apparaît avec l'élément dans le Gestionnaire de rapports lorsque vous consultez le contenu du dossier.|  
|Type de connexion|Extension pour le traitement des données utilisée avec la source de données. Vous ne pouvez utiliser que les extensions pour le traitement des données qui sont déployées sur le serveur de rapports. Pour plus d’informations sur les extensions pour le traitement des données incluses dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], consultez [Sources de données prises en charge par Reporting Services &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md).|  
|Chaîne de connexion|Chaîne de connexion pour la base de données. Pour plus d’informations et pour consulter des exemples de chaînes de connexion aux sources de données fréquemment utilisées, consultez [des connexions de données, les Sources de données et les chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md).|  
|Type d'informations d'identification|Spécifie la façon dont les informations d'identification sont obtenues pour la connexion et si elles doivent être utilisées une fois la connexion établie. Pour plus d’informations, consultez [Spécifier des informations d’identification et de connexion pour les sources de données de rapport](../../integration-services/connection-manager/data-sources.md).|  
  
 Une source de données partagée ne contient pas d'informations de requête utilisées pour récupérer des données. La requête est toujours conservée dans une définition de rapport.  
  
## <a name="creating-and-modifying-a-shared-data-source"></a>Création et modification d'une source de données partagée  
 Pour créer une source de données partagée ou modifier ses propriétés, vous devez disposer d'autorisations **Gérer les sources de données** sur le serveur de rapports. Si le serveur de rapports s'exécute en mode natif, vous pouvez utiliser le Gestionnaire de rapports pour créer et configurer la source de données partagée. Si le serveur de rapports s'exécute en mode intégré SharePoint, vous pouvez utiliser les pages d'application sur un site SharePoint. Pour n'importe quel serveur de rapports et quel que soit son mode, vous pouvez créer une source de données partagée dans le Concepteur de rapports, puis la publier sur un serveur cible.  
  
 Pour plus d'informations sur la création d'une source de données partagée, consultez :  
  
-   [Créer une source de données incorporée ou partagée &#40;SSRS&#41;](../create-an-embedded-or-shared-data-source-ssrs.md)  
  
-   [Créer et gérer des sources de données partagées &#40;Reporting Services en mode intégré SharePoint&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)  
  
 Après avoir créé une source de données partagée sur le serveur de rapports, vous pouvez créer des attributions de rôle pour y contrôler l'accès, la déplacer à un autre endroit, la renommer ou la mettre hors ligne pour empêcher le traitement des rapports pendant que des opérations de maintenance sont effectuées sur la source de données externe. Si vous renommez ou déplacez un élément de source de données partagée à un autre endroit de la hiérarchie des dossiers du serveur de rapports, les informations de chemin de tous les rapports ou abonnements qui font référence à cette source de données partagée sont corrigées en conséquence. Si vous mettez la source de données partagée hors ligne, aucun rapport, modèle ou abonnement ne s'exécutera tant que vous n'aurez pas réactivé la source de données.  
  
 Pour plus d’informations sur le contrôle de l’accès aux sources de données partagées dans l’arborescence des dossiers du serveur de rapports, consultez [Sécuriser les éléments de source de données partagée](../security/secure-shared-data-source-items.md).  
  
## <a name="deleting-a-shared-data-source"></a>Suppression d'une source de données partagée  
 Vous pouvez supprimer une source de données partagée de la même manière que vous supprimez un élément quelconque du serveur de rapports. Dans le Gestionnaire de rapports, vous ouvrez le dossier dans la vue de détails, sélectionnez l’élément, puis cliquez sur **supprimer**. Dans une page d’application sur un site SharePoint, vous ouvrez la bibliothèque SharePoint, sélectionnez l’élément, puis cliquez sur **supprimer**.  
  
 La suppression d'une source de données partagée désactive tout rapport, modèle ou abonnement piloté par les données qui l'utilise. Sans informations de connexion à la source de données, les éléments ne s'exécuteront plus. Pour activer ces éléments, vous devez ouvrir chacun d'eux et effectuer les opérations suivantes :  
  
-   Pour les rapports et abonnements pilotés par les données qui référencent la source de données partagée, vous pouvez spécifier les informations de connexion à la source de données dans les propriétés du rapport ou l'abonnement au rapport. Vous pouvez aussi sélectionner une nouvelle source de données partagée possédant les valeurs que vous souhaitez utiliser.  
  
-   Pour les modèles et les rapports du Générateur de rapports qui utilisent ce modèle, vous devez spécifier une nouvelle source de données partagée. Les modèles obtiennent uniquement des informations de connexion à la source de données par le biais des sources de données partagées.  
  
 Pour afficher la liste des rapports et modèles qui utilisent la source de données, ouvrez la page Éléments dépendants de la source de données partagée. Vous pouvez accéder à cette page lorsque vous ouvrez la source de données dans le Gestionnaire de rapports ou dans une page d'application SharePoint. Notez que la page Éléments dépendants n'indique pas les abonnements pilotés par les données. Si une source de données partagée est utilisée par un abonnement, celui-ci ne figurera pas dans la liste Éléments dépendants.  
  
 Il n'existe pas d'opération d'annulation pour la suppression d'une source de données partagée. Toutefois, si vous supprimez par erreur une source de données partagée, vous pouvez en créer une autre en utilisant les mêmes valeurs de propriété que celles de la source que vous avez supprimée. Vous devrez ouvrir chaque rapport, modèle et abonnement piloté par les données pour relier la source de données partagée à l'élément qui l'utilise, mais tant que les propriétés de source de données sont les mêmes qu'avant, les rapports, modèles et abonnements continueront de fonctionner comme avant.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer et gérer des sources de données partagées &#40;Reporting Services en mode intégré SharePoint&#41;](../create-manage-shared-data-sources-reporting-services-sharepoint-integrated-mode.md)   
 [Connexions de données, Sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Gérer des sources de données de rapports](manage-report-data-sources.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md)   
 [Connexions de données ou sources de données incorporées et partagées &#40;Générateur de rapports et SSRS&#41;](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [Page des propriétés des sources de données &#40;Gestionnaire de rapports&#41;](../data-sources-properties-page-report-manager.md)   
 [Créer, supprimer ou modifier une source de données partagée &#40;Gestionnaire de rapports&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Configurer les propriétés de la source de données d’un rapport &#40;Gestionnaire de rapports&#41;](configure-data-source-properties-for-a-report-report-manager.md)  
  
  
