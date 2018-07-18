---
title: Créer et gérer des abonnements pour les serveurs de rapports en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], managing
ms.assetid: 7f46cbdb-5102-4941-bca2-5e0ff9012c6b
caps.latest.revision: 37
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 56fb4e61fe7e442247fb9977afc440f13e5276e6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37186176"
---
# <a name="create-and-manage-subscriptions-for-native-mode-report-servers"></a>Créer et gérer des abonnements pour les serveurs de rapports en mode natif
  Cette section contient des rubriques sur le traitement, la supervision et le contrôle des abonnements. La gestion des abonnements varie selon qu'il s'agit d'abonnements standard ou pilotés par les données. Les abonnements standard sont généralement gérés par les utilisateurs qui en sont également les propriétaires. En revanche, les abonnements pilotés par les données sont généralement créés par un administrateur de serveur de rapports, qui en assure également la maintenance.  
  
 Les fonctionnalités d'abonnement et de remise sont activées par défaut (la remise par messagerie électronique nécessite une configuration préalable). Les extensions de remise par défaut comprennent la remise par partage de fichiers et la remise par messagerie électronique du serveur de rapports. À moins de créer ou d'installer des extensions de remise personnalisées, ces méthodes de distribution sont les seules disponibles pour les abonnements sur un serveur de rapports en mode natif.  
  
## <a name="permissions-for-subscribing-to-reports-on-a-native-mode-report-server"></a>Autorisations d'abonnement aux rapports d'un serveur de rapports en mode natif  
 Suivant la façon dont vous utilisez les rôles, vous pouvez octroyer à certains groupes d'utilisateurs la possibilité de s'abonner en activant ou en désactivant les tâches d'abonnement pour différents rôles. Les fonctionnalités d'abonnement sont accessibles par le biais de deux tâches :  
  
-   La tâche « Gérer les abonnements individuels » permet aux utilisateurs de créer, de modifier et de supprimer les abonnements d'un rapport spécifique. Dans les rôles prédéfinis, cette tâche fait partie des rôles Navigateur et Générateur de rapports. Les attributions de rôles incluant cette tâche autorisent un utilisateur à gérer uniquement les abonnements qu'il crée.  
  
-   La tâche « Gérer tous les abonnements » permet aux utilisateurs d'accéder à tous les abonnements pour les modifier. Cette tâche est obligatoire pour créer des abonnements pilotés par les données. Dans les rôles prédéfinis, seul le rôle Gestionnaire de contenu inclut cette tâche.  
  
## <a name="disabling-subscriptions"></a>Désactivation des abonnements  
 Désactivez la tâche « Gérer les abonnements individuels » du rôle pour retirer aux utilisateurs la possibilité de créer des abonnements. Lorsque vous supprimez cette tâche, les pages Abonnements ne sont plus disponibles. Dans le Gestionnaire de rapports, la page Mes abonnements semble vide (il est impossible de la supprimer) même si elle contenait auparavant des abonnements. La suppression de tâches liées à des abonnements empêche les utilisateurs de créer et de modifier des abonnements, mais elle ne supprime pas les abonnements existants. Ces abonnements continuent de s'exécuter tant qu'ils ne sont pas supprimés. Pour plus d’informations sur la suppression des abonnements, consultez [créer, modifier et supprimer des abonnements Standard &#40;Reporting Services en Mode natif&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md).  
  
 Pour désactiver le traitement des abonnements sur un serveur de rapports, vous pouvez définir le `ScheduleEventsAndReportDeliveryEnabled` propriété `False` dans le **Configuration de Surface d’exposition pour Reporting Services** facette de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] basée sur des stratégies de gestion. Vous empêcherez ainsi l'exécution de toutes les opérations planifiées. Vous ne pouvez pas désactiver seulement le traitement des abonnements sur le serveur de rapports.  
  
 Pour obtenir des instructions sur la façon d’annuler l’abonnement est en cours sur le serveur de rapports, consultez [gérer un processus en cours d’exécution](subscriptions/manage-a-running-process.md).  
  
## <a name="disabling-delivery-extensions"></a>Désactivation des extensions de remise  
 Toutes les extensions de remise installées sur un serveur de rapports sont disponibles pour tout utilisateur autorisé à créer un abonnement à un rapport donné. Les extensions de remise suivantes sont disponibles et configurées automatiquement :  
  
-   Partage de fichiers Windows  
  
-   Bibliothèque SharePoint (disponible uniquement à partir d'un site SharePoint intégré à un serveur de rapports en mode intégré SharePoint)  
  
 La remise par messagerie électronique doit être configurée avant de pouvoir être utilisée. Si vous ne la configurez pas, elle n'est pas disponible. Pour plus d’informations, consultez [configurer un serveur de rapports pour la remise du courrier électronique &#40;Gestionnaire de Configuration de SSRS&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 Si vous souhaitez désactiver des extensions spécifiques, vous pouvez supprimer les entrées d'extension appropriées dans le fichier RSReportServer.config. Pour plus d’informations, consultez [fichier de Configuration RSReportServer](report-server/rsreportserver-config-configuration-file.md) et [configurer un serveur de rapports pour la remise du courrier électronique &#40;Gestionnaire de Configuration de SSRS&#41;](../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 Lorsqu'une extension de remise est supprimée, elle n'est plus disponible dans le Gestionnaire de rapports, ni dans un site SharePoint. La suppression d'une extension de remise peut engendrer des abonnements inactifs. Avant de supprimer une extension, prenez soin de supprimer ces abonnements ou configurez-les pour qu'ils utilisent une autre extension de remise.  
  
## <a name="in-this-section"></a>Contenu de cette section  
 [Utiliser Mes abonnements](subscriptions/use-my-subscriptions-native-mode-report-server.md)  
 Explique comment utiliser la page Mes abonnements pour gérer les abonnements dont vous êtes propriétaire.  
  
 [Suspendre le traitement des rapports et des abonnements](subscriptions/disable-or-pause-report-and-subscription-processing.md)  
 Décrit les différentes méthodes permettant de suspendre le traitement des rapports, comme l'utilisation des attributions de rôle ou la désactivation des ressources du serveur de rapports.  
  
 [Contrôler la distribution des rapports](../../2014/reporting-services/control-report-distribution.md)  
 Décrit les paramètres de configuration et les options de remise que vous pouvez utiliser pour contrôler la distribution des rapports.  
  
 [Analyser les abonnements Reportions Services](subscriptions/monitor-reporting-services-subscriptions.md)  
 Décrit comment vous pouvez déterminer si un abonnement a réussi ou échoué, ainsi que les effets des modifications apportées aux rapports sur les abonnements existants.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer, modifier et supprimer des abonnements Standard &#40;Reporting Services en Mode natif&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md)  
  
  
