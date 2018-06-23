---
title: Affichage et arrêt des Packages en cours d’exécution sur l’intégration de serveur Services | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- packages [Integration Services], managing
- managing running packages [Integration Services]
- packages [Integration Services], running
- running package [Integration Services], managing
ms.assetid: 11bf44e6-f6b0-475f-b816-40e914dbac80
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: ce4fd750986269c0e92ae2ea764f02e1bd642cb7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141618"
---
# <a name="viewing-and-stopping-packages-running-on-the-integration-services-server"></a>Affichage et arrêt des packages exécutés sur le serveur Integration Services
  Le `SSISDB` base de données stocke l’historique d’exécution dans des tables internes qui ne sont pas visibles par les utilisateurs. Cependant, elle expose les informations dont vous avez besoin via des vues publiques que vous pouvez interroger. Elle fournit également des procédures stockées que vous pouvez appeler pour effectuer des tâches courantes liées aux packages.  
  
 En général, vous gérez des objets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur le serveur dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Cependant, vous pouvez également interroger les vues de base de données et appeler les procédures stockées directement, ou écrire du code personnalisé qui appelle l'API managé. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et l’API managé interrogent les vues et appeler les procédures stockées pour effectuer de nombreuses tâches. Par exemple, vous pouvez afficher la liste des packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui sont en cours d'exécution sur le serveur, et demander l'arrêt de packages si nécessaire.  
  
## <a name="viewing-the-list-of-running-packages"></a>Affichage de la liste de packages en cours d'exécution  
 Vous pouvez afficher la liste des packages en cours d'exécution sur le serveur dans la boîte de dialogue **Opérations actives** . Pour plus d'informations, consultez [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).  
  
 Pour plus d'informations sur les autres méthodes que vous pouvez utiliser pour afficher la liste de packages en cours d'exécution, consultez les rubriques suivantes.  
  
 Accès à [!INCLUDE[tsql](../includes/tsql-md.md)]  
 Pour afficher la liste des packages qui s’exécutent sur le serveur, interrogez la vue, [catalog.executions &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database) pour les packages qui ont l’état 2.  
  
 Accès par programmation via l'API managé  
 Consultez l’espace de noms <xref:Microsoft.SqlServer.Management.IntegrationServices> et ses classes.  
  
## <a name="stopping-a-running-package"></a>Arrêt d'un package en cours d'exécution  
 Vous pouvez demander l'arrêt d'un package en cours d’exécution dans la boîte de dialogue **Opérations actives** . Pour plus d'informations, consultez [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).  
  
 Pour plus d'informations sur les autres méthodes que vous pouvez utiliser pour arrêter l'exécution d'un package, consultez les rubriques suivantes.  
  
 Accès à [!INCLUDE[tsql](../includes/tsql-md.md)]  
 Pour arrêter un package en cours d’exécution sur le serveur, appelez la procédure stockée, [catalog.stop_operation &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database).  
  
 Accès par programmation via l'API managé  
 Consultez l’espace de noms <xref:Microsoft.SqlServer.Management.IntegrationServices> et ses classes.  
  
## <a name="viewing-the-history-of-packages-that-have-run"></a>Affichage de l'historique des packages qui ont été exécutés  
 Pour afficher l’historique des packages exécutés dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], utilisez le rapport **Toutes les exécutions**. Pour plus d’informations sur le rapport **Toutes les exécutions** et d’autres rapports standard, consultez [Rapports du serveur Integration Services](../../2014/integration-services/reports-for-the-integration-services-server.md).  
  
 Pour plus d'informations sur les autres méthodes que vous pouvez utiliser pour afficher l'historique des packages en cours d'exécution, consultez les rubriques suivantes.  
  
 Accès à [!INCLUDE[tsql](../includes/tsql-md.md)]  
 Pour afficher des informations relatives aux packages qui ont été exécutés, interrogez la vue, [catalog.executions &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database).  
  
 Accès par programmation via l'API managé  
 Consultez l’espace de noms <xref:Microsoft.SqlServer.Management.IntegrationServices> et ses classes.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de projets et de packages](packages/run-integration-services-ssis-packages.md)   
 [Rapports de dépannage pour l’exécution des packages](troubleshooting/troubleshooting-reports-for-package-execution.md)  
  
  
