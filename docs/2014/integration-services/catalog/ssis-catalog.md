---
title: Catalogue SSIS | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 24bd987e-164a-48fd-b4f2-cbe16a3cd95e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 14de3fa15fa5a648c2d41824d237040b5aa085e5
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58377474"
---
# <a name="ssis-catalog"></a>Catalogue SSIS
  Le `SSISDB` catalogue est le point central pour travailler avec [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] projets (SSIS) que vous avez déployés sur le [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server. Ainsi, c'est dans ce catalogue que vous définissez les paramètres de projet et de package, configurez les environnements pour spécifier des valeurs d'exécution pour les packages, exécutez et résolvez les problèmes relatifs aux packages, et gérez les opérations du serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Les objets qui sont stockés dans le `SSISDB` catalogue inclut les projets, packages, paramètres, des environnements et l’historique opérationnel.  
  
 Vous Inspectez les objets, paramètres et les données opérationnelles sont stockées dans le `SSISDB` catalogue, en interrogeant les vues dans le `SSISDB` base de données. Vous gérez des objets en appelant des procédures stockées le `SSISDB` de base de données ou à l’aide de l’interface utilisateur de la `SSISDB` catalogue. Dans de nombreux cas, la même tâche peut être effectuée dans l'interface utilisateur ou en appelant une procédure stockée.  
  
 Pour maintenir la base de données `SSISDB`, il est recommandé d'appliquer des stratégies d'entreprise standard pour la gestion des bases de données utilisateur. Pour plus d'informations sur la création de plans de maintenance, consultez [Maintenance Plans](../../relational-databases/maintenance-plans/maintenance-plans.md).  
  
 Le `SSISDB` catalogue et le `SSISDB` prise en charge de la base de données Windows PowerShell. Pour plus d'informations sur l'utilisation de SQL Server avec Windows PowerShell, consultez [SQL Server PowerShell](../../powershell/sql-server-powershell.md). Pour des exemples d'utilisation de Windows PowerShell pour exécuter des tâches telles que le déploiement d'un projet, consultez l'entrée de blog [SSIS et PowerShell dans SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=242539), sur blogs.msdn.com.  
  
 Pour plus d’informations sur l’affichage des données opérationnelles, consultez [surveillance des exécutions de Package et d’autres opérations](../performance/monitor-running-packages-and-other-operations.md).  
  
 Vous accédez à la `SSISDB` catalogue dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] en vous connectant à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] moteur de base de données, puis en développant le **catalogues Integration Services** nœud dans l’Explorateur d’objets. Vous accédez à la `SSISDB` dans la base de données [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] en développant le nœud bases de données dans l’Explorateur d’objets.  
  
> [!NOTE]  
>  Vous ne pouvez pas renommer la `SSISDB` base de données.  
  
