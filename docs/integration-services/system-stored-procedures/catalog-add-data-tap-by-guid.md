---
title: Catalog.add_data_tap_by_guid | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: ed9d7fa3-61a1-4e21-ba43-1ead7dfc74eb
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9bd4ecb4a6a419f1965a349d46d16d764dd83708
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogadddatatapbyguid"></a>catalog.add_data_tap_by_guid
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Ajoute un drainage de données à un chemin de flux de données spécifique dans un flux de données de package, pour une instance d'exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog add_data_tap_by_guid [ @execution_id = ] execution_id  
, [ @dataflow_task_guid = ] dataflow_task_guid   
, [ @dataflow_path_id_string = ] dataflow_path_id_string  
, [ @data_filename = ] data_filename  
, [ @max_rows = ] max_rows  
, [ @data_tap_id = ] data_tap_id  
```  
  
## <a name="arguments"></a>Arguments  
 [ @execution_id =] *execution_id*  
 ID de l'exécution contenant le package. Le *execution_id* est un **bigint**.  
  
 [ @dataflow_task_guid =] *dataflow_task_guid*  
 ID du flux de tâches de données dans le package qui contient le chemin d'accès au flux de données à drainer. Le *dataflow_task_guid* est un**uniqueidentifier**.  
  
 [ @dataflow_path_id_string =] *dataflow_path_id_string*  
 La chaîne d’identification pour le chemin d’accès du flux de données. Un chemin d'accès connectent deux composants de flux de données. Le **IdentificationString** propriété pour le chemin d’accès spécifie la chaîne.  
  
 Pour rechercher la chaîne d’identification, dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] avec le bouton droit le chemin d’accès entre les composants de flux de données de deux, puis cliquez sur **propriétés**. Le **IdentificationString** propriété s’affiche dans le **propriétés** fenêtre.  
  
 Le *dataflow_path_id_string* est un **nvarchar (4000)**.  
  
 [ @data_filename =] *data_filename*  
 Nom du fichier qui stocke les données drainées. Si la tâche de flux de données s'exécute à l'intérieur d'un conteneur de boucles Foreach ou For, des fichiers distincts stockent les données drainées pour chaque itération de la boucle. Chaque fichier a pour préfixe un nombre qui correspond à une itération. Fichiers de drainage de données sont écrits dans le dossier «*\<dossier d’installation de SQL Server >*\130\DTS\\». Le *data_filename* est un **nvarchar (4000)**.  
  
 [ @max_rows =] max_rows  
 Nombre de lignes capturées pendant le drainage de données. Si cette valeur n'est pas spécifiée, toutes les lignes sont capturées. Max_rows est un **int**.  
  
 [ @data_tap_id =] *data_tap_id*  
 ID de la collecte de données. Le *data_tap_id* est un **bigint**.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un drainage de données est créé sur le chemin d’accès de flux de données, `Paths[SRC DimDCVentor.OLE DB Source Output]`, dans le flux de données tâche `{D978A2E4-E05D-4374-9B05-50178A8817E8}`. Les données drainées sont stockées dans le fichier DCVendorOutput.csv.  
  
```sql
exec catalog.add_data_tap_by_guid   @execution_id,   
'{D978A2E4-E05D-4374-9B05-50178A8817E8}',   
'Paths[SRC DimDCVentor.OLE DB Source Output]',   
'D:\demos\datafiles\DCVendorOutput.csv'  
```  
  
## <a name="remarks"></a>Notes  
 Pour ajouter des drainages de données, l’instance de l’exécution doit être dans l’état créé (une valeur de 1 dans le **état** colonne de la [catalog.operations &#40; Base de données SSISDB &#41; ](../../integration-services/system-views/catalog-operations-ssisdb-database.md)affichage). La valeur d'état change lorsque vous exécutez l'exécution. Vous pouvez créer une exécution en appelant [catalog.create_execution &#40; Base de données SSISDB &#41; ](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md).  
  
 Les considérations suivantes sont à prendre en compte pour la procédure stockée add_data_tap_by_guid.  
  
-   Lorsque vous ajoutez un drainage de données, celui-ci n'est pas validé tant que le package n'est pas exécuté.  
  
-   Il est recommandé de limiter le nombre de lignes capturées pendant le drainage des données, pour éviter de générer des fichiers de données de grande taille. Si l'ordinateur sur lequel la procédure stockée est exécutée ne dispose pas d'assez d'espace de stockage pour les fichiers de données, la procédure arrête l'exécution.  
  
-   L'exécution de la procédure stockée add_data_tap_by_guid affecte les performances du package. Il est recommandé d'exécuter la procédure stockée seulement pour résoudre des problèmes de données.  
  
-   Pour accéder au fichier qui stocke les données drainées, vous devez disposer d'autorisations d'administrateur sur l'ordinateur où la procédure stockée est exécutée, ou vous devez être l'utilisateur qui a lancé l'exécution qui contient le package avec le drainage de données.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)  
  
  
