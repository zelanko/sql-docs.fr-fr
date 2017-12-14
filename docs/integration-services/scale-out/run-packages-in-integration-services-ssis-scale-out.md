---
title: "Exécuter des packages dans SQL Server Integration Services (SSIS) Scale Out | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
f1_keywords: sql13.ssis.ssms.ispackageexecuteinscaleout.f1
ms.workload: Inactive
ms.openlocfilehash: 88537ff52ada042d642b8915342e374ecca3246e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="run-packages-in-integration-services-ssis-scale-out"></a>Exécuter des packages dans Integration Services (SSIS) Scale Out
Une fois les packages déployés sur le serveur Integration Services, vous pouvez les exécuter dans Scale Out.

## <a name="run-packages-with-execute-package-in-scale-out-dialog"></a>Exécuter des packages avec la boîte de dialogue Exécuter un package dans Scale Out 

1. Ouvrir la boîte de dialogue Exécuter un package dans Scale Out

    Dans [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)], connectez-vous au serveur Integration Services. Dans l’Explorateur d’objets, développez l’arborescence pour afficher les nœuds sous **Catalogues Integration Services**. Cliquez avec le bouton droit sur le nœud **SSISDB** ou sur le projet ou le package que vous souhaitez exécuter, puis cliquez sur **Exécuter dans Scale Out**.

2. Sélectionner les packages et définir les options

    Dans la page **Sélection des packages** , vous sélectionnez plusieurs packages à exécuter et vous définissez l’environnement, les paramètres, les gestionnaires de connexions et les options avancées pour chaque package. Cliquez sur un package pour définir ces options.
    
    Sous l’onglet **Avancé** , vous définissez une option Scale Out appelée **Nombre de nouvelles tentatives**. Elle définit le nombre de nouvelles tentatives d’exécution du package en cas d’échec.

    > [!Note]
    > L’option **Vider en cas d’erreurs** ne prend effet que si le compte exécutant le service Scale Out Worker est administrateur de l’ordinateur local.

3. Sélectionner les ordinateurs

    Dans la page **Sélection des ordinateurs** , vous sélectionnez les ordinateurs Scale Out Worker où exécuter les packages. Par défaut, tout ordinateur est autorisé à exécuter les packages. 

   > [!Note] 
   > Les packages sont exécutés avec les informations d’identification des comptes d’utilisateur des services Scale Out Worker, qui sont affichées dans la page **Sélection des ordinateurs** . Par défaut, le compte est NT Service\SSISScaleOutWorker140. Vous souhaiterez peut-être les remplacer par vos propres comptes de laboratoire.

   >[!WARNING]
   >Les exécutions de package déclenchées par différents utilisateurs sur le même Worker sont effectuées avec le même compte. Il n’existe aucune frontière de sécurité entre elles. 

4. Exécuter les packages et afficher des rapports 

    Cliquez sur **OK** pour démarrer les exécutions de package. Pour afficher le rapport d’exécution d’un package, cliquez sur le package dans l’Explorateur d’objets, cliquez sur **Rapports**, sur **Toutes les exécutions**, et recherchez l’exécution.
    
## <a name="run-packages-with-stored-procedures"></a>Exécuter des packages avec des procédures stockées

1. Créer des exécutions

    Appelez [catalog].[create_execution] pour chaque package. Affectez la valeur True au paramètre **@runinscaleout**. Si les ordinateurs Scale Out Worker ne sont pas tous autorisés à exécuter le package, affectez la valeur False au paramètre **@useanyworker** .   

2. Définir les paramètres d’exécution

    Appelez [catalog].[set_execution_parameter_value] pour chaque exécution.

3. Définir les Scale Out Workers

    Appelez [catalog].[add_execution_worker]. Si un ordinateur est autorisé à exécuter le package, vous n’avez pas besoin d’appeler cette procédure stockée. 

4. Démarrer les exécutions

    Appelez [catalog].[start_execution]. Définissez le paramètre **@retry_count** pour définir le nombre de nouvelles tentatives d’exécution du package en cas d’échec.
    
#### <a name="example"></a>Exemple
L’exemple suivant exécute deux packages, package1.dtsx et package2.dtsx, dans Scale Out avec un Scale Out Worker.  

```sql
Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder1', @project_name=N'project1', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runinscaleout=True
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
GO

Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package2.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder2', @project_name=N'project2', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runinscaleout=True
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
GO
```

### <a name="permissions"></a>Permissions
L’exécution de packages dans Scale Out nécessite les autorisations suivantes :

-   L’appartenance au rôle de base de données **ssis_admin**  

-   L’appartenance au rôle de base de données **ssis_cluster_executor**  
  
-   L’appartenance au rôle serveur **sysadmin**  

## <a name="set-default-execution-mode"></a>Définir le mode d’exécution par défaut
Pour définir le mode d’exécution par défaut sur « Scale Out », cliquez avec le bouton droit sur le nœud **SSISDB** dans l’Explorateur d’objets de SSMS et sélectionnez **Propriétés**.
Dans la boîte de dialogue **Propriétés du catalogue**, définissez **Mode d’exécution par défaut à l’échelle du serveur** sur **Scale Out**.

Une fois ce paramètre défini, vous n’avez pas besoin de spécifier le paramètre **@runinscaleout** pour [catalog].[create_execution]. Les exécutions sont effectuées automatiquement dans Scale Out. 

![Mode d’exécution](media\exe-mode.PNG)

Pour basculer le mode d’exécution par défaut sur un mode non-Scale Out, définissez simplement **Mode d’exécution par défaut à l’échelle du serveur** sur **Serveur**.

## <a name="run-package-in-sql-agent-job"></a>Exécuter le package dans le travail de l’Agent SQL
Dans le travail de l’Agent SQL, vous pouvez choisir d’exécuter un package SSIS en tant qu’étape du travail. Pour exécuter le package dans Scale Out, vous pouvez tirer parti du mode d’exécution par défaut ci-dessus. Une fois le mode d’exécution par défaut défini sur « Scale Out », les packages dans les travaux de l’agent SQL sont exécutés dans Scale Out.
