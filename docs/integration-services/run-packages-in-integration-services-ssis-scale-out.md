---
title: "Ex&#233;cuter des packages dans Integration Services (SSIS) Scale Out | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c2f4cd7-9c47-416d-bb1e-40acc3e05342
caps.latest.revision: 5
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 5
---
# Ex&#233;cuter des packages dans Integration Services (SSIS) Scale Out
Une fois les packages déployés sur le serveur Integration Services, vous pouvez les exécuter dans Scale Out.

## <a name="run-packages-with-execute-package-in-scale-out-dialog"></a>Exécuter des packages avec la boîte de dialogue **Exécuter un package dans Scale Out** 

1. ### <a name="open-the-execute-package-in-scale-out-dialog-box"></a>Ouvrir la boîte de dialogue Exécuter un package dans Scale Out ###
    Dans [!INCLUDE[ssManStudioFull_md](../includes/ssmanstudiofull-md.md)], connectez-vous au serveur Integration Services. Dans l’Explorateur d’objets, développez l’arborescence pour afficher les nœuds sous **Catalogues Integration Services**. Cliquez avec le bouton droit sur le nœud **SSISDB** ou sur le projet ou le package que vous souhaitez exécuter, puis cliquez sur **Exécuter dans Scale Out**.
2. ### <a name="select-packages-and-set-the-options"></a>Sélectionner les packages et définir les options ###
    Dans la page **Sélection des packages**, vous sélectionnez plusieurs packages à exécuter et vous définissez l’environnement, les paramètres, les gestionnaires de connexions et les options avancées pour chaque package. Cliquez sur un package pour définir ces options.
    
    Sous l’onglet **Avancé**, vous définissez une option Scale Out appelée **Nombre de nouvelles tentatives**. Elle définit le nombre de nouvelles tentatives d’exécution du package en cas d’échec.
3. ### <a name="select-machines"></a>Sélectionner les ordinateurs ###
    Dans la page **Sélection des ordinateurs**, vous sélectionnez les ordinateurs Scale Out Worker où exécuter les packages. Par défaut, tout ordinateur est autorisé à exécuter les packages. 

   > [!NOTE]
> Les packages sont exécutés avec les informations d’identification des comptes d’utilisateur des services Scale Out Worker, qui sont affichées dans la page **Sélection des ordinateurs**. Par défaut, le compte est NT Service\SSISScaleOutWorker140. Vous souhaiterez peut-être les remplacer par vos propres comptes de laboratoire.

4. ### <a name="run-the-packages-and-view-reports"></a>Exécuter les packages et afficher des rapports 
    Cliquez sur **OK** pour démarrer les exécutions de package. Pour afficher le rapport d’exécution d’un package, cliquez sur le package dans l’Explorateur d’objets, cliquez sur **Rapports**, sur **Toutes les exécutions**, et recherchez l’exécution.
    
    
## <a name="run-packages-with-stored-procedures"></a>Exécuter des packages avec des procédures stockées

1. ### <a name="create-executions"></a>Créer des exécutions ###
    Appelez [catalog].[create_execution] pour chaque package. Affectez la valeur True au paramètre **@runincluster**. Si les ordinateurs Scale Out Worker ne sont pas tous autorisés à exécuter le package, affectez la valeur False au paramètre **@useanyworker**.   
2. ### <a name="set-execution-parameters"></a>Définir les paramètres d’exécution ###
    Appelez [catalog].[set_execution_parameter_value] pour chaque exécution.
3. ### <a name="set-scale-out-workers"></a>Définir les Scale Out Workers ###
    Appelez [catalog].[add_execution_worker]. Si un ordinateur est autorisé à exécuter le package, vous n’avez pas besoin d’appeler cette procédure stockée. 
4. ### <a name="start-executions"></a>Démarrer les exécutions ###
    Appelez [catalog].[start_execution]. Définissez le paramètre **@retry_count** pour définir le nombre de nouvelles tentatives d’exécution du package en cas d’échec.
    
    ### <a name="example"></a>Exemple  ###  
    L’exemple suivant exécute deux packages, package1.dtsx et package2.dtsx, dans Scale Out avec un Scale Out Worker.  
    ```
    Declare @execution_id bigint
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder1', @project_name=N'project1', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runincluster=True
    Select @execution_id
    DECLARE @var0 smallint = 1
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
    EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
    EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
    GO

    Declare @execution_id bigint
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package2.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder2', @project_name=N'project2', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runincluster=True
    Select @execution_id
    DECLARE @var0 smallint = 1
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
    EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
    EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
    GO
    ```


## <a name="permissions"></a>Permissions
L’exécution de packages dans Scale Out nécessite les autorisations suivantes :

-   L’appartenance au rôle de base de données **ssis_admin**  

-   L’appartenance au rôle de base de données **ssis_cluster_executor**  
  
-   L’appartenance au rôle serveur **sysadmin**  
    