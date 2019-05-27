---
title: Page abonnements (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: cf3a6bd0-e0b2-4875-a532-63ef34cfa860
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: eec92d7c58b68b14374666f65489f145fa863422
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66101090"
---
# <a name="subscriptions-page-report-manager"></a>Page Abonnements (Gestionnaire de rapports)
  La page Abonnements vous permet de répertorier tous les abonnements de la source de données partagée ou du rapport actifs. Si vous disposez d'une autorisation suffisante (accordée par la tâche « Gérer tous les abonnements », par exemple), vous pouvez afficher les abonnements de tous les utilisateurs. Si ce n'est pas le cas, cette page affiche uniquement les abonnements dont vous être propriétaire.  
  
> [!NOTE]  
>  D'autres pages contiennent également des informations sur les abonnements. Pour plus d’informations, consultez [Page Mes abonnements &#40;le Gestionnaire de rapports&#41; ](../../2014/reporting-services/my-subscriptions-page-report-manager.md) pour accéder à tous vos abonnements au même endroit ou la [nouvel abonnement ou modifier la Page d’abonnement &#40;le Gestionnaire de rapports&#41; ](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md) pour créer ou modifier un abonnement.  
  
 Certaines options ne sont disponibles que s'il existe des abonnements. Si aucun abonnement n'est défini et si vous accédez à cette page à partir d'un rapport, les options **Nouvel abonnement** et **Nouvel abonnement piloté par les données** sont les seules disponibles dans la page.  
  
 Avant de créer un abonnement, vous devez vérifier que la source de données du rapport utilise des informations d'identification stockées. Utilisez la page des propriétés des sources de données pour stocker des informations d'identification. Pour plus d’informations, consultez [Page de propriétés de Sources de données &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md).  
  
> [!NOTE]  
>  Cette fonctionnalité n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
### <a name="to-open-the-subscriptions-page-for-report"></a>Pour ouvrir la page Abonnements pour le rapport  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez afficher ou configurer un abonnement.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page des propriétés générales pour le rapport s'ouvre.  
  
4.  Sélectionnez l'onglet **Abonnements** .  
  
## <a name="options"></a>Options  
 **Supprimer**  
 Cliquez pour supprimer un abonnement. Avant de cliquer sur ce bouton, activez la case à cocher en regard de chaque abonnement que vous souhaitez supprimer.  
  
 **Nouvel abonnement**  
 Cliquez pour créer un abonnement au rapport actif. Ce bouton est activé lorsque le rapport utilise des informations d'identification stockées ou aucune information d'identification. Il n'est pas disponible lorsque vous ouvrez la page Abonnements pour une source de données partagée.  
  
 **Nouvel abonnement piloté par les données**  
 Cliquez pour générer une liste d'abonnés et des options de remise à partir d'une commande ou d'une requête exécutée sur une banque de données qui contient ces informations. Ce bouton est activé lorsque le rapport utilise des informations d'identification stockées ou aucune information d'identification. Il n'est pas disponible lorsque vous ouvrez la page Abonnements pour une source de données partagée.  
  
 **Modifier**  
 Cliquez pour afficher ou modifier la description.  
  
 **Rapport**  
 Lorsque vous ouvrez cette page à partir d'une source de données partagée, cette colonne identifie le rapport pour lequel l'abonnement est défini. La colonne **Dossier** identifie l'emplacement du rapport.  
  
 **Description**  
 Affiche une description de l'abonnement.  
  
 **Déclencheur**  
 Identifie les critères qui entraînent l'exécution de l'abonnement. Un déclencheur **TimedSubscription** est basé sur une planification qui définit à quel moment l'abonnement s'exécute. Un déclencheur **SnapshotUpdated** est basé sur une mise à jour d'un instantané de rapport.  
  
 **Propriétaire**  
 Affiche le nom de l'utilisateur qui a créé l'abonnement.  
  
 **Dernière exécution**  
 Indique à quel moment a eu lieu le dernier traitement de l'abonnement.  
  
 **État**  
 Indique l'état de l'abonnement Généralement, la valeur d'état est Nouveau ou la date et l'heure de dernière exécution de l'abonnement.  
  
 La valeur d'état « Données incorrectes » se présente lorsque l'abonnement comporte un pointeur vers des valeurs chiffrées qui ne sont plus valides, c'est-à-dire vers les informations d'identification utilisées pour exécuter le rapport). Les valeurs chiffrées existantes deviennent inutilisables lorsque les clés symétriques utilisées pour chiffrer et déchiffrer les données sont recréées sur le serveur de rapports.  
  
 Il n'est pas possible de traiter un abonnement s'il a été désactivé. Pour mettre à jour l'abonnement et le rendre opérationnel, ouvrez-le, puis enregistrez-le.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Créer, modifier et supprimer des abonnements Standard &#40;Reporting Services en Mode natif&#41;](subscriptions/create-and-manage-subscriptions-for-native-mode-report-servers.md)   
 [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md)   
 [Aide (F1) du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
