---
title: "Procédures (catalogue Integration Services) | Documents Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- stored procedures [Integration Services]
ms.assetid: a6ccd884-108f-4fb6-95ad-00b9cb65d5d6
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 21715bf65f3a85669dfe823511ddb9b6c2dd4d57
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="stored-procedures-integration-services-catalog"></a>Procédures stockées (catalogue Integration Services)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Cette section décrit les procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] qui sont disponibles pour l'administration des projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] déployés dans une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Appelez le [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] des procédures stockées pour ajouter, supprimer, modifier ou exécuter des objets qui sont stockés dans le **SSISDB** catalogue.  
  
 Le nom par défaut du catalogue est SSISDB. Les objets stockés dans le catalogue incluent des projets, des packages, des paramètres, des environnements et l'historique opérationnel.  
  
 Vous pouvez utiliser directement les vues de base de données et les procédures stockées, ou écrire du code personnalisé qui appelle l'API managée. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] et l'API managée interrogent les vues et appellent les procédures stockées décrites dans cette section pour effectuer de nombreuses tâches.  
  
## <a name="in-this-section"></a>Dans cette section  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)  
 Ajoute un drainage de données sur la sortie d'un composant dans un flux de données de package.  
  
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
 Ajoute un drainage de données à un chemin de flux de données spécifique dans un flux de données de package.  
  
 [catalog.check_schema_version](../../integration-services/system-stored-procedures/catalog-check-schema-version.md)  
 Détermine si le schéma de catalogue SSISDB et les binaires [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (assembly ISServerExec et SQLCLR) sont compatibles.  
  
 [Catalog.clear_object_parameter_value &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database.md)  
 Efface la valeur d'un paramètre pour un projet ou un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] existant stocké sur le serveur.  
  
 [Catalog.configure_catalog &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md)  
 Configure le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en définissant une propriété de catalogue sur une valeur spécifiée.  
  
 [catalog.create_environment &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-ssisdb-database.md)  
 Crée un environnement dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.create_environment_reference &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-reference-ssisdb-database.md)  
 Crée une référence environnementale pour un projet dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.create_environment_variable &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-variable-ssisdb-database.md)  
 Crée une variable d'environnement dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.create_execution &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md)  
 Crée une instance d'exécution dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.create_execution_dump](../../integration-services/system-stored-procedures/catalog-create-execution-dump.md)  
 Provoque la suspension d'un package en cours d'exécution et la création d'un fichier de vidage par ce dernier.  
  
 [catalog.create_folder &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-create-folder-ssisdb-database.md)  
 Crée un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.delete_environment &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-ssisdb-database.md)  
 Supprime un environnement d'un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.delete_environment_reference &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-reference-ssisdb-database.md)  
 Supprime une référence environnementale d'un projet dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.delete_environment_variable &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-variable-ssisdb-database.md)  
 Supprime une variable d'environnement d'un environnement dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.delete_folder &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-delete-folder-ssisdb-database.md)  
 Supprime un dossier du catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.delete_project &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-delete-project-ssisdb-database.md)  
 Supprime un projet existant d'un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.deny_permission &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-deny-permission-ssisdb-database.md)  
 Refuse une autorisation sur un objet sécurisable dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.deploy_project &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database.md)  
 Déploie un projet dans un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ou met à jour un projet existant qui a été déployé précédemment.  
  
 [Catalog.get_parameter_values &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database.md)  
 Résout et extrait les valeurs de paramètre par défaut d'un projet et les packages correspondants dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.get_project &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-get-project-ssisdb-database.md)  
 Extrait les propriétés d'un projet existant dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.grant_permission &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md)  
 Accorde une autorisation sur un objet sécurisable dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.move_environment &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-move-environment-ssisdb-database.md)  
 Déplace un environnement d'un dossier vers un autre dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.move_project &#40;&#40;Base de données SSISDB&#41;](../Topic/catalog.move_project%20\(\(SSISDB%20Database\).md)  
 Déplace un projet d'un dossier vers un autre dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.remove_data_tap](../../integration-services/system-stored-procedures/catalog-remove-data-tap.md)  
 Supprime un drainage de données d'une sortie de composant dans une exécution.  
  
 [catalog.rename_environment &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-rename-environment-ssisdb-database.md)  
 Renomme un environnement dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.rename_folder &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-rename-folder-ssisdb-database.md)  
 Renomme un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.restore_project &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database.md)  
 Restaure un projet dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] dans une version précédente.  
  
 [Catalog.revoke_permission &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-revoke-permission-ssisdb-database.md)  
 Révoque une autorisation sur un objet sécurisable dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_environment_property &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-property-ssisdb-database.md)  
 Définit la propriété d'un environnement dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_environment_reference_type &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-reference-type-ssisdb-database.md)  
 Définit le type de référence et le nom de l'environnement associés à une référence environnementale existante pour un projet dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_environment_variable_property &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-property-ssisdb-database.md)  
 Définit la propriété d'une variable d'environnement dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.set_environment_variable_protection &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-protection-ssisdb-database.md)  
 Définit le bit de critère de diffusion d'une variable d'environnement dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_environment_variable_value &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-value-ssisdb-database.md)  
 Définit la valeur d'une variable d'environnement dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_execution_parameter_value &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
 Définit la valeur d'un paramètre pour une instance d'exécution dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_execution_property_override_value](../../integration-services/system-stored-procedures/catalog-set-execution-property-override-value.md)  
 Définit la valeur d'une propriété pour une instance d'exécution dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.set_folder_description &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-folder-description-ssisdb-database.md)  
 Définit la description d'un dossier dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.set_object_parameter_value &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database.md)  
 Définit la valeur d'un paramètre dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Associe la valeur à une variable d'environnement ou affecte une valeur littérale qui sera utilisée par défaut si aucune autre valeur n'est affectée.  
  
 [Catalog.start_execution &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)  
 Démarre une instance d'exécution dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [catalog.startup](../../integration-services/system-stored-procedures/catalog-startup.md)  
 Effectue la maintenance de l'état des opérations pour le catalogue SSISDB.  
  
 [Catalog.stop_operation &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database.md)  
 Arrête une validation ou une instance d'exécution dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.validate_package &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-validate-package-ssisdb-database.md)  
 Valide de façon asynchrone un package dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 [Catalog.validate_project &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-validate-project-ssisdb-database.md)  
 Valide de façon asynchrone un projet dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
[Catalog.add_execution_worker &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md)   
Ajoute un [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] montée en puissance des processus de travail une instance d’exécution de monter en charge.

[Catalog.enable_worker_agent &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-enable-worker-agent-ssisdb-database.md)   
Activer un montée en puissance des processus de travail pour travailler avec cette mise à l’échelle Out maître [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalogue.

[Catalog.disable_worker_agent &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-disable-worker-agent-ssisdb-database.md)   
Désactiver un montée en puissance des processus de travail pour travailler avec cette mise à l’échelle Out maître [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] catalogue.



