---
title: Créer, modifier et supprimer des planifications | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services]
- modifying schedules
- removing schedules
- shared schedules [Reporting Services], creating
- shared schedules [Reporting Services], modifying
- schedules [Reporting Services], deleting
- deleting schedules
- schedules [Reporting Services], creating
- schedules [Reporting Services], modifying
- shared schedules [Reporting Services], deleting
ms.assetid: 05da5f3d-9222-43a9-893b-aa10f0f690f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 177450ed6cbe934406fc596606e0bb13ee51f7eb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62511019"
---
# <a name="create-modify-and-delete-schedules"></a>Create, Modify, and Delete Schedules
  Cette rubrique est consacrée à la création, la modification et la suppression des planifications.  
  
 Dans cette rubrique :  
  
-   [Présentation de la gestion des planifications partagées](#bkmk_overview)  
  
-   [Créer et gérer des planifications partagées (Mode SharePoint)](#bkmk_sharepoint)  
  
-   [Créer et gérer des planifications partagées (Mode natif)](#bkmk_native)  
  
##  <a name="bkmk_overview"></a> Présentation de la gestion des planifications partagées  
 Pour gérer des planifications partagées en mode natif, utilisez la page Planifications dans le Gestionnaire de rapports ou le dossier Planifications partagées dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Pour le mode SharePoint, utilisez les pages de gestion pour l'application de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Vous pouvez voir toutes les planifications partagées qui sont définies pour le serveur de rapports, suspendre et reprendre des planifications (uniquement dans le Gestionnaire de rapports), et sélectionner les planifications à modifier ou à supprimer. La page Planifications partagées résume les informations suivantes concernant l'état de chaque planification : fréquence, propriétaire, date d'expiration et état.  
  
 Vous pouvez déterminer si une planification partagée est utilisée de manière active, en procédant comme suit :  
  
-   Vérifiez les valeurs des champs Date de la dernière exécution, Date de la prochaine exécution et État dans la page Planifications partagées. Si une planification ne s'exécute plus parce qu'elle est arrivée à expiration, la date d'expiration apparaît dans le champ État.  
  
-   Consultez la page Rapports d'une planification partagée donnée. Cette page répertorie tous les rapports et datasets partagés qui utilisent la planification partagée.  
  
-   Affichez les journaux des traces ou les fichiers journaux des exécutions des rapports afin de déterminer si ces derniers se sont exécutés aux heures spécifiées dans la planification. Pour plus d’informations, consultez [Fichiers journaux et sources de Reporting Services](../report-server/reporting-services-log-files-and-sources.md).  
  
##  <a name="bkmk_sharepoint"></a> Créer et gérer des planifications partagées (mode SharePoint)  
 Une planification partagée est une planification à usage général qui fournit des informations de planification prêtes à l'emploi à un nombre quelconque de rapports ou d'abonnements. Vous créez une planification partagée, puis vous la référencez dans un abonnement ou dans une page de propriétés lorsque vous avez besoin d'informations de planification. La gestion, la suspension et la reprise des planifications partagées peuvent être centralisées. En revanche, vous devez modifier manuellement une planification personnalisée pour empêcher l'exécution d'un rapport ou d'un abonnement.  
  
 Vous devez être un administrateur de site pour pouvoir créer, modifier ou supprimer les planifications partagées d'un site SharePoint.  
  
 Vous pouvez identifier une planification spécifique par son nom descriptif. Si aucun nom n'est spécifié, un nom par défaut est créé à partir des informations qui se rapportent à la planification, par exemple sa périodicité ou ses dates et heures d'exécution.  
  
> [!NOTE]  
>  La création de planifications partagées requiert le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
### <a name="create-shared-schedules-sharepoint"></a>Créer des planifications partagées (SharePoint)  
  
##### <a name="to-create-shared-schedules"></a>Pour créer des planifications partagées  
  
1.  Cliquez sur **Actions du site**.  
  
2.  Cliquez sur **Paramètres du site**.  
  
3.  Dans la section Reporting Services, cliquez sur **Gérer les planifications partagées**.  
  
4.  Cliquez sur **Ajouter une planification** pour ouvrir la page Propriétés de planification.  
  
5.  Entrez un nom descriptif pour la planification. Dans les pages d’application utilisées pour travailler avec des rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , ce nom apparaît dans les listes déroulantes des pages de définition de la planification sur l’ensemble du site. Évitez les noms longs difficiles à lire. Efforcez-vous de respecter une convention d'affectation des noms pour fournir la plus grande partie des informations descriptives au début du nom.  
  
6.  Choisissez une fréquence. Selon la fréquence choisie, les options de planification qui s’affichent sur la page peuvent varier pour prendre en charge cette fréquence (par exemple, si vous choisissez **Mois**, le nom de chaque mois s’affiche sur la page).  
  
7.  Définissez la planification. Toutes les combinaisons de planification ne peuvent pas être prises en charge dans une seule planification.  
  
8.  Définissez une date de début et de fin.  
  
9. Cliquez sur **OK**.  
  
### <a name="delete-shared-schedules-sharepoint"></a>Supprimer des planifications partagées (SharePoint)  
 Toutes les planifications, qu'elles soient partagées ou spécifiques aux rapports, doivent être supprimées manuellement. Si vous supprimez une planification partagée en cours d'utilisation, toutes les références à cette dernière sont remplacées par des planifications personnalisées non spécifiées (c'est-à-dire des planifications personnalisées qui n'ont pas d'informations de date et d'heure).  
  
 Le fait de supprimer une planification et le fait de provoquer son expiration sont deux opérations différentes. Une date d'expiration sert à arrêter une planification, mais ne la supprime pas. Comme les planifications servent à automatiser les opérations du serveur de rapports, elles ne sont jamais supprimées automatiquement. Les planifications expirées fournissent aux administrateurs de serveurs de rapports des éléments de preuve quant à la cause de l'arrêt subit d'un processus automatisé. Sans la planification expirée, un administrateur de serveur de rapports pourrait faire une erreur de diagnostic pour un problème ou perdre du temps à tenter de résoudre un processus qui fonctionne parfaitement.  
  
 Une planification personnalisée qui a expiré reste associée au rapport. Vous pouvez déterminer si une planification est arrivée à expiration en vérifiant sa date de fin. Une planification partagée expirée reste dans la liste des planifications partagées. Le champ État indique si la planification est arrivée à expiration. Vous pouvez rétablir la planification en reportant la date de fin ou vous pouvez supprimer la référence à la planification si vous n'en n'avez plus besoin.  
  
##### <a name="to-delete-a-shared-schedule"></a>Pour supprimer une planification partagée  
  
1.  Cliquez sur **Actions du site**.  
  
2.  Cliquez sur **Paramètres du site**.  
  
3.  Dans la section Reporting Services, cliquez sur **Gérer les planifications partagées**.  
  
4.  Sélectionnez la planification, puis cliquez sur **Supprimer**.  
  
##  <a name="bkmk_native"></a> Créer et gérer des planifications partagées (Mode natif)  
 Les planifications partagées doivent être supprimées manuellement via la page Planifications du Gestionnaire de rapports ou le dossier Planifications partagées dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Si vous supprimez une planification partagée qui est en cours d'utilisation, toutes les références à cette planification sont remplacées par des planifications spécifiques aux rapports.  
  
 Les planifications spécifiques à un rapport ou un abonnement sont supprimées lorsque vous supprimez le rapport ou l'abonnement, ou lorsque vous choisissez une autre approche pour exécuter le rapport ou l'abonnement. Par exemple, si vous choisissez **Toujours exécuter ce rapport avec les données les plus récentes** , la planification spécifique aux rapports que vous avez créée pour exécuter un rapport en tant qu'instantané d'exécution de rapport est supprimée.  
  
 Le fait de supprimer une planification et le fait de provoquer son expiration sont deux opérations différentes. Une date d'expiration sert à arrêter une planification, mais ne la supprime pas. Comme les planifications servent à automatiser un grand nombre de fonctionnalités, elles ne sont jamais supprimées automatiquement. Les planifications expirées fournissent aux administrateurs de serveurs de rapports des éléments de preuve quant à la cause de l'arrêt subit d'un processus automatisé. Sans la présence de la planification expirée, un administrateur de serveur de rapports peut faire une erreur de diagnostic pour un problème ou perdre inutilement du temps à tenter de dépanner un processus qui fonctionne parfaitement.  
  
 Une planification spécifique aux rapports arrivée à expiration reste associée au rapport. Vous pouvez déterminer si une planification est arrivée à expiration en vérifiant sa date de fin. Une planification partagée expirée reste dans la liste des planifications partagées. Le champ État indique si la planification est arrivée à expiration. Vous pouvez rétablir la planification en reportant la date de fin ou vous pouvez supprimer la référence à la planification si vous n'en n'avez plus besoin.  
  
### <a name="create-delete-or-modify-a-shared-schedule-report-manager"></a>Créer, supprimer ou modifier une planification partagée (Gestionnaire de rapports)  
 La création et la modification d'une planification consiste à définir des options de fréquence qui déterminent le moment d'exécution de la planification.  
  
-   Les planifications partagées sont créées en tant qu'éléments distincts. Après les avoir créées, vous les référencez lors de la définition d'un abonnement ou de toute autre opération planifiée.  
  
-   Les planifications spécifiques aux rapports sont créées lorsque vous définissez un abonnement ou configurez des propriétés d'exécution de rapport. L'entrée des informations de planification fait partie de la définition d'un abonnement ou du paramétrage des propriétés. Pour définir une planification spécifique aux rapports, ouvrez le rapport ou l'abonnement qui l'utilise.  
  
 Une planification partagée contient les informations de planification et de périodicité qui peuvent être utilisées par tous les rapports publiés et abonnements qui s'exécutent sur un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Si de nombreux rapports et abonnements s'exécutent en même temps, vous pouvez créer une planification partagée pour ces travaux. Si vous souhaitez modifier ultérieurement la périodicité ou la date de fin, vous pouvez effectuer cette modification à un seul emplacement.  
  
 La maintenance des planifications partagées est plus facile à assurer ; par ailleurs, ces dernières vous apportent une plus grande souplesse de gestion des opérations planifiées. Par exemple, vous pouvez suspendre et reprendre des planifications partagées. En outre, si vous trouvez que trop d'opérations planifiées s'exécutent en même temps, vous pouvez créer plusieurs planifications partagées qui s'exécutent à des heures différentes, puis vous pouvez ajuster les informations de planification de sorte que la charge de traitement soit répartie de manière égale sur le serveur de rapports.  
  
 Vous pouvez créer ou modifier une planification à n'importe quel moment. Toutefois, si une planification commence à s'exécuter avant que vous n'ayez terminé vos modifications, la version précédente de la planification est utilisée. La planification révisée ne prend pas effet tant que vous ne l'avez pas enregistrée.  
  
 Si vous modifiez une planification partagée, vous pouvez la suspendre avant d'apporter des modifications. Les modifications prennent effet lorsque vous reprenez la planification.  
  
##### <a name="to-create-or-modify-a-shared-schedule-report-manager"></a>Pour créer ou modifier une planification partagée (Gestionnaire de rapports)  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Dans le Gestionnaire de rapports, cliquez sur **Paramètres du site**dans la barre d’outils globale.  
  
3.  Cliquez sur **Planifications**.  
  
4.  Cliquez sur **Nouvelle planification**. Pour modifier une planification existante, cliquez sur son nom.  
  
5.  Tapez un nom descriptif pour la planification.  
  
6.  Sélectionnez **Heure**, **Jour**, **Semaine**ou **Mois**. Cliquez sur **Une fois** pour créer une planification qui ne s'exécute qu'une seule fois. Des options supplémentaires s'affichent lorsque vous spécifiez la base de votre planification.  
  
7.  Si vous le souhaitez, sélectionnez une date de début pour la planification. Par défaut, il s'agit de la date du jour. Vous pouvez reporter le début de la planification en choisissant une date ultérieure.  
  
8.  Sélectionnez éventuellement une date de fin de planification. La planification cesse de s'exécuter à la date indiquée, mais elle n'est pas supprimée.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-report-manager"></a>Pour supprimer une planification partagée (Gestionnaire de rapports)  
  
1.  Dans le Gestionnaire de rapports, cliquez sur **Paramètres du site**dans la barre d’outils globale.  
  
    > [!NOTE]  
    >  Si l'option **Paramètres du site** n'est pas disponible, vous n'êtes pas autorisé à modifier ces paramètres.  
  
2.  Dans la section **Autre** de cette page, cliquez sur **Gérer les planifications partagées**.  
  
3.  Activez la case à cocher située en regard de la planification à supprimer, puis cliquez sur **Supprimer**.  
  
 Si vous supprimez une planification partagée utilisée par plusieurs rapports et abonnements, le serveur de rapports créera des planifications individuelles pour chaque rapport et abonnement qui a précédemment utilisé la planification partagée. Chaque nouvelle planification individuelle contiendra la date, l'heure et la périodicité spécifiée dans la planification partagée. Notez que [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne fournit pas de gestion centrale des planifications individuelles. Si vous supprimez une planification partagée, vous devez désormais gérer les informations de planification pour chaque élément individuel.  
  
 Si vous n'êtes pas sûr qu'une planification partagée soit utilisée, envisagez plutôt de la supprimer dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] . [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] fournit les mêmes fonctionnalités de gestion des planifications partagées que le Gestionnaire de rapports, mais il fournit également une page Rapports supplémentaire qui indique le nom de chaque rapport utilisant la planification.  
  
### <a name="create-delete-or-modify-a-shared-schedule-management-studio"></a>Créer, supprimer ou modifier une planification partagée (Management Studio)  
 Une planification partagée contient les informations de planification et de périodicité qui peuvent être utilisées par tous les rapports publiés et abonnements qui s'exécutent sur un serveur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Si de nombreux rapports et abonnements s'exécutent en même temps, vous pouvez créer une planification partagée pour ces travaux. Si vous souhaitez modifier ultérieurement la périodicité ou la date de fin, vous pouvez effectuer cette modification à un seul emplacement.  
  
 La maintenance des planifications partagées est plus facile à assurer ; par ailleurs, ces dernières vous apportent une plus grande souplesse de gestion des opérations planifiées. Par exemple, vous pouvez suspendre et reprendre des planifications partagées. En outre, si vous trouvez que trop d'opérations planifiées s'exécutent en même temps, vous pouvez créer plusieurs planifications partagées qui s'exécutent à des heures différentes, puis vous pouvez ajuster les informations de planification de sorte que la charge de traitement soit répartie de manière égale sur le serveur de rapports.  
  
##### <a name="to-create-or-modify-a-shared-schedule-management-studio"></a>Pour créer ou modifier une planification partagée (Management Studio)  
  
1.  Démarrez SQL Server Management Studio et connectez-vous à une instance du serveur de rapports.  
  
2.  Dans l'Explorateur d'objets, développez un nœud du serveur de rapports.  
  
3.  Cliquez avec le bouton droit sur le dossier Planifications partagées, puis cliquez sur **Nouvelle planification**. La page Général de la boîte de dialogue **Nouvelle planification partagée** s'affiche.  
  
     Pour modifier une planification partagée existante, développez le dossier Planifications partagées, cliquez avec le bouton droit sur la planification à modifier, puis cliquez sur **Propriétés**.  
  
4.  Tapez un nom descriptif pour la planification.  
  
5.  Si vous le souhaitez, sélectionnez une date de début pour la planification. Par défaut, il s'agit de la date du jour.  
  
6.  Si vous le souhaitez, sélectionnez une date de fin pour la planification. La planification cesse de s'exécuter à la date indiquée, mais elle n'est pas supprimée.  
  
7.  Pour configurer une planification périodique, sélectionnez **Heure**, **Jour**, **Semaine**ou **Mois**. Des options supplémentaires s'affichent. Utilisez ces options supplémentaires pour configurer la périodicité de la planification, en fonction de vos préférences selon l'heure, le jour, la semaine ou le mois.  
  
     Sinon, pour spécifier une planification unique (non périodique), sélectionnez **Une fois**, puis spécifiez une **Heure de début**.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-management-studio"></a>Pour supprimer une planification partagée (Management Studio)  
  
1.  Dans l'Explorateur d'objets, développez un nœud du serveur de rapports.  
  
2.  Développez le dossier Planifications partagées, cliquez avec le bouton droit sur la planification à supprimer, puis cliquez sur **Supprimer**. La boîte de dialogue **Suppression des éléments du catalogue** s'affiche.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 Si vous supprimez une planification partagée utilisée par plusieurs rapports et abonnements, le serveur de rapports créera des planifications individuelles pour chaque rapport et abonnement qui a précédemment utilisé la planification partagée. Chaque nouvelle planification individuelle contiendra la date, l'heure et la périodicité spécifiée dans la planification partagée. Notez que [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne fournit pas de gestion centrale des planifications individuelles. Si vous supprimez une planification partagée, vous devez désormais gérer les informations de planification pour chaque élément individuel. Avant de supprimer une planification partagée, utilisez la [page Rapports](../tools/schedule-properties-reports-page.md) pour déterminer les rapports qui l'utilisent actuellement.  
  
## <a name="see-also"></a>Voir aussi  
 [Schedules](schedules.md)   
 [Pause and Resume Shared Schedules](pause-and-resume-shared-schedules.md)   
 [Mettre en cache un rapport &#40;Gestionnaire de rapports&#41;](../report-server/cache-a-report-report-manager.md)   
 [Ajouter un instantané à un historique de rapport &#40;Gestionnaire de rapports&#41;](../report-server/add-a-snapshot-to-report-history-report-manager.md)  
  
  
