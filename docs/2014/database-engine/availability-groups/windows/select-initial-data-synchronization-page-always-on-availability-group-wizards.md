---
title: Sélectionnez la Page de synchronisation des données initiale (Assistants de groupe de disponibilité AlwaysOn) | Documents Microsoft
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.addreplicawizard.selectinitialdatasync.f1
- sql12.swb.adddatabasewizard.selectinitialdatasync.f1
- sql12.swb.newagwizard.selectinitialdatasync.f1
ms.assetid: 457b1140-4819-4def-8f7c-54a406e6db12
caps.latest.revision: 36
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.openlocfilehash: 2c949bd5ec421ac41d602b28af2d087153b0358c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053143"
---
# <a name="select-initial-data-synchronization-page-alwayson-availability-group-wizards"></a>Page Sélectionner la synchronisation de données initiale (assistants de groupe de disponibilité AlwaysOn)
  Utilisez la page AlwaysOn **Sélectionner la synchronisation de données initiale** afin d'indiquer votre préférence pour la synchronisation des données initiale des nouvelles bases de données secondaires. Cette page est commune à trois Assistants : [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)]et [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)].  
  
 Les choix possibles sont : **Complet**, **Joindre uniquement**ou **Ignorer la synchronisation de données initiale**. Avant de sélectionner **Complet** ou **Joindre uniquement** , assurez-vous que votre environnement satisfait aux conditions préalables requises.  
  

  
##  <a name="Recommendations"></a> Recommandations  
  
-   Interrompez les tâches de sauvegarde de fichier journal pour les bases de données principales durant la synchronisation de données initiale.  
  
-   Pour les bases de données volumineuses, les opérations de sauvegarde complète et de restauration peuvent prendre beaucoup de temps et solliciter beaucoup de ressources. Dans ce cas, nous vous recommandons de préparer vos bases de données secondaires vous-même. Pour plus d'informations, consultez [Pour préparer manuellement une base de données secondaire](#PrepareSecondaryDbs), plus loin dans cette rubrique.  
  
-   La synchronisation de données initiale complète requiert la spécification d'un partage réseau. Avant d'utiliser un assistant pour effectuer la synchronisation initiale complète des données, nous vous recommandons d'implémenter un plan de sécurité des autorisations d'accès sur le dossier de partage réseau. Cette précaution est importante car les données potentiellement sensibles figurant dans le fichier de sauvegarde peuvent être accessibles par toute personne disposant d'une autorisation en lecture READ sur le dossier. En outre, pour protéger votre opérations de sauvegarde et de restauration, nous vous recommandons de sécuriser les canaux réseau entre chaque instance de serveur qui héberge un réplica de disponibilité et le dossier de partage réseau.  
  
     Si vos opérations de sauvegarde et de restauration nécessitent une sécurisation élevée, nous vous recommandons de sélectionner l'option **Joindre uniquement** ou **Ignorer la synchronisation de données initiale** .  
  
##  <a name="Full"></a> Complet  
 Pour chaque base de données primaire, l'option **Complet** exécute plusieurs opérations dans un flux de travail : création d'une sauvegarde complète et une sauvegarde du journal de la base de données primaire, création des bases de données secondaires correspondantes en restaurant ces sauvegardes sur chaque instance de serveur qui héberge un réplica secondaire et jointure de chaque base de données secondaire à un groupe de disponibilité.  
  
 Sélectionnez cette option uniquement si votre environnement satisfait aux conditions préalables requises qui suivent pour utiliser la synchronisation de données initiale complète, et si vous souhaitez que l'Assistant démarre automatiquement la synchronisation des données.  
  
 **Conditions préalables requises pour utiliser la synchronisation de données initiale complète**  
  
