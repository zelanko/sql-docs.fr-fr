---
title: "Affichage et arr&#234;t des packages ex&#233;cut&#233;s sur le serveur Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "08/26/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "packages [Integration Services], gestion"
  - "gestion des packages en cours d'exécution [Integration Services]"
  - "packages [Integration Services], exécution"
  - "exécution de package [Integration Services], gestion"
ms.assetid: 11bf44e6-f6b0-475f-b816-40e914dbac80
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# Affichage et arr&#234;t des packages ex&#233;cut&#233;s sur le serveur Integration Services
  La base de données **SSISDB** stocke l'historique de l'exécution dans des tables internes qui ne sont pas visibles par les utilisateurs. Cependant, elle expose les informations dont vous avez besoin via des vues publiques que vous pouvez interroger. Elle fournit également des procédures stockées que vous pouvez appeler pour effectuer des tâches courantes liées aux packages.  
  
 En général, vous gérez des objets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur le serveur dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Cependant, vous pouvez également interroger les vues de base de données et appeler les procédures stockées directement, ou écrire du code personnalisé qui appelle l'API managé. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et l'API managé interrogent les vues et appellent les procédures stockées pour effectuer de nombreuses tâches. Par exemple, vous pouvez afficher la liste des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui sont en cours d'exécution sur le serveur, et demander l'arrêt de packages si nécessaire.  
  
## Affichage de la liste de packages en cours d'exécution  
 Vous pouvez afficher la liste des packages en cours d'exécution sur le serveur dans la boîte de dialogue **Opérations actives** . Pour plus d'informations, consultez [Active Operations Dialog Box](../../integration-services/performance/active-operations-dialog-box.md).  
  
 Pour plus d'informations sur les autres méthodes que vous pouvez utiliser pour afficher la liste de packages en cours d'exécution, consultez les rubriques suivantes.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]  - Accès  
 Pour afficher la liste des packages qui s’exécutent sur le serveur, interrogez la vue, [catalog.executions &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md) pour les packages qui ont l’état 2.  
  
 Accès par programmation via l'API managé  
 Consultez l’espace de noms <xref:Microsoft.SqlServer.Management.IntegrationServices> et de ses classes.  
  
## Arrêt d'un package en cours d'exécution  
 Vous pouvez demander l'arrêt d'un package en cours d’exécution dans la boîte de dialogue **Opérations actives**. Pour plus d'informations, consultez [Active Operations Dialog Box](../../integration-services/performance/active-operations-dialog-box.md).  
  
 Pour plus d'informations sur les autres méthodes que vous pouvez utiliser pour arrêter l'exécution d'un package, consultez les rubriques suivantes.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]  - Accès  
 Pour arrêter un package en cours d’exécution sur le serveur, appelez la procédure stockée, [catalog.stop_operation &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database.md).  
  
 Accès par programmation via l'API managé  
 Consultez l’espace de noms <xref:Microsoft.SqlServer.Management.IntegrationServices> et de ses classes.  
  
## Affichage de l'historique des packages qui ont été exécutés  
 Pour afficher l’historique des packages exécutés dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], utilisez le rapport **Toutes les exécutions**. Pour plus d’informations sur le rapport **Toutes les exécutions** et d’autres rapports standard, consultez [Rapports du serveur Integration Services](../../integration-services/performance/reports-for-the-integration-services-server.md).  
  
 Pour plus d'informations sur les autres méthodes que vous pouvez utiliser pour afficher l'historique des packages en cours d'exécution, consultez les rubriques suivantes.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]  - Accès  
 Pour afficher des informations relatives aux packages qui ont été exécutés, interrogez la vue, [catalog.executions &#40;SSISDB Database&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md).  
  
 Accès par programmation via l'API managé  
 Consultez l’espace de noms <xref:Microsoft.SqlServer.Management.IntegrationServices> et de ses classes.  
  
## Voir aussi  
 [Exécution de projets et de packages](https://msdn.microsoft.com/library/hh213290.aspx)   
 [Dépannage des rapports pour l'exécution des packages](https://msdn.microsoft.com/library/gg471512.aspx)  
  
  