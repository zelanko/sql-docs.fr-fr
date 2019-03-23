---
title: Activer la journalisation pour l’exécution du Package sur le serveur SSIS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 8930c63c-bc6f-46c2-b428-b3c29ee89a7d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 99321c27fa28d16260ee3b27972d83a8b61cae59
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58393257"
---
# <a name="enable-logging-for-package-execution-on-the-ssis-server"></a>Activer la journalisation des exécutions de package sur le serveur SSIS
  Cette procédure explique comment définir ou modifier le niveau de journalisation d'un package lorsque vous exécutez un package déployé sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Le niveau de journalisation que vous définissez lorsque vous exécutez le package remplace la journalisation du package configurée à l'aide de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations, consultez [Activer la journalisation des packages dans les outils de données SQL Server](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md) .  
  
 Pour spécifier le niveau de journalisation, procédez selon l'une des méthodes suivantes. Cette rubrique présente la première méthode.  
  
-   Configuration d'une instance d'un package d'exécution à l'aide de la boîte de dialogue Exécuter le package  
  
-   Définition des paramètres pour une instance d’exécution à l’aide de [catalog.set_execution_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)  
  
-   Configuration d'un travail de l'Agent SQL Server pour une exécution de package à l'aide de la boîte de dialogue Nouvelle étape de travail.  
  
### <a name="to-set-the-logging-level-for-a-package-by-using-the-execute-package-dialog-box"></a>Pour définir le niveau de journalisation d'un package à l'aide de la boîte de dialogue Exécuter le package  
  
1.  Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], naviguez jusqu'au package dans l'Explorateur d'objets.  
  
2.  Cliquez avec le bouton droit sur le package, puis sélectionnez **Exécuter**.  
  
3.  Dans la boîte de dialogue **Exécuter le package** , sélectionnez l'onglet **Avancé** .  
  
4.  Sous **Niveau de journalisation**, sélectionnez le niveau de journalisation. Consultez la table ci-dessous pour une description des valeurs disponibles.  
  
5.  Terminez toutes les autres configurations du package, puis cliquez sur **OK** pour l'exécuter.  
  
 Les niveaux de journalisation suivants sont disponibles.  
  
|Niveau de journalisation|Description|  
|-------------------|-----------------|  
|None|La journalisation est désactivée. Seul l'état d'exécution du package est enregistré.|  
|Simple|Tous les événements sont enregistrés, sauf les événements personnalisés et de diagnostic. Valeur par défaut.|  
|Performances|Seules les statistiques de performances, et les événements OnError et OnWarning, sont enregistrés.<br /><br /> Le rapport **Performances de l'exécution** affiche le temps d'activité et le temps total écoulé des composants de flux de données du package. Ces informations sont disponibles si le niveau de journalisation de la dernière exécution du package a été défini sur **Performances** ou **Commentaires**. Pour plus d'informations, consultez [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).<br /><br /> La vue [catalog.execution_component_phases](/sql/integration-services/system-views/catalog-execution-component-phases) affiche les heures de début et de fin des composants de flux de données, pour chaque phase d’exécution. Cette vue affiche ces informations pour ces composants uniquement lorsque le niveau de journalisation de l'exécution du package est défini sur **Performances** ou **Commentaires**.|  
|Commentaires|Tous les événements sont enregistrés, y compris les événements personnalisés et de diagnostic.<br /><br /> L'événement DiagnosticEx est un exemple d'événement de diagnostic. Chaque fois qu'une tâche d'exécution de package exécute un package enfant, enregistre cet événement. Le message d’événement qui se compose des valeurs de paramètre passées aux packages enfants<br /><br /> La valeur de la colonne de message pour DiagnosticEx est du texte XML. . Pour afficher le texte du message pour une exécution de package, interrogez la vue [catalog.operation_messages &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database).<br /><br /> Remarque : Les événements personnalisés sont notamment les événements consignés par les tâches [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Pour plus d’informations, consultez [Custom Messages for Logging](../../2014/integration-services/custom-messages-for-logging.md).<br /><br /> La vue [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) affiche une ligne chaque fois qu’un composant de flux de données envoie des données à un composant en aval, pour une exécution de package. Le niveau de journalisation doit avoir la valeur **Commentaires** pour capturer ces informations dans la vue.|  
  
## <a name="see-also"></a>Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)   
 [Activer la journalisation des packages dans les outils de données SQL Server](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md)  
  
  
