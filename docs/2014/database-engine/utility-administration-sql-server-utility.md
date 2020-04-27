---
title: Administration de l’utilitaire (Utilitaire SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 3e5a00c3-8905-40f0-9ddc-d924df9c2f0d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6da38b25ca23302c8b683a5c9b54ed2b6f88f6b2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62773751"
---
# <a name="utility-administration-sql-server-utility"></a>Administration de l'utilitaire (utilitaire SQL Server)
  Utilisez les onglets Administration de l'utilitaire pour gérer les paramètres de stratégie, de sécurité et d'entrepôt de données pour un utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Pour plus d’informations sur les concepts de l’utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , consultez [Fonctionnalités et tâches de l’utilitaire SQL Server](../relational-databases/manage/sql-server-utility-features-and-tasks.md).  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 Onglet Stratégie : utilisez l'onglet de stratégie pour afficher ou spécifier des stratégies d'analyse globales.  
  
 Définissez des stratégies globales de surveillance des applications de couche Données. Pour développer la liste des valeurs de cette option, cliquez sur la flèche en regard du nom de la stratégie ou cliquez sur le titre de la stratégie.  
 Quand une application se trouve-t-elle à court de capacité de processeur ? Pour modifier cette stratégie, utilisez le contrôle situé à droite de la description de la stratégie, puis cliquez sur **Appliquer**. Vous pouvez également restaurer les valeurs par défaut ou ignorer les modifications à l'aide des boutons situés en bas de l'affichage.  
  
-   La valeur maximale par défaut pour l'utilisation du processeur est de 70 %.  
  
-   La valeur minimale par défaut pour l'utilisation du processeur est de 0 %.  
  
 Quand une application se trouve-t-elle à court d'espace de fichier ? Pour modifier la stratégie d’utilisation de l’espace du fichier de données ou du fichier journal, utilisez le contrôle situé à droite de la description de la stratégie, puis cliquez sur **Appliquer**. Vous pouvez également restaurer les valeurs par défaut ou ignorer les modifications à l'aide des boutons situés en bas de l'affichage.  
  
-   La valeur maximale par défaut pour l'utilisation de l'espace du fichier est de 70 %.  
  
-   La valeur minimale par défaut pour l'utilisation de l'espace du fichier est de 0 %.  
  
 Définissez des stratégies globales de surveillance des applications d'instance gérée de SQL Server. Pour développer la liste des valeurs de cette option, cliquez sur la flèche en regard du nom de la stratégie ou cliquez sur le titre de la stratégie.  
 Quand une instance gérée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] se trouve-t-elle à court de capacité de processeur ? Pour modifier cette stratégie, utilisez le contrôle situé à droite de la description de la stratégie, puis cliquez sur **Appliquer**. Vous pouvez également restaurer les valeurs par défaut ou ignorer les modifications à l'aide des boutons situés en bas de l'affichage.  
  
-   La valeur maximale par défaut pour l'utilisation d'une instance du processeur est de 70 %.  
  
-   La valeur minimale par défaut pour l'utilisation d'une instance du processeur est de 0 %.  
  
 Quand une instance gérée d'un ordinateur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] se trouve-t-elle à court de capacité de processeur ? Pour modifier cette stratégie, utilisez le contrôle situé à droite de la description de la stratégie, puis cliquez sur **Appliquer**. Vous pouvez également restaurer les valeurs par défaut ou ignorer les modifications à l'aide des boutons situés en bas de l'affichage.  
  
-   La valeur maximale par défaut pour l'utilisation du processeur de l'ordinateur est de 70 %.  
  
-   La valeur minimale par défaut pour l'utilisation du processeur de l'ordinateur est de 0 %.  
  
 Quand une instance gérée de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est-elle à court d'espace de fichier ? Pour modifier la stratégie d’utilisation de l’espace du fichier de données ou du fichier journal, utilisez le contrôle situé à droite de la description de la stratégie, puis cliquez sur **Appliquer**. Vous pouvez également restaurer les valeurs par défaut ou ignorer les modifications à l'aide des boutons situés en bas de l'affichage.  
  
-   La valeur maximale par défaut pour l'utilisation de l'espace du fichier est de 70 %.  
  
