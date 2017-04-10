---
title: "Surveiller les packages en cours d’ex&#233;cution et autres op&#233;rations | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 14
---
# Surveiller les packages en cours d’ex&#233;cution et autres op&#233;rations
  Vous pouvez surveiller les exécutions des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], les validations de projet et d’autres opérations en utilisant un ou plusieurs des outils suivants. Certains outils tels que les drainages de données ne sont disponibles que pour les projets déployés sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   Journaux  
  
     Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../../integration-services/performance/integration-services-ssis-logging.md).  
  
-   Rapports  
  
     Pour plus d'informations, consultez [Reports for the Integration Services Server](../../integration-services/performance/reports-for-the-integration-services-server.md).  
  
-   Vues  
  
     Pour plus d’informations, consultez [Vues &#40;Catalogue Integration Services&#41;](../../integration-services/system-views/views-integration-services-catalog.md).  
  
-   Compteurs de performance  
  
     Pour plus d’informations, consultez [Compteurs de performances](../../integration-services/performance/performance-counters.md).  
  
-   Drainages de données  
  
## Types d'opération  
 Plusieurs types d’opérations différents sont surveillés dans le catalogue **SSISDB**, sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Plusieurs messages peuvent être associés à chaque opération. Chaque message peut être classifié dans l'un des différents types. Par exemple, un message peut être de type Informations, Warning ou Error. Pour obtenir la liste complète des types de messages, consultez la documentation de la vue Transact-SQL [catalog.operation_messages &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md). Pour obtenir une liste complète des types d’opérations, consultez [catalog.operations &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md).  
  
 Neuf types d'état différents sont utilisés pour indiquer l'état d'une opération. Pour obtenir une liste complète des types de statuts, consultez la vue [catalog.operations &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md).  
  
## Contenu connexe  
 Entrée de blog [Vue d’ensemble de l’API SSIS T-SQL](http://go.microsoft.com/fwlink/?LinkId=249051), sur blogs.msdn.com.  
  
  