> [!NOTE]  
>  Si le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l’instance qui le `SSISDB` base de données est attachée à arrête ou ne répond pas, le ISServerExec.exe fin du processus. Un message est écrit dans un journal des événements Windows.  
>   
>  Si les ressources [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] basculent dans le cadre d'un basculement de cluster, les packages en cours de exécution ne redémarrent pas. Vous pouvez utiliser les points de contrôle pour redémarrer les packages. Pour plus d'informations, consultez [Redémarrer des packages à l'aide de points de contrôle](../packages/restart-packages-by-using-checkpoints.md).  
  
## <a name="catalog-object-identifiers"></a>Identificateurs d'objets de catalogue  
 Lorsque vous créez un objet dans le catalogue, attribuez-lui un nom. Ce nom constitue l'identificateur de l'objet. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définit des règles quant aux caractères pouvant être utilisés dans un identificateur. Les noms des objets suivants doivent respecter les règles liées aux identificateurs.  
  
-   Dossier  
  
-   Projet  
  
-   Environnement  
  
-   Paramètre  
  
-   Variable d'environnement  
  
### <a name="folder-project-environment"></a>Dossier, projet, environnement  
 Lorsque vous renommez un dossier, un projet ou un environnement, respectez les règles suivantes.  
  
-   Les caractères non valides sont les caractères ASCII/Unicode allant de 1 à 31, les guillemets ("), le signe inférieur à (\<), le signe supérieur à (>), la barre verticale (|), le retour arrière (\b), la valeur null (\0) et la tabulation (\t).  
  
-   Le nom ne peut pas contenir d'espaces de début ni de fin.  
  
-   \@ ne doit pas être utilisé comme premier caractère, mais il peut l’être par la suite \@.  
  
-   La longueur du nom doit être supérieure à 0 et inférieure ou égale à 128.  
  
### <a name="parameter"></a>Paramètre  
 Lorsque vous affectez un nom à un paramètre, respectez les règles suivantes :  
  
-   Le premier caractère du nom doit être une lettre, ainsi que défini dans la norme Unicode 2.0, ou un trait de soulignement (_).  
  
-   Les caractères suivants peuvent être des lettres ou des nombres conformément à la norme Unicode 2.0, ou un trait de soulignement (_).  
  
### <a name="environment-variable"></a>Variable d'environnement  
 Lorsque vous attribuez un nom à une variable d'environnement, respectez les règles suivantes :  
  
-   Les caractères non valides sont les caractères ASCII/Unicode allant de 1 à 31, les guillemets ("), le signe inférieur à (\<), le signe supérieur à (>), la barre verticale (|), le retour arrière (\b), la valeur null (\0) et la tabulation (\t).  
  
-   Le nom ne peut pas contenir d'espaces de début ni de fin.  
  
-   \@ ne doit pas être utilisé comme premier caractère, mais il peut l’être par la suite \@.  
  
-   La longueur du nom doit être supérieure à 0 et inférieure ou égale à 128.  
  
-   Le premier caractère du nom doit être une lettre, ainsi que défini dans la norme Unicode 2.0, ou un trait de soulignement (_).  
  
-   Les caractères suivants peuvent être des lettres ou des nombres conformément à la norme Unicode 2.0, ou un trait de soulignement (_).  
  
## <a name="catalog-configuration"></a>Configuration du catalogue  
 Pour définir précisément le comportement du catalogue, vous devez ajuster ses propriétés. Les propriétés du catalogue définissent la façon dont les données sensibles sont chiffrées, ainsi que la façon dont les opérations et les données du contrôle de version des projets sont conservées. Pour définir les propriétés du catalogue, utilisez la boîte de dialogue **Propriétés du catalogue** ou appelez la procédure stockée [catalog.configure_catalog &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database). Pour afficher les propriétés, utilisez la boîte de dialogue ou interrogez [catalog.configure_catalog &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database). Cette boîte de dialogue est accessible en cliquant avec le bouton droit sur `SSISDB` dans l'Explorateur d'objets.  
  
### <a name="operations-and-project-version-cleanup"></a>Nettoyage des opérations et des versions de projet  
 Les données d'état de nombreuses opérations du catalogue sont stockées dans des tables de base de données internes. Ainsi, le catalogue effectue le suivi de l'état des exécutions de packages et des déploiements de projets. Pour limiter la taille des données opérationnelles, le **travail de maintenance de serveur SSIS** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est utilisé pour supprimer les anciennes données. Ce travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est créé lors de l'installation de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Vous pouvez mettre à jour ou redéployer un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en le déployant avec le même nom dans le même dossier du catalogue. Par défaut, chaque fois que vous redéployez un projet, le `SSISDB` catalogue conserve la version précédente du projet. Pour limiter la taille des données opérationnelles, le **travail de maintenance de serveur SSIS** est utilisé pour supprimer les anciennes versions des projets.  
  
 Ce qui suit `SSISDB` propriétés du catalogue définissent comment cette [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se comporte de travail de l’Agent. Vous pouvez afficher et modifier les propriétés à l’aide de la boîte de dialogue **Propriétés du catalogue** ou à l’aide de [catalog.catalog_properties &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database) et [catalog.configure_catalog &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database).  
  
 **Nettoyer les journaux régulièrement**  
 L'étape de travail de nettoyage des opérations s'exécute lorsque cette propriété a la valeur `True`.  
  
 **Période de rétention (jours)**  
 Définit l'âge maximal des données opérationnelles autorisées (en jours). Les données plus anciennes sont supprimées.  
  
 La valeur minimale est de un jour. La valeur maximale est limitée uniquement par la valeur maximale de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `int` données. Pour plus d’informations sur ce type de données, consultez [int, bigint, smallint et tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql).  
  
 **Supprimer régulièrement les anciennes versions**  
 L'étape de travail de nettoyage des versions de projet s'exécute lorsque cette propriété a la valeur `True`.  
  
 **Nombre maximal de versions par projet**  
 Définit le nombre de versions d’un projet stockées dans le catalogue. Les versions antérieures des projets sont supprimées.  
  
### <a name="encryption-algorithm"></a>Algorithme de chiffrement  
 La propriété **Algorithme de chiffrement** spécifie le type de chiffrement utilisé pour chiffrer les valeurs des paramètres sensibles. Vous pouvez faire votre choix parmi les types de chiffrement suivants.  
  
-   AES_256 (par défaut)  
  
-   AES_192  
  
-   AES_128  
  
-   DESX  
  
-   TRIPLE_DES_3KEY  
  
-   TRIPLE_DES  
  
-   DES  
  
 Lorsque vous déployez un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], le catalogue chiffre automatiquement les données du package et les valeurs sensibles. Le catalogue déchiffre automatiquement les données lorsque vous les récupérez. Le catalogue SSISDB utilise le niveau de protection `ServerStorage`. Pour plus d'informations, consultez [Access Control for Sensitive Data in Packages](../security/access-control-for-sensitive-data-in-packages.md).  
  
 La modification de l'algorithme de chiffrement est une opération qui prend du temps. Tout d'abord, le serveur doit utiliser l'algorithme précédemment spécifié pour déchiffrer toutes les valeurs de configuration. Le serveur doit ensuite utiliser le nouvel algorithme pour ré-chiffrer les valeurs. Pendant ce temps, aucune autre opération [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ne peut être effectuée sur le serveur. Ainsi, pour permettre aux opérations [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de continuer de façon ininterrompue, l’algorithme de chiffrement est une valeur en lecture seule dans la boîte de dialogue dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 Pour modifier le **algorithme de chiffrement** paramètre de propriété, définissez la `SSISDB` de base de données en mode mono-utilisateur, puis appelez la procédure stockée catalog.configure_catalog. Utilisez ENCRYPTION_ALGORITHM pour l’argument *property_name* . Pour connaître les valeurs de propriétés prises en charge, consultez [catalog.catalog_properties &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database). Pour plus d’informations sur la procédure stockée, consultez [catalog.configure_catalog &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database).  
  
 Pour plus d’informations sur le mode mono-utilisateur, consultez [Définir une base de données en mode mono-utilisateur](../../relational-databases/databases/set-a-database-to-single-user-mode.md). Pour plus d’informations sur le chiffrement et les algorithmes de chiffrement dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez les rubriques de la section [Chiffrement SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md).  
  
 Une clé principale de base de données est utilisée pour le chiffrement. La clé est générée lorsque vous créez le catalogue. Pour plus d’informations, consultez [Créer le catalogue SSIS](ssis-catalog.md).  
  
 Le tableau suivant répertorie les noms des propriétés apparaissant dans la boîte de dialogue **Propriétés du catalogue** et les propriétés correspondantes en vue de base de données.  
  
|Nom de la propriété (boîte de dialogue**Propriétés du catalogue** )|Nom de la propriété (vue de base de données)|  
|---------------------------------------------------------|-------------------------------------|  
|Nom de l'algorithme de chiffrement|ENCRYPTION_ALGORITHM|  
|Nettoyer les journaux régulièrement|OPERATION_CLEANUP_ENABLED|  
|Période de rétention (jours)|RETENTION_WINDOW|  
|Supprimer régulièrement les anciennes versions|VERSION_CLEANUP_ENABLED|  
|Nombre maximal de versions par projet|MAX_PROJECT_VERSIONS|  
|Niveau d'enregistrement par défaut au niveau du serveur|SERVER_LOGGING_LEVEL|  
  
## <a name="permissions"></a>Autorisations  
 Les projets, les environnements et les packages sont contenus dans des dossiers qui sont des objets sécurisables. Vous pouvez accorder des autorisations à un dossier, notamment l'autorisation de MANAGE_OBJECT_PERMISSIONS. MANAGE_OBJECT_PERMISSIONS vous permet de déléguer l'administration du contenu du dossier à un utilisateur sans avoir à accorder à celui-ci l'appartenance au rôle ssis_admin. Vous pouvez également accorder des autorisations relatives à des projets, des environnements et des opérations. Opérations incluent l’initialisation [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], déploiement de projets, création et démarrage d’exécutions, validation des projets et des packages et la configuration du `SSISDB` catalogue.  
  
 Pour plus d’informations sur les rôles de base de données, consultez [Rôles au niveau de la base de données](../../relational-databases/security/authentication-access/database-level-roles.md).  
  
 Le catalogue SSISDB utilise un déclencheur DDL, ddl_cleanup_object_permissions, pour appliquer l'intégrité des informations d'autorisations sur les éléments sécurisables SSIS. Le déclencheur est activé lorsqu'un principal de base de données, tel qu'un utilisateur de base de données, un rôle de base de données ou un rôle d'application de base de données, est supprimé de la base de données SSISDB.  
  
 Si le principal a accordé ou refusé des autorisations à d'autres principaux, révoquez les autorisations données par le fournisseur d'autorisations, avant que le principal puisse être supprimé. Sinon, un message d'erreur est retourné lorsque le système essaie de supprimer le principal. Le déclencheur supprime tous les enregistrements d'autorisation dans lesquels le principal de la base de données est un bénéficiaire.  
  
 Il est recommandé que le déclencheur n’est pas désactivé, car il garantit que n’il aucun enregistrement d’autorisation orphelin après la suppression d’un principal de base de données à partir de la `SSISDB` base de données.  
  
### <a name="managing-permissions"></a>Gestion des autorisations  
 Vous pouvez gérer les autorisations à l’aide de l’interface utilisateur de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , des procédures stockées et de l’espace de noms <xref:Microsoft.SqlServer.Management.IntegrationServices> .  
  
 Pour gérer les autorisations à l'aide de l'interface utilisateur de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , servez-vous des boîtes de dialogue suivantes.  
  
-   Dans le cas d'un dossier, utilisez la page **Autorisations** de la [Folder Properties Dialog Box](folder-properties-dialog-box.md).  
  
-   Dans le cas d'un projet, utilisez la page **Autorisations** de la [Project Properties Dialog Box](project-properties-dialog-box.md).  
  
 Pour gérer les autorisations à l’aide de Transact-SQL, appelez [catalog.grant_permission &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database), [catalog.deny_permission &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-deny-permission-ssisdb-database) et [catalog.revoke_permission &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-revoke-permission-ssisdb-database). Pour afficher les autorisations effectives pour le principal actuel pour tous les objets, interrogez [catalog.effective_object_permissions &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-effective-object-permissions-ssisdb-database). Cette rubrique fournit les descriptions des différents types d'autorisations. Pour afficher les autorisations affectées explicitement à l’utilisateur, interrogez [catalog.explicit_object_permissions &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-explicit-object-permissions-ssisdb-database).  
  
## <a name="folders"></a>Dossiers  
 Un dossier contient un ou plusieurs projets et environnements le `SSISDB` catalogue. Vous pouvez utiliser la vue [catalog.folders &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-folders-ssisdb-database) pour accéder aux informations relatives aux dossiers du catalogue. Vous pouvez utiliser les procédures stockées suivantes pour gérer des dossiers.  
  
-   [catalog.create_folder &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-create-folder-ssisdb-database)  
  
-   [catalog.delete_folder &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-delete-folder-ssisdb-database)  
  
-   [catalog.rename_folder &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-rename-folder-ssisdb-database)  
  
-   [catalog.set_folder_description &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-folder-description-ssisdb-database)  
  
## <a name="projects-and-packages"></a>Projets et packages  
 Chaque projet peut contenir plusieurs packages. Les projets et les packages peuvent contenir des paramètres et des références aux environnements. Vous pouvez accéder aux paramètres et aux références d'environnement à l'aide de la [Configure Dialog Box](configure-dialog-box.md).  
  
 Vous pouvez effectuer d'autres tâches de projet en appelant les procédures stockées suivantes.  
  
-   [catalog.delete_project &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-delete-project-ssisdb-database)  
  
-   [catalog.deploy_project &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database)  
  
-   [catalog.get_project &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-get-project-ssisdb-database)  
  
-   [catalog.move_project &#40;&#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-move-project-ssisdb-database)  
  
-   [catalog.restore_project &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database)  
  
 Ces vues fournissent des détails sur les packages, les projets et les versions des projets.  
  
-   [catalog.projects &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-projects-ssisdb-database)  
  
-   [catalog.packages &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-packages-ssisdb-database)  
  
-   [catalog.object_versions &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-object-versions-ssisdb-database)  
  
## <a name="parameters"></a>Paramètres  
 Vous utilisez des paramètres pour affecter des valeurs aux propriétés des packages au moment de l'exécution de ces packages. Pour définir la valeur d’un package ou d’un paramètres de projet et pour effacer la valeur, appelez [catalog.set_object_parameter_value &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database) et [catalog.clear_object_parameter_value &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database). Pour définir la valeur d’un paramètre pour une instance d’exécution, appelez [catalog.set_execution_parameter_value &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database). Vous pouvez récupérer les valeurs des paramètres par défaut en appelant [catalog.get_parameter_values &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database).  
  
 Ces vues affichent les paramètres de tous les packages et projets, ainsi que les valeurs de paramètre utilisées pour une instance d'exécution.  
  
-   [catalog.object_parameters &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database)  
  
-   [catalog.execution_parameter_values &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-execution-parameter-values-ssisdb-database)  
  
## <a name="server-environments-server-variables-and-server-environment-references"></a>Environnements serveur, variables de serveur et références d'environnement serveur  
 Les environnements serveur contiennent des variables de serveur. Les valeurs des variables peuvent être utilisées lorsqu'un package est exécuté ou validé sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Les procédures stockées suivantes vous permettent d'exécuter de nombreuses autres tâches de gestion sur les environnements et les variables.  
  
-   [catalog.create_environment &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-create-environment-ssisdb-database)  
  
-   [catalog.delete_environment &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-delete-environment-ssisdb-database)  
  
-   [catalog.move_environment &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-move-environment-ssisdb-database)  
  
-   [catalog.rename_environment &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-rename-environment-ssisdb-database)  
  
-   [catalog.set_environment_property &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-environment-property-ssisdb-database)  
  
-   [catalog.create_environment_variable &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-create-environment-variable-ssisdb-database)  
  
-   [catalog.delete_environment_variable &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-delete-environment-variable-ssisdb-database)  
  
-   [catalog.set_environment_variable_property &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-environment-variable-property-ssisdb-database)  
  
-   [catalog.set_environment_variable_value &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-environment-variable-value-ssisdb-database)  
  
 En appelant la procédure stockée [catalog.set_environment_variable_protection &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-environment-variable-protection-ssisdb-database), vous pouvez définir le bit de sensibilité d’une variable.  
  
 Pour utiliser la valeur d'une variable de serveur, spécifiez la référence entre le projet et l'environnement serveur. Vous pouvez utiliser les procédures stockées suivantes pour créer et supprimer des références. Vous pouvez également indiquer si l'environnement peut se trouver dans le même dossier que le projet ou dans un dossier différent.  
  
-   [catalog.create_environment_reference &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-create-environment-reference-ssisdb-database)  
  
-   [catalog.delete_environment_reference &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-delete-environment-reference-ssisdb-database)  
  
-   [catalog.set_environment_reference_type &#40;Base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-environment-reference-type-ssisdb-database)  
  
 Pour plus de détails sur les environnements et les variables, interrogez ces vues.  
  
-   [catalog.environments &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-environments-ssisdb-database)  
  
-   [catalog.environment_variables &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-environment-variables-ssisdb-database)  
  
-   [catalog.environment_references &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-environment-references-ssisdb-database)  
  
## <a name="executions-and-validations"></a>Exécutions et validations  
 Une exécution est une instance d'une exécution de package. Appelez [catalog.create_execution &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database) et [catalog.start_execution &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database) pour créer et démarrer une exécution. Pour arrêter une exécution ou une validation de package/projet, appelez [catalog.stop_operation &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database).  
  
 Pour suspendre un package en cours d'exécution et créer un fichier de vidage, appelez la procédure stockée catalog.create_execution_dump. Le fichier de vidage fournit des informations sur l'exécution d'un package, ce qui peut vous aider à résoudre les problèmes d'exécution. Pour plus d'informations sur la génération et la configuration de fichiers de vidage, consultez [Generating Dump Files for Package Execution](../troubleshooting/generating-dump-files-for-package-execution.md).  
  
 Pour plus de détails sur les exécutions, les validations et les messages enregistrés pendant les opérations, ainsi que pour obtenir des informations contextuelles sur les erreurs, interrogez ces vues.  
  
-   [catalog.executions &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database)  
  
-   [catalog.operations &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-operations-ssisdb-database)  
  
-   [catalog.operation_messages &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-operation-messages-ssisdb-database)  
  
-   [catalog.extended_operation_info &#40;Base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-extended-operation-info-ssisdb-database)  
  
-   [catalog.event_messages](/sql/integration-services/system-views/catalog-event-messages)  
  
-   [catalog.event_message_context](/sql/integration-services/system-views/catalog-event-message-context)  
  
 Vous pouvez valider des projets et des packages en appelant les procédures stockées [catalog.validate_project &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-validate-project-ssisdb-database) et [catalog.validate_package &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-validate-package-ssisdb-database). La vue [catalog.validations &#40;base de données SSISDB&#41;](/sql/integration-services/system-views/catalog-validations-ssisdb-database) fournit des informations sur les validations, telles que les références d’environnement serveur prises en compte dans la validation, s’il s’agit d’une validation de dépendance ou d’une validation complète, et si le runtime 32 bits ou 64 bits est utilisé pour exécuter le package.  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Créer le catalogue SSIS](ssis-catalog.md)  
  
-   [Sauvegarder, restaurer et déplacer le catalogue SSIS](../backup-restore-and-move-the-ssis-catalog.md)  
  
## <a name="related-content"></a>Contenu associé  
  
-   Entrée de blog, [SSIS and PowerShell in SQL Server 2012](https://go.microsoft.com/fwlink/?LinkId=242539), sur blogs.msdn.com.  
  
-   Entrée de blog [Conseils pour le contrôle d'accès du catalogue SSIS](https://go.microsoft.com/fwlink/?LinkId=246669), sur blogs.msdn.com.  
  
-   Entrée de blog, [A Glimpse of the SSIS Catalog Managed Object Model](https://go.microsoft.com/fwlink/?LinkId=254267), sur blogs.msdn.com.  
  
  