-   La valeur minimale par défaut pour l'utilisation de l'espace du fichier est de 0 %.  
  
 Quand une instance gérée d'un ordinateur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] se trouve-t-elle à court d'espace de volume de stockage ? Pour modifier cette stratégie, utilisez le contrôle situé à droite de la description de la stratégie, puis cliquez sur **Appliquer**. Vous pouvez également restaurer les valeurs par défaut ou ignorer les modifications à l'aide des boutons situés en bas de l'affichage.  
  
-   La valeur maximale par défaut pour l'utilisation de l'espace du volume de l'ordinateur est de 70 %.  
  
-   La valeur minimale par défaut pour l'utilisation de l'espace du volume de l'ordinateur est de 0 %.  
  
 Réduction du bruit des violations de la stratégie par des ressources très volatiles. Pour développer les contrôles de cette fonctionnalité, cliquez sur la flèche basse située sur le côté droit de l'écran.  
 Pour plus d’informations, consultez [réduire le bruit dans les stratégies d’utilisation du processeur &#40;Utilitaire SQL Server&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 Onglet de sécurité : affiche les noms de connexion disposant d'autorisations pour administrer ou lire l'UCP.  
  
 Sélectionnez les connexions de l'UCP qui seront ajoutées au rôle de lecteur d'utilitaire.  
 Le privilège de lecteur d'utilitaire permet au compte d'utilisateur de :  
  
-   Connectez-vous à l'utilitaire [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   Affichez tous les points d'observation dans l'Explorateur de l'utilitaire dans SSMS.  
  
-   Affichez les paramètres sur le nœud Administration de l'utilitaire dans l'Explorateur de l'utilitaire dans SSMS.  
  
 Les administrateurs de l'utilitaire peuvent inscrire et supprimer des instances de SQL Server dans un utilitaire SQL Server. Ils peuvent aussi modifier des stratégies sur les instances gérées et modifier des paramètres d'administration sur l'UCP.  
  
 Pour être administrateur de l'utilitaire, vous devez avoir des privilèges de sysadmin sur l'instance de SQL Server. Pour ajouter ou modifier des comptes d'utilisateurs pour l'UCP de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], utilisez l'Explorateur d'objets dans SSMS pour ajouter l'utilisateur aux connexions serveur de l'instance de l'UCP de SQL Server. Pour plus d’informations, consultez [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql).  
  
## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur  
 Onglet Entrepôt de données : affiche les détails de configuration de l'entrepôt de données de gestion de l'utilitaire.  
  
 Conservation des données  
 Spécifiez la période de rétention des données pour les informations d'utilisation recueillies pour les instances managées de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. La période par défaut est d'un an. La valeur minimale est d'un mois. La plus longue valeur prise en charge est de 2 ans.  
  
 Informations de configuration de l'entrepôt de données de l'utilitaire  
 Les paramètres de configuration suivants ne sont pas configurables dans cette version de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
-   Nom de l’UMDW : Sysutility_mdw_\<GUID>_DATA.  
  
-   fréquence de téléchargement du jeu d'éléments de collecte : toutes les 15 minutes.  
  
 Le répertoire UMDW est configurable : \<Lecteur_système:\Program Files\Microsoft SQL Server\MSSQL10_50.<Nom_UCP>\MSSQL\Data\\, où \<Lecteur_système est normalement le lecteur C:\. Le fichier journal, UMDW_\<GUID>_LOG, se trouve dans le même répertoire.  
  
> [!NOTE]  
>  L'emplacement du fichier UMDW (sysutility_mdw) peut être modifié à l'aide des opérations de détachement et d'attachement ou d'ALTER DATABASE. Nous recommandons l'utilisation d'ALTER DATABASE. Pour plus d’informations, consultez [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
 Revenir aux valeurs par défaut prédéfinies  
 Pour rétablir les valeurs par défaut des paramètres de cet onglet, cliquez sur le bouton **Paramètres par défaut** , puis sur **Appliquer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Tableau de bord de l’utilitaire &#40;Utilitaire SQL Server&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md)   
 [Détails de l’application de la couche données déployée &#40;Utilitaire SQL Server&#41;](../../2014/database-engine/deployed-data-tier-application-details-sql-server-utility.md)   
 [Détails Managed Instance &#40;Utilitaire SQL Server&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md)   
 [Surveiller des instances de SQL Server dans l'utilitaire SQL Server](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md)  
  
  
