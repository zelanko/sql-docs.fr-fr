---
title: "Rapports du serveur Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.SWB.SUMMARY.RENDER.CUSTOM.REPORT.F1"
ms.assetid: e976e7c0-a805-4370-bf73-356c8e3becfb
caps.latest.revision: 17
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 17
---
# Rapports du serveur Integration Services
  Dans la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], les rapports standard sont disponibles dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour vous aider à surveiller les projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] déployés sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Ces rapports vous aident à consulter l'état et l'historique du package et, si nécessaire, à identifier la cause des erreurs d'exécution du package.  
  
 En haut de chaque page de rapport, l'icône de retour permet de revenir à la page précédente, l'icône de rafraîchissement actualise les informations affichées dans la page et l'icône d'impression vous permet d'imprimer la page en cours.  
  
 Pour plus d’informations sur la manière de déployer des packages sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Déployer des projets sur le serveur Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md).  
  
## Tableau de bord Integration Services  
 Le rapport **Tableau de bord Integration Services** fournit une vue d’ensemble de toutes les exécutions de package sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour chaque package qui s'est exécuté sur le serveur, le tableau de bord vous permet de « zoomer » pour rechercher des détails spécifiques sur les erreurs d'exécution du package qui se sont produites.  
  
 Le rapport affiche les sections d'informations suivantes.  
  
