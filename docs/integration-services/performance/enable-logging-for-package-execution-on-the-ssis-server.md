---
title: "Activer la journalisation des ex&#233;cutions de package sur le serveur SSIS | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQL13.SSIS.SSMS.ISMANAGECUSTOMIZEDLOGGINGLEVEL.F1"
ms.assetid: 8930c63c-bc6f-46c2-b428-b3c29ee89a7d
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# Activer la journalisation des ex&#233;cutions de package sur le serveur SSIS
  Cette rubrique explique comment définir ou modifier le niveau de journalisation d'un package lorsque vous exécutez un package déployé sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Le niveau de journalisation que vous définissez lorsque vous exécutez le package remplace la journalisation du package configurée lors de la création dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations, consultez [Activer la journalisation des packages dans les outils de données SQL Server](../../integration-services/performance/enable-package-logging-in-sql-server-data-tools.md).  
  
 Dans **Propriétés du serveur** de SQL Server, sous la propriété **Niveau de journalisation du serveur**, vous pouvez sélectionner un niveau de journalisation par défaut au niveau du serveur. Vous pouvez choisir parmi les niveaux de journalisation intégrés décrits dans cette rubrique, ou choisir un niveau de journalisation personnalisé existant. Le niveau de journalisation sélectionné s'applique par défaut à tous les packages déployés sur le catalogue SSIS. Il s'applique également par défaut à une étape de travail de l'Agent SQL qui exécute un package SSIS.  
  
 Vous pouvez également spécifier le niveau de journalisation d’un package individuel en procédant selon l'une des méthodes suivantes. Cette rubrique présente la première méthode.  
  
-   Configuration d'une instance d'un package d'exécution à l'aide de la boîte de dialogue Exécuter le package  
  
