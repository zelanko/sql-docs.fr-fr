---
title: Surveillance des exécutions de Package et d’autres opérations | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: cbbcd79f-ab9b-46ec-84cb-4821c1d16b99
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b985193eb9aa9b73d513f2d5ce8368f5d8fbb6ab
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060692"
---
# <a name="monitoring-for-package-executions-and-other-operations"></a>Analyse des exécutions de packages et d'autres opérations
  Vous pouvez surveiller les exécutions des packages [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , les validations de projet et d’autres opérations en utilisant un ou plusieurs des outils suivants. Certains outils tels que les drainages de données ne sont disponibles que pour les projets déployés sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
-   Journaux  
  
     Pour plus d’informations, consultez [Journalisation Integration Services &#40;SSIS&#41;](integration-services-ssis-logging.md).  
  
-   Rapports  
  
     Pour plus d'informations, consultez [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).  
  
-   Vues  
  
     Pour plus d’informations, consultez [Vues &#40;Catalogue Integration Services&#41;](/sql/integration-services/system-views/views-integration-services-catalog).  
  
-   Compteurs de performance  
  
     Pour plus d’informations, consultez [Compteurs de performances](performance-counters.md).  
  
-   Drainages de données  
  
## <a name="operation-types"></a>Types d'opération  
 Plusieurs types d’opérations différents sont surveillés dans le `SSISDB` de catalogue, dans le [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server. Plusieurs messages peuvent être associés à chaque opération. Chaque message peut être classifié dans l'un des différents types. Par exemple, un message peut être de type Informations, Warning ou Error. Pour obtenir la liste complète des types de messages, consultez la documentation de la vue Transact-SQL [catalog.operation_messages &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database). Pour obtenir une liste complète des types d’opérations, consultez [catalog.operations &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database).  
  
 Neuf types d'état différents sont utilisés pour indiquer l'état d'une opération. Pour obtenir une liste complète des types de statuts, consultez la vue [catalog.operations &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database).  
  
## <a name="related-content"></a>Contenu associé  
 Entrée de blog [Vue d’ensemble de l’API SSIS T-SQL](http://go.microsoft.com/fwlink/?LinkId=249051), sur blogs.msdn.com.  
  
  
