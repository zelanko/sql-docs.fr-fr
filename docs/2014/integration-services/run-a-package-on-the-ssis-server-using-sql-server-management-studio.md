---
title: Exécuter un Package sur le serveur SSIS à l’aide de SQL Server Management Studio | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 56dc1bf8-99d4-41dc-bdc4-f64f1ccfd688
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7195e8159ed1b4c1fb0092ac07369196403a69f0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48119229"
---
# <a name="run-a-package-on-the-ssis-server-using-sql-server-management-studio"></a>Exécuter un package sur le serveur SSIS à l’aide de SQL Server Management Studio
  Après avoir déployé votre projet sur le serveur[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], vous pouvez exécuter le package sur le serveur.  
  
 Vous pouvez utiliser des rapports d'opérations pour afficher des informations sur les packages qui ont été exécutés, ou qui sont actuellement exécutés, sur le serveur. Pour plus d'informations, consultez [Reports for the Integration Services Server](../../2014/integration-services/reports-for-the-integration-services-server.md).  
  
### <a name="to-run-a-package-on-the-server-using-sql-server-management-studio"></a>Pour exécuter un package sur le serveur à l'aide de SQL Server Management Studio  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] et connectez-vous à l'instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui contient le catalogue [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  Dans l’Explorateur d’objets, développez le nœud **Catalogues Integration Services** , développez le nœud **SSISDB** , puis accédez au package contenu dans le projet que vous avez déployé.  
  
3.  Cliquez avec le bouton droit sur le nom du package, puis sélectionnez **Exécuter**.  
  
4.  Configurez l’exécution du package à l’aide des paramètres sous les onglets **Paramètres**, **Gestionnaires de connexions**et **Avancé** de la boîte de dialogue **Exécuter le package** .  
  
5.  Cliquez sur **OK** pour exécuter le package.  
  
     -ou-  
  
     Utilisez des procédures stockées pour exécuter le package. Cliquez sur **Script** pour générer l’instruction Transact-SQL qui crée et démarre une instance de l’exécution. L'instruction inclut un appel aux procédures stockées catalog.create_execution, catalog.set_execution_parameter_value et catalog.start_execution. Pour plus d’informations sur ces procédures stockées, consultez [catalog.create_execution &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database), [catalog.set_execution_parameter_value &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) [catalog.start_execution &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).  
  
  