-   Définition des paramètres pour une instance d’exécution à l’aide de [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
  
-   Configuration d'un travail de l'Agent SQL Server pour une exécution de package à l'aide de la boîte de dialogue Nouvelle étape de travail.  
  
## Définir le niveau de journalisation d'un package à l'aide de la boîte de dialogue Exécuter le package  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], naviguez jusqu'au package dans l'Explorateur d'objets.  
  
2.  Cliquez avec le bouton droit sur le package, puis sélectionnez **Exécuter**.  
  
3.  Dans la boîte de dialogue **Exécuter le package** , sélectionnez l'onglet **Avancé** .  
  
4.  Sous **Niveau de journalisation**, sélectionnez le niveau de journalisation. Cette rubrique contient une description des valeurs disponibles.  
  
5.  Terminez toutes les autres configurations du package, puis cliquez sur **OK** pour l'exécuter.  
  
## Sélectionner un niveau de journalisation  
 Les niveaux de journalisation intégrés suivants sont disponibles. Vous pouvez également sélectionner un niveau de journalisation personnalisé existant. Cette rubrique contient une description des niveaux de journalisation personnalisés.  
  
|Niveau de journalisation|Description|  
|-------------------|-----------------|  
|Aucun|La journalisation est désactivée. Seul l'état d'exécution du package est enregistré.|  
|Basic|Tous les événements sont enregistrés, sauf les événements personnalisés et de diagnostic. Ceci est la valeur par défaut.|  
|RuntimeLineage|Collecte les données nécessaires au suivi des informations de lignage dans le flux de données. Vous pouvez analyser ces informations de lignage afin de mapper la relation de lignage entre différentes tâches. Les éditeurs de logiciels indépendants et les développeurs peuvent créer des outils de mappage de lignage personnalisés à l’aide de ces informations.|  
|Performance|Seules les statistiques de performances, et les événements OnError et OnWarning, sont enregistrés.<br /><br /> Le rapport **Performances de l'exécution** affiche le temps d'activité et le temps total écoulé des composants de flux de données du package. Ces informations sont disponibles si le niveau de journalisation de la dernière exécution du package a été défini sur **Performances** ou **Commentaires**. Pour plus d'informations, consultez [Reports for the Integration Services Server](../../integration-services/performance/reports-for-the-integration-services-server.md).<br /><br /> La vue [catalog.execution_component_phases](../../integration-services/system-views/catalog-execution-component-phases.md) affiche les heures de début et de fin des composants de flux de données, pour chaque phase d’exécution. Cette vue affiche ces informations pour ces composants uniquement lorsque le niveau de journalisation de l'exécution du package est défini sur **Performances** ou **Commentaires**.|  
|Commentaires|Tous les événements sont enregistrés, y compris les événements personnalisés et de diagnostic.<br /><br /> Les événements personnalisés sont notamment les événements consignés par les tâches [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Pour plus d'informations sur les événements personnalisés, consultez [Custom Messages for Logging](../../integration-services/performance/custom-messages-for-logging.md).<br /><br /> L'événement **DiagnosticEx** est un exemple d'événement de diagnostic. Chaque fois qu'une tâche d'exécution de package exécute un package enfant, cet événement capture les valeurs de paramètres passées aux packages enfants.<br /><br /> L’événement **DiagnosticEx** vous permet également d’obtenir les noms des colonnes dans lesquelles des erreurs se produisent au niveau des lignes. Cet événement consigne un mappage de lignage de flux de données dans le journal. Vous pouvez alors rechercher le nom de colonne dans ce mappage de lignage à l’aide de l’identificateur de colonne capturé par une sortie d’erreur.  Pour plus d’informations, consultez [Error Handling in Data](../../integration-services/data-flow/error-handling-in-data.md).<br /><br /> La valeur de la colonne de message pour **DiagnosticEx** est du texte XML. Pour afficher le texte du message pour une exécution de package, interrogez la vue [catalog.operation_messages &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md). Notez que l’événement **DiagnosticEx** ne conserve pas l’espace blanc dans sa sortie XML afin réduire la taille du journal. Pour améliorer la lisibilité, copiez le journal dans un éditeur XML (dans Visual Studio, par exemple) prenant en charge la mise en forme XML et la mise en surbrillance de la syntaxe.<br /><br /> La vue [catalog.execution_data_statistics](../../integration-services/system-views/catalog-execution-data-statistics.md) affiche une ligne chaque fois qu’un composant de flux de données envoie des données à un composant en aval, pour une exécution de package. Le niveau de journalisation doit avoir la valeur **Commentaires** pour capturer ces informations dans la vue.|  
  
## Créer et gérer des niveaux de journalisation personnalisés à l'aide de la boîte de dialogue de gestion des niveaux de journalisation personnalisés  
 Vous pouvez créer des niveaux de journalisation personnalisés qui collectent uniquement les statistiques et les événements que vous souhaitez. Vous pouvez également capturer le contexte des événements, notamment les valeurs de variables, les chaînes de connexion et les propriétés de composants. Lorsque vous exécutez un package, vous pouvez sélectionner un niveau de journalisation personnalisé partout où vous pouvez sélectionner un niveau de journalisation intégré.  
  
> [!TIP]  
>  Pour capturer les valeurs des variables d’un package, la propriété **IncludeInDebugDump** des variables doit être définie sur **True**.  
  
1.  Pour créer et gérer des niveaux de journalisation personnalisés, dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], cliquez avec le bouton droit sur la base de données SSISDB, sélectionnez **Niveau de journalisation personnalisé** pour ouvrir la boîte de dialogue **Gestion du niveau de journalisation personnalisée**. La liste **Niveaux de journalisation personnalisés** contient tous les niveaux de journalisation personnalisés existants.  
  
2.  Pour **créer** un niveau de journalisation personnalisé, cliquez sur **Créer**, puis indiquez un nom et une description. Dans les onglets **Statistiques** et **Événements** , sélectionnez les statistiques et les événements que vous souhaitez collecter. Dans l’onglet **Événements** , vous pouvez également sélectionner l’option **Inclure le contexte** pour des événements individuels. Ensuite, cliquez sur **Enregistrer**.  
  
3.  Pour **mettre à jour** un niveau de journalisation personnalisé existant, sélectionnez-le dans la liste, reconfigurez-le, puis cliquez sur **Enregistrer**.  
  
4.  Pour **supprimer** un niveau de journalisation personnalisé existant, sélectionnez-le dans la liste, puis cliquez sur **Supprimer**.  
  
 **Autorisations des niveaux de journalisation personnalisés.**  
  
-   Tous les utilisateurs de la base de données SSISDB peuvent voir les niveaux de journalisation personnalisés et sélectionner un niveau de journalisation personnalisé lorsqu'ils exécutent des packages.  
  
-   Seuls les utilisateurs avec un rôle ssis_admin ou sysadmin peuvent créer, mettre à jour ou supprimer des niveaux de journalisation personnalisés.  
  
## Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md)   
 [Activer la journalisation des packages dans les outils de données SQL Server](../../integration-services/performance/enable-package-logging-in-sql-server-data-tools.md)  
  
  