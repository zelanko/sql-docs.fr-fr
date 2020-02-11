---
title: Déployer et exécuter des packages SSIS à l’aide de procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 60914b0c-1f65-45f8-8132-0ca331749fcc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8cc6c9a2961696512c69f9c3e9de6d229eabb509
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72251314"
---
# <a name="deploy-and-execute-ssis-packages-using-stored-procedures"></a>Déployer et exécuter des packages SSIS à l'aide de procédures stockées
  Lorsque vous configurez un projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] afin d'utiliser le modèle de déploiement de projet, vous pouvez utiliser les procédures stockées du catalogue [!INCLUDE[ssIS](../includes/ssis-md.md)] pour déployer le projet et pour exécuter des packages. Pour plus d’informations sur le modèle de déploiement de projet, consultez [Déploiement de projets et de packages](packages/deploy-integration-services-ssis-projects-and-packages.md).  
  
 Vous pouvez également utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour déployer le projet et pour exécuter des packages. Pour plus d’informations, consultez les rubriques de la section **Voir aussi**.  
  
> [!TIP]
>  Vous pouvez facilement créer des instructions Transact-SQL pour les procédures stockées répertoriées dans la procédure ci-dessous, à l'exception de catalog.deploy_project, en procédant comme suit :  
> 
>  1.  Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], développez le nœud **Catalogues Integration Services** dans l’Explorateur d’objets et accédez au package à exécuter.  
> 2.  Cliquez avec le bouton droit sur le package, puis cliquez sur **Exécuter**.  
> 3.  Si nécessaire, définissez les valeurs des paramètres, les propriétés du gestionnaire de connexions, ainsi que les options de l’onglet **Avancé**, telles que le niveau de journalisation.  
> 
>      Pour plus d’informations sur les niveaux de journalisation, consultez [Activer la journalisation des exécutions de package sur le serveur SSIS](../../2014/integration-services/enable-logging-for-package-execution-on-the-ssis-server.md).  
> 4.  Avant de cliquer sur **OK** pour exécuter le package, cliquez sur **Script**. Transact-SQL s’affiche dans une fenêtre de l’Éditeur de requête dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
## <a name="to-deploy-and-execute-a-package-using-stored-procedures"></a>Pour déployer et exécuter un package à l'aide de procédures stockées  
  
1.  Appelez [catalog.deploy_project &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database) pour déployer le projet [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] qui contient le package sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
     Pour récupérer le contenu binaire du fichier [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] de déploiement de projet, pour le * \@paramètre project_stream* , utilisez une instruction SELECT avec la fonction OPENROWSET et le fournisseur d’ensembles de lignes en bloc. Le fournisseur d'ensembles de lignes BULK vous permet de lire des données dans un fichier. L'argument SINGLE_BLOB du fournisseur d'ensembles de lignes BULK retourne le contenu du fichier de données sous la forme d'un ensemble de lignes à une seule ligne, une seule colonne de type varbinary (max). Pour plus d’informations, consultez [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql).  
  
     Dans l’exemple suivant, le projet SSISPackages_ProjectDeployment est déployé dans le dossier SSIS Packages sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Les données binaires sont lues à partir du fichier projet (SSISPackage_ProjectDeployment. ISPAC) et sont stockées * \@* dans le paramètre ProjectBinary de type varbinary (max). La * \@* valeur du paramètre ProjectBinary est assignée au paramètre * \@project_stream* .  
  
    ```  
    DECLARE @ProjectBinary as varbinary(max)  
    DECLARE @operation_id as bigint  
    Set @ProjectBinary = (SELECT * FROM OPENROWSET(BULK 'C:\MyProjects\ SSISPackage_ProjectDeployment.ispac', SINGLE_BLOB) as BinaryData)  
  
    Exec catalog.deploy_project @folder_name = 'SSIS Packages', @project_name = 'DeployViaStoredProc_SSIS', @Project_Stream = @ProjectBinary, @operation_id = @operation_id out  
  
    ```  
  