|Section|Description|  
|-------------|-----------------|  
|**Informations sur l'exécution**|Affiche le nombre d'exécutions à différents états (échec, en cours d'exécution, réussi, autres) au cours des dernières 24 heures.|  
|**Informations sur le package**|Affiche le nombre total de packages exécutés au cours des dernières 24 heures.|  
|**Informations de connexion**|Affiche les connexions utilisées durant les exécutions qui se sont soldées par un échec au cours des dernières 24 heures.|  
|**Informations détaillées sur les packages**|Affiche les détails des exécutions terminées qui se sont produites au cours des dernières 24 heures. Par exemple, cette section présente le nombre d'exécutions qui se sont soldées par un échec par rapport au nombre total d'exécutions, à la durée des exécutions (en secondes) et à la durée moyenne des exécutions au cours des trois derniers mois.<br /><br /> Pour afficher des informations supplémentaires pour un package, cliquez sur **Vue d’ensemble**, **Tous les messages** et **Performances de l’exécution**.<br /><br /> Le rapport **Performances de l’exécution** indique la durée de la dernière instance d’exécution, ainsi que les heures de début et de fin et l’environnement qui a été appliqué.<br /><br /> Le graphique et la table associée inclus dans le rapport **Performances de l’exécution** indiquent la durée des 10 dernières exécutions réussies du package. Le tableau indique également la durée moyenne d'exécution sur une période de trois mois. Différents environnements et valeurs littérales ont pu être appliqués au moment de l'exécution de ces 10 exécutions réussies du package.<br /><br /> Enfin, le rapport **Performances de l’exécution** affiche le temps d’activité et le temps total écoulé des composants de flux de données du package. Le temps d'activité fait référence au temps total d'exécution d'un composant au cours de toutes les phases, et le temps total fait référence au temps total écoulé pour un composant. Le rapport affiche ces informations uniquement pour les composants de package lorsque le niveau de journalisation de la dernière exécution du package est défini sur Performances ou Commentaires.<br /><br /> Le rapport **Vue d’ensemble** indique l’état des tâches du package. Le rapport **Messages** indique les messages d’événements et les messages d’erreur du package et les tâches, par exemple les heures de début et de fin et le nombre de lignes écrites.<br /><br /> Vous pouvez également cliquer sur **Afficher les messages** dans le rapport **Vue d’ensemble** pour accéder au rapport **Messages**. Vous pouvez également cliquer sur **Afficher la vue d’ensemble** dans le rapport **Messages** pour accéder au rapport **Vue d’ensemble**.|  
  
 Vous pouvez filtrer la table affichée dans une page en cliquant sur **Filtrer** et en sélectionnant des critères dans la boîte de dialogue **Paramètres du filtre**. Les critères de filtre disponibles dépendent des données qui sont affichées. Vous pouvez modifier l’ordre de tri du rapport en cliquant sur l’icône de tri dans la boîte de dialogue **Paramètres du filtre**.  
  
## Rapport Toutes les exécutions  
 Le rapport **Toutes les exécutions** affiche un résumé de toutes les exécutions d’[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] effectuées sur le serveur. Il peut y avoir plusieurs exécutions de l'exemple de package. Contrairement au rapport **Tableau de bord Integration Services**, vous pouvez configurer le rapport **Toutes les exécutions** pour afficher les exécutions qui ont démarré au cours d’une plage de dates. Les dates peuvent couvrir plusieurs jours, mois ou années.  
  
 Le rapport affiche les sections d'informations suivantes.  
  
|Section|Description|  
|-------------|-----------------|  
|Filtre|Indique le filtre actif appliqué au rapport, tel que la plage d'heures de début.|  
|Informations sur l'exécution|Indique l'heure de début, l'heure de fin, la durée d'exécution de chaque package. Vous pouvez afficher la liste des valeurs de paramètre utilisées avec une exécution de package, telles que les valeurs qui ont été passées à un package enfant à l'aide de la tâche d'exécution de package. Pour afficher la liste des paramètres, cliquez sur Vue d'ensemble.|  
  
 Pour plus d’informations sur l’utilisation de la tâche d’exécution de package afin de rendre des valeurs disponibles dans un package enfant, consultez [Tâche d’exécution de package](../../integration-services/control-flow/execute-package-task.md).  
  
 Pour plus d’informations sur les paramètres, consultez [Paramètres des projets et des packages Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-package-and-project-parameters.md).  
  
## Toutes les connexions  
 Le rapport **Toutes les connexions** fournit les informations suivantes pour les connexions qui ont échoué, pour les exécutions qui se sont produites sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le rapport affiche les sections d'informations suivantes.  
  
|Section|Description|  
|-------------|-----------------|  
|Filtre|Indique le filtre actif appliqué au rapport, tel que les connexions avec une chaîne spécifiée et la plage **Heure du dernier échec**.<br /><br /> Vous définissez la plage **Heure du dernier échec** pour afficher uniquement les échecs de connexion qui se sont produits pendant une plage de dates. La plage peut couvrir plusieurs jours, mois ou années.|  
|Détails|Affiche la chaîne de connexion, le nombre d'exécutions pendant lesquelles une connexion a échoué et la date du dernier échec de connexion.|  
  
## Rapport Toutes les opérations  
 Le rapport **Toutes les opérations** affiche un résumé de toutes les opérations [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] effectuées sur le serveur, notamment les déploiements, validations et exécutions de package, ainsi que d’autres opérations d’administration. Comme avec le Tableau de bord Integration Services, vous pouvez appliquer un filtre à la table afin de réduire les informations affichées.  
  
## Rapport Toutes les validations  
 Le rapport **Toutes les validations** affiche un résumé de toutes les validations d’[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] effectuées sur le serveur. Le résumé affiche les informations relatives à chaque validation telles que l'état, l'heure de début et l'heure de fin. Chaque entrée du résumé inclut un lien vers les messages générés pendant la validation. Comme avec le Tableau de bord Integration Services, vous pouvez appliquer un filtre à la table afin de réduire les informations affichées.  
  
## Rapports personnalisés  
 Vous pouvez ajouter un rapport personnalisé (fichier .rdl) au nœud de catalogue **SSISDB** sous le nœud **Catalogues Integration Services** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Avant d'ajouter le rapport, vérifiez que vous utilisez une convention d'affectation des noms en trois parties pour qualifier le projet référencé comme table source. Dans le cas contraire, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] affiche une erreur. La convention d’affectation des noms est \<base de données>.\<propriétaire>.\<objet>. Par exemple, le nom « SSISDB.interne.exécutions ».  
  
> [!NOTE]  
>  Quand vous ajoutez des rapports personnalisés au nœud **SSISDB** sous le nœud **Bases de données**, le préfixe SSISDB n’est pas nécessaire.  
  
 Pour obtenir des instructions sur la manière de créer et d’ajouter un rapport personnalisé, consultez [Ajouter un rapport personnalisé à Management Studio](../../ssms/object/add-a-custom-report-to-management-studio.md).  
  
## Tâches associées  
 [Afficher les rapports du serveur Integration Services](../../integration-services/performance/view-reports-for-the-integration-services-server.md)  
  
## Contenu connexe  
[Surveiller les packages en cours d’exécution et autres opérations](../../integration-services/performance/monitor-running-packages-and-other-operations.md)
  
  