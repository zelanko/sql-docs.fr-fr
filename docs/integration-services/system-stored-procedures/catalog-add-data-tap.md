---
title: Catalog.add_data_tap | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a25ebcc7-535e-4619-adf6-4e2b5a62ba37
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 686b40e7e1ad7f7843bee5af3295fdf394538f63
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogadddatatap"></a>catalog.add_data_tap
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Ajoute un drainage de données sur la sortie d'un composant dans un flux de données de package, pour une instance d'exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.add_data_tap [ @execution_id = ] execution_id  
, [ @task_package_path = ] task_package_path  
, [ @dataflow_path_id_string = ] dataflow_path_id_string  
, [ @data_filename = ] data_filename  
, [ @max_rows = ] max_rows  
, [ @data_tap_id = ] data_tap_id OUTPUT  
```  
  
## <a name="arguments"></a>Arguments  
 [ @execution_id =] *execution_id*  
 ID de l'exécution contenant le package. Le *execution_id* est un **bigint**.  
  
 [ @task_package_path =] *task_package_path*  
 Chemin d'accès de package de la tâche de flux de données. Le **PackagePath** propriété pour la tâche de flux de données spécifie le chemin d’accès. Le chemin d'accès respecte la casse. Pour rechercher le chemin d’accès du package, dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] avec le bouton droit de la tâche de flux de données, puis cliquez sur **propriétés**. Le **PackagePath** propriété s’affiche dans le **propriétés** fenêtre.  
  
 Le *task_package_path* est un **nvarchar (max)**.  
  
 [ @dataflow_path_id_string =] *dataflow_path_id_string*  
 La chaîne d’identification pour le chemin d’accès du flux de données. Un chemin d'accès connectent deux composants de flux de données. Le **IdentificationString** propriété pour le chemin d’accès spécifie la chaîne.  
  
 Pour rechercher la chaîne d’identification, dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] avec le bouton droit le chemin d’accès entre les composants de flux de données de deux, puis cliquez sur **propriétés**. Le **IdentificationString** propriété s’affiche dans le **propriétés** fenêtre.  
  
 Le *dataflow_path_id_string* est un **nvarchar (4000)**.  
  
 [ @data_filename =] *data_filename*  
 Nom du fichier qui stocke les données drainées. Si la tâche de flux de données s'exécute à l'intérieur d'un conteneur de boucles Foreach ou For, des fichiers distincts stockent les données drainées pour chaque itération de la boucle. Chaque fichier a pour préfixe un nombre qui correspond à une itération.  
  
 Par défaut, le fichier est stocké dans le \< *lecteur*> : dossier \Program Files\Microsoft SQL Server\130\DTS\DataDumps.  
  
 Le *data_filename* est un **nvarchar (4000)**.  
  
 [ @max_rows =] *max_rows*  
 Nombre de lignes capturées pendant le drainage de données. Si cette valeur n'est pas spécifiée, toutes les lignes sont capturées. Le *max_rows* est un **int**.  
  
 [ @data_tap_id =] *data_tap_id*  
 Retourne l'ID de la collecte de données. Le *data_tap_id* est un **bigint**.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un drainage de données est créé sur le chemin d’accès de flux de données, `'Paths[OLE DB Source.OLE DB Source Output]`, dans le flux de données de tâche, `\Package\Data Flow Task`. Les données collectées sont stockées dans le `output0.txt` fichier dans le dossier DataDumps (\<*lecteur*> : \Program Files\Microsoft SQL Server\130\DTS\DataDumps).  
  
```sql
Declare @execution_id bigint  
Exec SSISDB.Catalog.create_execution @folder_name='Packages',@project_name='SSISPackages', @package_name='Package.dtsx',@reference_id=Null, @use32bitruntime=False, @execution_id=@execution_id OUTPUT  
  
Exec SSISDB.Catalog.set_execution_parameter_value @execution_id,50, 'LOGGING_LEVEL', 0  
  
Exec SSISDB.Catalog.add_data_tap @execution_id, @task_package_path='\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[OLE DB Source.OLE DB Source Output]', @data_filename = 'output0.txt'  
  
Exec SSISDB.Catalog.start_execution @execution_id  
```  
  
## <a name="remarks"></a>Notes  
 Pour ajouter des drainages de données, l’instance de l’exécution doit être dans l’état créé (une valeur de 1 dans le **état** colonne de la [catalog.operations &#40; Base de données SSISDB &#41; ](../../integration-services/system-views/catalog-operations-ssisdb-database.md)affichage). La valeur d'état change lorsque vous exécutez l'exécution. Vous pouvez créer une exécution en appelant [catalog.create_execution &#40; Base de données SSISDB &#41; ](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md).  
  
 Les considérations suivantes sont à prendre en compte pour la procédure stockée add_data_tap.  
  
-   Si une exécution contient un package parent et un ou plusieurs packages enfants, vous devez ajouter un drainage de données pour chaque package pour lequel vous souhaitez effectuer un drainage de données.  
  
-   Si un package contient plusieurs tâches de flux de données portant le même nom, task_package_path identifie de manière unique la tâche de flux de données qui contient la sortie du composant drainé.  
  
-   Lorsque vous ajoutez une collecte de données, celle-ci n'est pas validée tant que le package n'est pas exécuté.  
  
-   Il est recommandé de limiter le nombre de lignes capturées pendant le drainage des données, pour éviter de générer des fichiers de données de grande taille. Si l'ordinateur sur lequel la procédure stockée est exécutée, manque d'espace de stockage pour les fichiers de données, le package cesse de s'exécuter et un message d'erreur est consigné dans un journal.  
  
-   L'exécution de la procédure stockée add_data_tap affecte les performances du package. Il est recommandé d'exécuter la procédure stockée seulement pour résoudre des problèmes de données.  
  
-   Pour accéder au fichier qui stocke les données drainées, vous devez être administrateur sur l'ordinateur sur lequel la procédure stockée est exécutée. Vous devez également être l'utilisateur qui a démarré l'exécution contenant le package avec le drainage de données.  
  
## <a name="return-codes"></a>Codes de retour  
 0 (succès)  
  
 Lorsque la procédure stockée échoue, elle génère une erreur.  
  
## <a name="result-set"></a>Jeu de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations MODIFY sur l'instance d'exécution  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit les conditions provoquant l'échec de la procédure stockée.  
  
-   L'utilisateur ne dispose pas des autorisations MODIFY.  
  
-   Le drainage de données du composant spécifié, dans le package spécifié, a déjà été ajouté.  
  
-   La valeur spécifiée pour le nombre de lignes à capturer n'est pas valide.  
  
## <a name="requirements"></a>Spécifications  
  
## <a name="external-resources"></a>Ressources externes  
 Entrée de blog, [SSIS 2012 : A Peek to Data Taps](http://go.microsoft.com/fwlink/?LinkId=239983), sur le site rafael-salas.com.  
  
## <a name="see-also"></a>Voir aussi  
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
  
  
