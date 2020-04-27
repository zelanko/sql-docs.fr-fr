---
title: Page mes abonnements (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 491a85a3-f323-4155-a0a8-de2779899995
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 75d662f677ee2b6bbab8e445804ca7f142b5c034
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66108188"
---
# <a name="my-subscriptions-page-report-manager"></a>Page Mes abonnements (Gestionnaire de rapports)
  La page Mes abonnements vous permet d'afficher tous vos abonnements à un seul emplacement. À partir de cette page, vous pouvez accéder à vos propres abonnements et les modifier ou les supprimer. Vous ne possédez que les abonnements que vous créez. En revanche, vous ne pouvez pas accéder aux abonnements des autres utilisateurs ou à ceux que vous utilisez mais dont vous n'êtes pas propriétaire (par exemple, si votre nom a été ajouté à un abonnement existant défini par un autre utilisateur). Vous ne pouvez pas créer d'abonnements à partir de cette page. Pour plus d’informations sur la création d’abonnements, consultez la [page nouvel abonnement ou modifier l’abonnement &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/new-subscription-or-edit-subscription-page-report-manager.md).  
  
 Par défaut, les abonnements sont triés par ordre alphabétique (par nom de rapport). Cliquez sur un autre en-tête de colonne pour modifier l'ordre de tri des abonnements. Si vous ne possédez pas d'abonnements ou si vous n'êtes pas autorisé à créer ou gérer des abonnements, aucun abonnement n'apparaît dans la page.  
  
> [!NOTE]  
>  Cette fonctionnalité n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="navigation"></a>Navigation  
 Utilisez la procédure suivante pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
### <a name="to-open-the-my-subscriptions-page"></a>Pour ouvrir la page Mes abonnements  
  
1.  Ouvrez le Gestionnaire de rapports.  
  
2.  En haut de la page, dans l'angle droit, cliquez sur Mes abonnements.  
  
    > [!NOTE]  
    >  Mes abonnements est toujours disponible, même si vous n'êtes pas autorisé à créer des abonnements.  
  
## <a name="options"></a>Options  
 **Supprimer**  
 Activez la case à cocher en regard de chaque abonnement à supprimer, puis cliquez sur **Supprimer**.  
  
 **Modifier**  
 Cliquez pour afficher ou modifier la description.  
  
 **Rapport**  
 Affiche le rapport défini dans l'abonnement. Cliquez sur le nom du rapport pour afficher ce dernier.  
  
 **Description**  
 Affiche une description de l'abonnement. Cliquez sur la description pour afficher ou modifier les informations sur l'abonnement du rapport.  
  
 **Répertoire**  
 Affiche le dossier qui contient le rapport défini dans l'abonnement. Cliquez sur le nom du dossier pour afficher le contenu de ce dernier.  
  
 **Déclencheur**  
 Identifie les critères qui entraînent l'exécution de l'abonnement. Un déclencheur **TimedSubscription** est basé sur une planification qui définit à quel moment l'abonnement s'exécute. Un déclencheur **SnapshotUpdated** est basé sur une mise à jour d'un instantané de rapport.  
  
 **Dernière exécution**  
 Indique à quel moment a eu lieu le dernier traitement de l'abonnement.  
  
 **État**  
 Indique l'état de l'abonnement En règle générale, l'état est « Nouveau » ou correspond à la date et à l'heure de la dernière exécution de l'abonnement.  
  
 La valeur d'état « Données incorrectes » se présente lorsque l'abonnement comporte un pointeur vers des valeurs chiffrées qui ne sont plus valides, c'est-à-dire vers les informations d'identification utilisées pour exécuter le rapport). Les valeurs chiffrées existantes deviennent inutilisables lorsque les clés symétriques utilisées pour chiffrer et déchiffrer les données sont recréées sur le serveur de rapports.  
  
 Il n'est pas possible de traiter un abonnement s'il a été désactivé. Pour mettre à jour l'abonnement et le rendre opérationnel, ouvrez-le, puis enregistrez-le.  
  
## <a name="see-also"></a>Voir aussi  
 [Abonnements et remise &#40;Reporting Services&#41;](subscriptions/subscriptions-and-delivery-reporting-services.md)   
 [Aide F1 du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