-   Tous les chemins d'accès des fichiers de base de données doivent être identiques sur chaque instance de serveur qui héberge un réplica pour le groupe de disponibilité.  
  
    > [!NOTE]  
    >  Si les chemins d'accès des fichiers de sauvegarde et de restauration diffèrent entre l'instance de serveur sur laquelle vous exécutez l'Assistant et une instance de serveur qui doit héberger un réplica secondaire, les opérations de sauvegarde et de restauration doivent être exécutées manuellement à l'aide de l'option WITH MOVE. Pour plus d'informations, consultez [Pour préparer manuellement une base de données secondaire](#PrepareSecondaryDbs), plus loin dans cette rubrique.  
  
-   Aucun nom de base de données primaire ne peut exister sur une instance de serveur qui héberge un réplica secondaire. Cela signifie qu'aucune des nouvelles bases de données secondaires ne peut exister pour le moment.  
  
-   Vous devez spécifier un partage réseau pour que l'assistant crée des sauvegardes et puisse y accéder. Pour le réplica principal, le compte utilisé pour démarrer le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] doit disposer d'autorisations de système de fichiers en lecture et en écriture sur un partage réseau. Pour les réplicas secondaires, le compte doit disposer d'une autorisation en lecture sur le partage réseau.  
  
    > [!IMPORTANT]  
    >  Les sauvegardes de journaux feront partie de votre chaîne de sauvegarde du journal. Stockez les fichiers de sauvegarde des journaux de manière appropriée.  
  
 **Si les conditions préalables requises ne sont pas satisfaites**  
  
 L'Assistant ne peut pas créer les bases de données secondaires pour ce groupe de disponibilité. Pour plus d'informations sur la façon de les préparer, consultez [Pour préparer manuellement une base de données secondaire](#PrepareSecondaryDbs), plus loin dans cette rubrique.  
  
 **Si les conditions préalables requises sont remplies**  
  
 Si toutes les conditions préalables requises sont remplies et si vous souhaitez que l'Assistant effectue la synchronisation de données initiale complète, sélectionnez l'option **Complet** et spécifiez un partage réseau. L'Assitant crée alors la base de données complète et les sauvegardes des fichiers journaux de chaque base de données sélectionnée et place ces sauvegardes sur le partage réseau que vous spécifiez. Ensuite, sur chaque instance de serveur qui héberge l'un des nouveaux réplicas secondaires, l'Assistant crée les bases de données secondaires en restaurant les sauvegardes à l'aide de RESTORE WITH NORECOVERY. Après la création de chacune des bases de données secondaires, l'Assistant joint la nouvelle base de données secondaire au groupe de disponibilité. Dès qu'une base de données secondaire est jointe, les synchronisations de données démarrent sur cette base de données.  
  
 **Spécifier un emplacement réseau partagé accessible par tous les réplicas**  
 Pour créer et restaurer des sauvegardes, l'assistant vous demande de spécifier un partage réseau. Le compte utilisé pour démarrer le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] sur chaque instance de serveur qui hébergera un réplica de disponibilité doit disposer d'autorisations de système de fichiers en lecture et en écriture sur le partage réseau.  
  
> [!IMPORTANT]  
>  Les sauvegardes de journaux feront partie de votre chaîne de sauvegarde du journal. Stockez les fichiers de sauvegarde de manière appropriée.  
  
##  <a name="Joinonly"></a> Joindre uniquement  
 Sélectionnez cette option uniquement s'il existe déjà des nouvelles bases de données secondaires sur chaque instance de serveur qui héberge un réplica secondaire pour le groupe de disponibilité. Pour plus d'informations sur la préparation des bases de données secondaires, consultez [Pour préparer manuellement une base de données secondaire](#PrepareSecondaryDbs), plus loin dans cette section.  
  
 Si vous sélectionnez **Joindre uniquement**, l'assistant essaie de joindre chaque base de données secondaire existante au groupe de disponibilité.  
  
## <a name="skip-initial-data-synchronization"></a>Ignorer la synchronisation de données initiale  
 Sélectionnez cette option si vous souhaitez effectuer vos propres sauvegardes de base de données et de journaux de chaque base de données primaire, puis les restaurer dans chaque instance de serveur qui héberge un réplica secondaire. Une fois que vous avez fermé l'assistant, vous devez ensuite joindre chaque base de données secondaire sur chaque réplica secondaire.  
  
> [!NOTE]  
>  Pour plus d’informations, consultez [Démarrer un mouvement de données sur une base de données secondaire AlwaysOn &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
##  <a name="PrepareSecondaryDbs"></a> Pour préparer manuellement une base de données secondaire  
 Pour préparer les bases de données secondaires indépendamment de l'Assistant [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] utilisé, vous pouvez opter pour l'une des méthodes suivantes :  
  
-   Restaurez manuellement une sauvegarde récente de la base de données primaire à l'aide de RESTORE WITH NORECOVERY, puis restaurez chaque sauvegarde de journal suivante à l'aide de RESTORE WITH NORECOVERY. Si les bases de données primaire et secondaire ont des chemins d'accès différents, vous devez utiliser l'option WITH MOVE. Effectuez cette séquence de restauration sur chaque instance de serveur qui héberge un réplica secondaire pour le groupe de disponibilité.  Vous pouvez utiliser [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou PowerShell pour exécuter ces opérations de sauvegarde et de restauration.  
  
     **Pour plus d'informations, consultez :**  
  
     [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   Si vous ajoutez une ou plusieurs bases de données primaires pour la copie des journaux de transaction à un groupe de disponibilité, vous pourrez peut-être effectuer une migration d'une ou de plusieurs bases de données secondaires correspondantes depuis la copie des journaux de transaction vers [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Pour plus d’informations, consultez [les conditions préalables pour la migration à partir de l’envoi de journaux pour les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md).  
  
    > [!NOTE]  
    >  Après avoir créé toutes les bases de données secondaires pour le groupe de disponibilité, si vous souhaitez effectuer des sauvegardes sur des réplicas secondaires, vous devez reconfigurer la préférence de sauvegarde automatisée du groupe de disponibilité.  
  
     **Pour plus d'informations, consultez :**  
  
     [Conditions préalables pour la migration à partir de journaux de transaction vers les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
     [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
 Après avoir créé une base de données secondaire, appliquez toutes les sauvegardes de journal en cours à la nouvelle base de données secondaire.  
  
 Éventuellement, vous pouvez préparer toutes les bases de données secondaires avant d'exécuter l'Assistant. Puis, dans la page **Sélectionner la synchronisation de données initiale** de l'Assistant, sélectionnez **Joindre uniquement** pour joindre automatiquement vos nouvelles bases de données secondaires au groupe de disponibilité.  
  
##  <a name="LaunchWiz"></a> Tâches associées  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter un réplica au groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Utiliser l’Assistant Ajouter une base de données au groupe de disponibilité &#40;SQL Server Management Studio&#41;](availability-group-add-database-to-group-wizard.md)  
  
-   [Utiliser l’Assistant Basculer le groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Démarrer un mouvement de données sur une base de données secondaire AlwaysOn &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  