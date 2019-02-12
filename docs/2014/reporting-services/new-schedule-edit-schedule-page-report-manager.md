---
title: 'Nouvelle planification : Modifier la planification Page (Gestionnaire de rapports) | Microsoft Docs'
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 52a4d250-e185-4116-a29c-d809940a00fb
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 97af25216bd0f1e30531fcb43e182672cd299ac6
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56034544"
---
# <a name="new-schedule-edit-schedule-page-report-manager"></a>Nouvelle planification : Modifier la Page de planification (Gestionnaire de rapports)
  La page Nouvelle planification / Modifier la planification permet de créer une planification pour un rapport. Les planifications sont utilisées avec des abonnements. Elles permettent en outre d'actualiser des rapports mis en cache et de créer des instantanés en tant qu'éléments autonomes ou dans un historique de rapport.  
  
> [!NOTE]  
>  Cette fonctionnalité n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
 Vous ne pouvez créer des planifications que pour les rapports qui peuvent s'exécuter sans assistance. L'exécution d'un rapport sans assistance requiert que vous stockiez les informations d'identification de la source de données de rapport dans la base de données du serveur de rapports. Pour plus d’informations, consultez [Page de propriétés de Sources de données &#40;le Gestionnaire de rapports&#41;](../../2014/reporting-services/data-sources-properties-page-report-manager.md).  
  
 Toutes les combinaisons de fréquence ne peuvent pas être prises en charge dans une seule planification. Par exemple, si vous souhaitez exécuter un rapport à 12:00 et 16:00 ous les vendredis, vous devez créer deux planifications quotidiennes qui spécifient le vendredi comme jour d'exécution mais avec une heure de début de 12:00 pour l'une et une heure de début de 16:00 pour la seconde.  
  
 Le traitement de la planification est basé sur l'heure locale du serveur de rapports qui héberge et traite la planification.  
  
## <a name="navigation"></a>Navigation  
 Utilisez les procédures suivantes pour naviguer jusqu'à cet emplacement dans l'interface utilisateur.  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-execution-properties-page-of-a-report"></a>Pour ouvrir la page Nouvelle planification ou Modifier la planification dans la page de propriétés Exécution d'un rapport  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez configurer une planification.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page Propriétés générales pour le modèle s'ouvre.  
  
4.  Sélectionnez l'onglet **Exécution** .  
  
5.  Sélectionnez l'option **Effectuer le rendu de ce rapport à partir d'un instantané de rapport**. Sélectionnez ensuite **Utilisez la planification ci-dessous pour ajouter des instantanés à l'historique de rapport**, puis **Planification spécifique aux rapports**. Puis cliquez sur **Configurer**.  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-history-properties-page-of-a-report"></a>Pour ouvrir la page Nouvelle planification ou Modifier la planification dans la page de propriétés Historique d'un rapport  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez configurer une planification.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant, cliquez sur **Gérer**. La page Propriétés générales pour le modèle s'ouvre.  
  
4.  Sélectionnez l'onglet **Historique** .  
  
5.  Sélectionnez **Utilisez la planification ci-dessous pour ajouter des instantanés à l'historique de rapport**, puis **Planification spécifique aux rapports**. Puis cliquez sur **Configurer**.  
  
### <a name="to-open-the-new-schedule-or-edit-schedule-page-from-the-subscriptions-page"></a>Pour ouvrir la page Nouvelle planification ou Modifier la planification dans la page Abonnements  
  
1.  Ouvrez le Gestionnaire de rapports et recherchez le rapport pour lequel vous souhaitez configurer une planification.  
  
2.  Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
3.  Dans le menu déroulant,  
  
    -   Cliquez sur **Gérer**. La page des propriétés générales pour le rapport s'ouvre. Sélectionnez ensuite l'onglet **Abonnements** .  
  
    -   Cliquez sur **S'abonner**. La page de propriétés **Abonnements** du rapport s'ouvre.  
  
4.  Dans la barre d'outils, cliquez sur **Nouvel abonnement** ou sélectionnez un abonnement existant à modifier.  
  
5.  Sous **Options de traitement d'abonnement**, cliquez sur **Nouvelle planification**.  
  
## <a name="options"></a>Options  
 **Détails de la planification**  
 Sélectionnez les options qui déterminent la fréquence et le moment d'exécution d'un rapport. Les options de fréquence sont en couche. Le premier ensemble d'options spécifie une catégorie de fréquences (toutes les heures, tous les jours, toutes les semaines, etc.) Le second ensemble d'options qui apparaît dépend de votre sélection initiale.  
  
-   **Heure** définit une planification qui s'exécute toutes les heures. Utilisez la section **Dates de début et de fin** pour spécifier le jour d'exécution de la planification.  
  
-   **Jour** définit une planification qui s'exécute les jours sélectionnés à une heure spécifique. Vous pouvez spécifier les jours comme suit : Chaque \< *jour*>, tous les jours ouvrables et chaque \< *nombre*> jours. La sélection d'une option rend les autres inapplicables même si d'autres jours semblent sélectionnés.  
  
-   **Semaine** définit une planification qui s'exécute toutes les semaines à une heure spécifique. L'intervalle peut correspondre à des semaines entières (toutes les deux semaines, par exemple) ou à des jours compris dans la semaine.  
  
-   **Mois** définit une planification qui s'exécute tous les mois. Dans un mois, vous pouvez choisir un jour basé sur un modèle (le dernier dimanche de chaque mois, par exemple) ou des dates spécifiques (tels que 1 et 15 pour indiquer le 1er et le 15e jour de chaque mois). À l'aide de virgules et de tirets, vous pouvez spécifier plusieurs jours et plages (1, 5, 7-12, 21, par exemple).  
  
-   **Une fois** définit une planification qui s'exécute une seule fois. Utilisez la section **Dates de début et de fin** pour spécifier le jour d'exécution de la planification. La planification expire dès qu'elle a été traitée.  
  
 **Dates de début et de fin**  
 Spécifie une date de début qui détermine à quel moment la planification prend effet et une date de fin qui détermine à quel moment la planification expire.  
  
 Les planifications expirent sans notification. Après la date de fin, elles ne s'exécutent plus. Les planifications expirées ne sont pas supprimées. Elles ne peuvent être supprimées que manuellement. Ainsi, si vous choisissez de continuer à utiliser la planification, vous pouvez rallonger la date de fin.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md)   
 [Aide (F1) du Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