2.  Appelez [catalog.create_execution &#40; base de données SSISDB &#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) pour créer une instance de l’exécution du package et éventuellement [catalog.set_execution_parameter_value &#40;base de données SSISDB &#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database) pour définir les valeurs de paramètres d’exécution.  
  
     Dans l'exemple suivant, catalog.create_execution crée une instance d'exécution pour le fichier package.dtsx contenu dans le projet SSISPackage_ProjectDeployment. Le projet se trouve dans le dossier SSIS Packages. L'execution_id retourné par la procédure stockée est utilisé dans l'appel à catalog.set_execution_parameter_value. Cette deuxième procédure stockée attribue au paramètre LOGGING_LEVEL la valeur 3 (journalisation verbose) et attribue à un paramètre de package nommé Parameter1 la valeur 1.  
  
     Pour les paramètres tels que LOGGING_LEVEL la valeur d'object_type est 50. Pour les paramètres de package la valeur d'object_type est 30.  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    GO  
  
    ```  
  
3.  Appelez [catalog.start_execution &#40;base de données SSISDB &#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) pour exécuter le package.  
  
     Dans l'exemple suivant, un appel à catalog.start_execution est ajouté à Transact-SQL pour démarrer l'exécution du package. L'execution_id retourné par la procédure stockée catalog.create_execution est utilisé.  
  
    ```  
    Declare @execution_id bigint  
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Package.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'SSIS Packages', @project_name=N'SSISPackage_ProjectDeployment', @use32bitruntime=False, @reference_id=1  
  
    Select @execution_id  
    DECLARE @var0 smallint = 3  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0  
  
    DECLARE @var1 int = 1  
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=30, @parameter_name=N'Parameter1', @parameter_value=@var1  
  
    EXEC [SSISDB].[catalog].[start_execution] @execution_id  
    GO  
  
    ```  
  
## <a name="to-deploy-a-project-from-server-to-server-using-stored-procedures"></a>Pour déployer un projet de serveur à serveur à l'aide de procédures stockées  
 Vous pouvez déployer un projet de serveur à serveur à l’aide des procédures stockées [catalog.get_project &#40;base de données SSISDB &#41;](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database) et [catalog.deploy_project &#40;base de données SSISDB &#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database).  
  
 Vous devez effectuer les opérations suivantes avant d'exécuter les procédures stockées.  
  
-   Créez un objet serveur lié. Pour plus d’informations, consultez [Créer des serveurs liés &#40;moteur de base de données SQL Server&#41;](../database-engine/sql-server-database-engine-overview.md).  
  
     Dans la page **Options du serveur** de la boîte de dialogue **Propriétés du serveur lié**, attribuez à **RPC** et à **Sortie RPC** la valeur **True**. Par ailleurs, attribuez à **Activer la promotion des transactions distribuées pour RPC** la valeur **False**.  
  
-   Vérifiez les paramètres dynamiques du fournisseur que vous avez sélectionné pour le serveur lié : développez le nœud **Fournisseurs** sous **Serveurs liés** dans l’Explorateur d’objets, puis cliquez avec le bouton droit sur le fournisseur et cliquez sur **Propriétés**. Sélectionnez **Activer** en regard de **Paramètre dynamique**.  
  
-   Vérifiez que le Coordinateur de transactions distribuées (DTC, Distributed Transaction Coordinator) est démarré sur les deux serveurs.  
  
 Appelez catalog.get_project pour retourner les données binaires du projet, puis appelez catalog.deploy_project. La valeur retournée par catalog.get_project est insérée dans une variable de table de type varbinary (max). Le serveur lié ne peut pas retourner des résultats qui sont varbinary (max).  
  
 Dans l'exemple suivant, catalog.get_project retourne une valeur binaire pour le projet SSISPackages sur le serveur lié. catalog.deploy_project déploie le projet sur le serveur local, dans un dossier nommé DestFolder.  
  
```  
declare @resultsTableVar table (  
project_binary varbinary(max)  
)  
  
INSERT @resultsTableVar (project_binary)  
EXECUTE [MyLinkedServer].[SSISDB].[catalog].[get_project] 'Packages', 'SSISPackages'  
  
declare @project_binary varbinary(max)  
select @project_binary = project_binary from @resultsTableVar  
  
exec [SSISDB].[CATALOG].[deploy_project] 'DestFolder', 'SSISPackages', @project_binary  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Déployer des projets sur Integration Services Server](../../2014/integration-services/deploy-projects-to-integration-services-server.md)   
 [Exécuter un package dans SQL Server Data Tools](../../2014/integration-services/run-a-package-in-sql-server-data-tools.md)   
 [Exécuter un package sur le serveur SSIS à l’aide de SQL Server Management Studio](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
  
