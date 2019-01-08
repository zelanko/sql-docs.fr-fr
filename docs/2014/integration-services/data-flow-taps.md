---
title: Drainages de flux de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 2d847adf-4b3d-4949-a195-ef43de275077
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4e807fad8929ccb087b9ba55615b235a2950cdb1
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53376781"
---
# <a name="data-flow-taps"></a>Drainage des flux de données
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] introduit une nouvelle fonctionnalité qui vous permet d'ajouter un drainage des données au niveau du chemin d'accès d'un flux de données d'un package au moment de l'exécution et diriger la sortie à partir du drainage des données vers un fichier externe. Pour utiliser cette fonctionnalité, vous devez déployer votre projet SSIS à l'aide du modèle de déploiement de projet sur un serveur SSIS. Après avoir déployé le package sur le serveur, vous devez exécuter des scripts T-SQL sur la base de données SSISDB pour ajouter des drainages de données avant d'exécuter le package. Voici un exemple de scénario :  
  
1.  Créez une instance d’exécution d’un package à l’aide de la procédure stockée [catalog.create_execution &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database).  
  
2.  Ajoutez un drainage de données à l’aide d’une procédure stockée [catalog.add_data_tap](/sql/integration-services/system-stored-procedures/catalog-add-data-tap) ou [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid).  
  
3.  Démarrez l’instance d’exécution du package à l’aide de [catalog.start_execution &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database).  
  
 Voici un exemple de script SQL qui exécute les étapes décrites dans le scénario ci-dessus :  
  
```  
  
Declare @execid bigint  
EXEC [SSISDB].[catalog].[create_execution] @folder_name=N'ETL Folder', @project_name=N'ETL Project', @package_name=N'Package.dtsx', @execution_id=@execid OUTPUT  
EXEC [SSISDB].[catalog].add_data_tap @execution_id = @execid, @task_package_path = '\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[Flat File Source.Flat File Source Output]', @data_filename = 'output.txt'  
EXEC [SSISDB].[catalog].[start_execution] @execid  
  
```  
  
 Les paramètres folder_name, project_name et package_name de la procédure stockée create_execution correspondent au dossier, au projet et au package dans le catalogue Integration Services. Vous pouvez obtenir les noms de dossier, projet et package à utiliser dans l'appel de create_execution dans SQL Server Management Studio comme le montre l'image suivante. Si le projet SSIS ne s'affiche pas ici, vous n'avez peut-être pas encore déployé le projet sur le serveur SSIS. Cliquez avec le bouton droit sur le projet SSIS dans Visual Studio, puis cliquez sur Déployer pour déployer le projet sur le serveur SSIS prévu.  
  
 Au lieu de taper des instructions SQL, générez le script d'exécution de package en procédant comme suit :  
  
1.  Cliquez avec le bouton droit sur **Package.dtsx** , puis sélectionnez **Exécuter**.  
  
2.  Cliquez sur le bouton de la barre d'outils **Script** pour générer le script.  
  
3.  Ajoutez l'instruction add_data_tap avant l'appel de start_execution.  
  
 Le paramètre task_package_path de la procédure stockée add_data_tap correspond à la propriété PackagePath de la tâche de flux de données dans Visual Studio. Dans Visual Studio, cliquez avec le bouton droit sur **Tâche de flux de données**, puis cliquez sur **Propriétés** pour lancer la fenêtre Propriétés.  Notez la valeur de la propriété **PackagePath** pour l’utiliser comme valeur du paramètre task_package_path de l’appel de procédure stockée add_data_tap.  
  
 Le paramètre dataflow_path_id_string de la procédure stockée add_data_tap correspond à la propriété IdentificationString du chemin d'accès de flux de données auquel vous voulez ajouter un drainage de données. Pour obtenir dataflow_path_id_string, cliquez sur le chemin de flux de données (flèche entre les tâches du flux de données), et notez la valeur de la propriété **IdentificationString** dans la fenêtre Propriétés.  
  
 Quand vous exécutez le script, le fichier de sortie est stocké dans \<Program Files>\Microsoft SQL Server\110\DTS\DataDumps. S'il existe déjà un fichier du même nom, un nouveau fichier avec un suffixe (par exemple : output[1].txt) est créé.  
  
 Comme mentionné précédemment, vous pouvez également utiliser la procédure stockée [catalog.add_data_tap_by_guid](/sql/integration-services/system-stored-procedures/catalog-add-data-tap-by-guid)plutôt que add_data_tap. Cette procédure stockée accepte l'ID de tâche de flux de données comme paramètre au lieu de task_package_path. L'ID de tâche de flux de données est disponible dans la fenêtre Propriétés de Visual Studio.  
  
## <a name="removing-a-data-tap"></a>Suppression d'un drainage de données  
 Vous pouvez supprimer un drainage de données avant de lancer l’exécution à l’aide de la procédure stockée [catalog.remove_data_tap](/sql/integration-services/system-stored-procedures/catalog-remove-data-tap) . Cette procédure stockée accepte l'ID de drainage de données comme paramètre, que vous pouvez obtenir en tant que résultat de la procédure stockée add_data_tap.  
  
```  
  
DECLARE @tap_id bigint  
EXEC [SSISDB].[catalog].add_data_tap @execution_id = @execid, @task_package_path = '\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[Flat File Source.Flat File Source Output]', @data_filename = 'output.txt' @data_tap_id=@tap_id OUTPUT  
EXEC [SSISDB].[catalog].remove_data_tap @tap_id  
  
```  
  
## <a name="listing-all-data-taps"></a>Création de la liste de tous les drainages de données  
 Vous pouvez également afficher la liste de tous les drainages de données à l'aide de l'affichage catalog.execution_data_taps. L’exemple suivant extrait les drainages de données pour une instance d’exécution de spécification (ID : 54).  
  
```  
select * from [SSISDB].[catalog].execution_data_taps where execution_id=@execid  
```  
  
## <a name="performance-consideration"></a>Observation relative aux performances  
 Le fait d'activer le niveau de journalisation détaillée et d'ajouter des drainages de données augmente les opérations d'E/S effectuées par votre solution d'intégration de données. Par conséquent, il est recommandé d'ajouter des drainages de données uniquement à des fins de dépannage.  
  
## <a name="video"></a>Vidéo  
 Cette [vidéo sur TechNet](https://technet.microsoft.com/sqlserver/dn600163) montre comment ajouter/utiliser des drainages de données dans le catalogue SQL Server 2012 SSISDB qui permettent de déboguer des packages par programmation et de capturer les résultats partiels au moment de l’exécution. Elle explique également comment répertorier/supprimer ces drainages de données et les meilleures pratiques pour l'utilisation des drainages de données dans des packages SSIS.  
  
## <a name="related-tasks"></a>Tâches associées  
 [Débogage d'un flux de données](troubleshooting/debugging-data-flow.md)  
  
 [Outils de dépannage pour l’exécution des packages](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
  
