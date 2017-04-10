---
title: "Administration de DQS | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "administration de dqs"
  - "administration"
  - "DQS, administration"
ms.assetid: 9940ef5d-f6f6-4dec-9414-1077a4d7f12b
caps.latest.revision: 21
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 21
---
# Administration de DQS
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) vous permet d’administrer et de gérer les différentes activités DQS effectuées sur [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], configurer les propriétés de niveau serveur liées à des activités DQS, configurez les paramètres de Service de données de référence et configurer les paramètres de journal DQS. Ces opérations sont effectuées via le **Administration** fonctionnalité dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Selon votre accès de sécurité (rôle) dans DQS, vous êtes autorisé ou non à accéder à certaines fonctionnalités de cette zone.  
  
 Outre ces activités d'administration, cette rubrique offre également des informations sur la sauvegarde et la restauration des bases de données DQS, une activité d'administration qui n'est pas effectuée à l'aide de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
 La fonctionnalité d'administration de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] présente les avantages suivants :  
  
-   Permet aux gestionnaires de données d'analyser les différentes activités de DQS sur un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] à partir de [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
-   Permet aux administrateurs de DQS surveiller les activités DQS sur un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] d’un [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], et *arrêter* une activité en cours d’exécution ou *arrêter* un processus en cours d’exécution dans une activité, si nécessaire.  
  
-   Configurer les paramètres du service de données de référence tels que la configuration de la connectivité à Windows Azure Marketplace et la gestion des fournisseurs de services de données de référence tiers.  
  
-   Configurer les valeurs de seuil pour les activités de nettoyage et de mise en correspondance.  
  
-   Activer/désactiver les notifications dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
-   Configurer la journalisation en fonction du niveau de gravité des événements.  
  
##  <a name="AdminUsingClent"></a> Activités administratives effectuées à l'aide de Data Quality Client  
 Ces activités sont effectuées en utilisant la **Administration** fonctionnalité dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
### Analyse des activités  
 Le **analyse de l’activité** écran [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] affiche des informations détaillées sur chaque activité effectuée sur un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]. Cet écran est utilisé principalement par le gestionnaire de données pour procéder à une analyse approfondie de toutes les activités effectuées sur le [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] auquel l'application [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] est connectée. Cet écran ne fournit pas de surveillance au niveau du système. En outre, cet écran permet aux administrateurs de DQS de contrôler une activité ou un processus d'une activité en terminant une activité en cours d'exécution ou en arrêtant un processus en cours d'exécution dans une activité, si nécessaire. Les données sont affichées pour la découverte des connaissances, la gestion des domaines, la stratégie de correspondance, le nettoyage, la mise en correspondance et le nettoyage basé sur SQL Server Integration Services (SSIS).  
  
### Configuration  
 Le **Configuration** écran [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] permet à l’administrateur DQS effectuer les opérations suivantes :  
  
-   **Données de référence**: configurer les fournisseurs de services de données de référence : fournisseurs de services de données de référence directe ou de Windows Azure Marketplace. Après avoir installé les fournisseurs de services de données de référence, vous pouvez mapper un domaine/domaine composite aux données de référence pendant l'activité de gestion des domaines d'une base de connaissances, puis utiliser cette base de connaissances pour l'activité de nettoyage dans un projet de qualité des données. Elle vous permet également de spécifier les paramètres proxy de connexion à Internet pour l'utilisation de Windows Azure Marketplace.  
  
-   **Paramètres généraux**: spécifiez les valeurs de seuil pour le nettoyage de données et mise en correspondance et s’il faut activer les notifications de profilage dans [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. Ces valeurs de seuil sont utilisées par DQS pendant les opérations de nettoyage et de mise en correspondance assistées par ordinateur dans un projet de qualité des données.  
  
-   **Paramètres du journal**: les fichiers journaux dans DQS enregistrent les activités effectuées dans DQS et sont utiles pour le suivi des problèmes opérationnels lors de la maintenance et le dépannage. Vous pouvez filtrer les messages que vous souhaitez consigner dans le journal pour les différentes fonctionnalités de DQS (gestion de domaines, découverte des connaissances, nettoyage, mise en correspondance et services de données de référence) et les différents modules de DQS selon le niveau de gravité des événements.  
  
> [!NOTE]  
>  Le **Configuration** écran est disponible uniquement pour les utilisateurs qui disposent du rôle dqs_administrator sur la base de données DQS_MAIN.  
  
##  <a name="AdminOutsideClient"></a> Activités administratives effectuées en dehors de Data Quality Client  
 Ces opérations sont effectuées en dehors de Data Quality Client :  
  
-   **Sauvegarde et restauration des bases de données DQS**: la sauvegarde et la restauration de bases de données DQS est identique à celui de sauvegarde et restauration d’une base de données SQL Server avec des considérations spécifiques à DQS.  
  
-   **Détacher et attacher les bases de DQS**: les étapes pour détacher et attacher les bases de données DQS est identique à celui de détachement et l’attachement d’une base de données SQL Server avec des considérations spécifiques à DQS.  
  
 Pour plus d’informations, consultez [Gérer les bases de données DQS](../data-quality-services/manage-dqs-databases.md).  
  
## Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Explique comment analyser les activités de DQS.|[Surveiller les activités DQS](../data-quality-services/monitor-dqs-activities.md)|  
|Explique comment configurer les paramètres des données de référence dans DQS.|[Configure DQS to Use Reference Data](../data-quality-services/configure-dqs-to-use-reference-data.md)|  
|Explique comment configurer les valeurs de seuil pour les opérations de nettoyage et de mise en correspondance.|[Configure Threshold Values for Cleansing and Matching](../data-quality-services/configure-threshold-values-for-cleansing-and-matching.md)|  
|Explique comment activer ou désactiver les notifications dans DQS.|[Enable or Disable Profiling Notifications in DQS](../data-quality-services/enable-or-disable-profiling-notifications-in-dqs.md)|  
|Explique comment configurer la journalisation dans DQS selon le niveau de gravité des événements.|[Configure Severity Levels for DQS Log Files](../data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|Explique comment configurer les paramètres de journalisation avancés dans DQS.|[Configurer les paramètres avancés pour les fichiers journaux DQS](../data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
|Explique comment sauvegarder et restaurer les bases de données DQS.|[Sauvegarde et restauration de bases de données DQS](../data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|Décrit comment détacher et attacher des bases de données DQS.|[Detaching and Attaching DQS Databases](../data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## Voir aussi  
 [Services de données de référence dans DQS](../data-quality-services/reference-data-services-in-dqs.md)   
 [Gérer les fichiers journaux DQS](../data-quality-services/manage-dqs-log-files.md)   
 [Gérer des bases de données DQS](../data-quality-services/manage-dqs-databases.md)  
  
  