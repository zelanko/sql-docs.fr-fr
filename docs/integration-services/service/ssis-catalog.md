---
title: "Catalogue SSIS | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24bd987e-164a-48fd-b4f2-cbe16a3cd95e
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Catalogue SSIS
  Le catalogue **SSISDB** est l’élément central pour l’utilisation des projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) que vous avez déployés sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Ainsi, c'est dans ce catalogue que vous définissez les paramètres de projet et de package, configurez les environnements pour spécifier des valeurs d'exécution pour les packages, exécutez et résolvez les problèmes relatifs aux packages, et gérez les opérations du serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Les objets stockés dans le catalogue **SSISDB** sont les projets, les packages, les paramètres, les environnements et l'historique opérationnel.  
  
 Vous inspectez les objets, les paramètres et les données opérationnelles stockés dans le catalogue **SSISDB** en interrogeant les vues de la base de données **SSISDB** . Vous gérez des objets en appelant des procédures stockées situées dans la base de données **SSISDB** ou à l'aide de l'interface utilisateur du catalogue **SSISDB** . Dans de nombreux cas, la même tâche peut être effectuée dans l'interface utilisateur ou en appelant une procédure stockée.  
  
 Pour maintenir la base de données **SSISDB** , il est recommandé d'appliquer des stratégies d'entreprise standard pour la gestion des bases de données utilisateur. Pour plus d'informations sur la création de plans de maintenance, consultez [Maintenance Plans](../../relational-databases/maintenance-plans/maintenance-plans.md).  
  
 Le catalogue **SSISDB** et la base de données **SSISDB** prennent en charge Windows PowerShell. Pour plus d'informations sur l'utilisation de SQL Server avec Windows PowerShell, consultez [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md). Pour des exemples d'utilisation de Windows PowerShell pour exécuter des tâches telles que le déploiement d'un projet, consultez l'entrée de blog [SSIS et PowerShell dans SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=242539), sur blogs.msdn.com.  
  
 Pour plus d’informations sur l’affichage des données opérationnelles, consultez [Surveiller les packages en cours d’exécution et autres opérations](../../integration-services/performance/monitor-running-packages-and-other-operations.md).  
  
 Vous accédez au catalogue **SSISDB** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] en vous connectant au moteur de base de données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , puis en développant le nœud **Catalogues Integration Services** dans l'Explorateur d'objets. Vous accédez à la base de données **SSISDB** de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] en développant le nœud Bases de données dans l'Explorateur d'objets.  
  
> [!NOTE] Vous ne pouvez pas renommer la base de données **SSISDB** .  
  
> [!NOTE] Si l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laque la base de données **SSISDB** est rattachée s'arrête ou ne répond pas, le processus ISServerExec.exe prend fin. Un message est écrit dans un journal des événements Windows.  
>   
>  Si les ressources [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] basculent dans le cadre d'un basculement de cluster, les packages en cours de exécution ne redémarrent pas. Vous pouvez utiliser les points de contrôle pour redémarrer les packages. Pour plus d'informations, consultez [Restart Packages by Using Checkpoints](../../integration-services/packages/restart-packages-by-using-checkpoints.md).  
  
## <a name="in-this-topic"></a>Dans cette rubrique  
  
-   [Identificateurs d’objets de catalogue](../../integration-services/service/ssis-catalog.md#CatalogObjectIdentifiers)  
  
-   [Configuration du catalogue](../../integration-services/service/ssis-catalog.md#Configuration)  
  
-   [Autorisations](../../integration-services/service/ssis-catalog.md#Permissions)  
  
-   [Dossiers](../../integration-services/service/ssis-catalog.md#Folders)  
  
-   [Projets et packages](../../integration-services/service/ssis-catalog.md#ProjectsAndPackages)  
  
-   [Paramètres](../../integration-services/service/ssis-catalog.md#Parameters)  
  
-   [Environnements serveur, variables de serveur et références d’environnement serveur](../../integration-services/service/ssis-catalog.md#ServerEnvironments)  
  
-   [Exécutions et validations](../../integration-services/service/ssis-catalog.md#Executions)  
  
-   [Prise en charge d’AlwaysOn](../../integration-services/service/ssis-catalog.md#AlwaysOn)  
  
-   [Tâches connexes](../../integration-services/service/ssis-catalog.md#RelatedTasks)  
  
-   [Contenu connexe](../../integration-services/service/ssis-catalog.md#RelatedContent)  
  
##  <a name="a-namecatalogobjectidentifiersa-catalog-object-identifiers"></a><a name="CatalogObjectIdentifiers"></a> Identificateurs d’objets de catalogue  
 Lorsque vous créez un objet dans le catalogue, attribuez-lui un nom. Ce nom constitue l'identificateur de l'objet. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] définit des règles quant aux caractères pouvant être utilisés dans un identificateur. Les noms des objets suivants doivent respecter les règles liées aux identificateurs.  
  
-   Dossier  
  
-   Projet  
  
-   Environnement  
  
-   Paramètre  
  
-   Variable d'environnement  
  
###  <a name="a-namefoldera-folder-project-environment"></a><a name="Folder"></a> Dossier, projet, environnement  
 Lorsque vous renommez un dossier, un projet ou un environnement, respectez les règles suivantes.  
  
-   Les caractères non valides sont les caractères ASCII/Unicode 1 à 31, les guillemets ("), le signe inférieur à (\<), le signe supérieur à (>), la barre verticale (|), le retour arrière (\b), la valeur null (\0) et la tabulation (\t).  
  
-   Le nom ne peut pas contenir d'espaces de début ni de fin.  
  
-   @ ne doit pas être utilisé comme premier caractère, mais les caractères suivants peuvent être @.  
  
-   La longueur du nom doit être supérieure à 0 et inférieure ou égale à 128.  
  
###  <a name="a-nameparametera-parameter"></a><a name="Parameter"></a> Paramètre  
 Lorsque vous affectez un nom à un paramètre, respectez les règles suivantes :  
  
-   Le premier caractère du nom doit être une lettre, ainsi que défini dans la norme Unicode 2.0, ou un trait de soulignement (_).  
  
-   Les caractères suivants peuvent être des lettres ou des nombres conformément à la norme Unicode 2.0, ou un trait de soulignement (_).  
  
###  <a name="a-nameenvironmentvariablea-environment-variable"></a><a name="EnvironmentVariable"></a> Variable d’environnement  
 Lorsque vous attribuez un nom à une variable d'environnement, respectez les règles suivantes :  
  
-   Les caractères non valides sont les caractères ASCII/Unicode 1 à 31, les guillemets ("), le signe inférieur à (\<), le signe supérieur à (>), la barre verticale (|), le retour arrière (\b), la valeur null (\0) et la tabulation (\t).  
  
-   Le nom ne peut pas contenir d'espaces de début ni de fin.  
  
-   @ ne doit pas être utilisé comme premier caractère, mais les caractères suivants peuvent être @.  
  
-   La longueur du nom doit être supérieure à 0 et inférieure ou égale à 128.  
  
-   Le premier caractère du nom doit être une lettre, ainsi que défini dans la norme Unicode 2.0, ou un trait de soulignement (_).  
  
-   Les caractères suivants peuvent être des lettres ou des nombres conformément à la norme Unicode 2.0, ou un trait de soulignement (_).  
  
##  <a name="a-nameconfigurationa-catalog-configuration"></a><a name="Configuration"></a> Configuration du catalogue  
 Pour définir précisément le comportement du catalogue, vous devez ajuster ses propriétés. Les propriétés du catalogue définissent la façon dont les données sensibles sont chiffrées, ainsi que la façon dont les opérations et les données du contrôle de version des projets sont conservées. Pour définir les propriétés du catalogue, utilisez la boîte de dialogue **Propriétés du catalogue** ou appelez la procédure stockée [catalog.configure_catalog &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md). Pour afficher les propriétés, utilisez la boîte de dialogue ou interrogez [catalog.configure_catalog &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md). Vous pouvez accéder à cette boîte de dialogue en cliquant avec le bouton droit sur **SSISDB** dans l’Explorateur d’objets.  
  
###  <a name="a-namecleanupa-operations-and-project-version-cleanup"></a><a name="Cleanup"></a> Nettoyage des opérations et des versions de projet  
 Les données d'état de nombreuses opérations du catalogue sont stockées dans des tables de base de données internes. Ainsi, le catalogue effectue le suivi de l'état des exécutions de packages et des déploiements de projets. Pour limiter la taille des données opérationnelles, le **travail de maintenance de serveur SSIS** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est utilisé pour supprimer les anciennes données. Ce travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est créé lors de l'installation de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Vous pouvez mettre à jour ou redéployer un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] en le déployant avec le même nom dans le même dossier du catalogue. Par défaut, chaque fois que vous redéployez un projet, le catalogue **SSISDB** en conserve la version précédente. Pour limiter la taille des données opérationnelles, le **travail de maintenance de serveur SSIS** est utilisé pour supprimer les anciennes versions des projets.  
 
Pour exécuter le **travail de maintenance du serveur SSIS**, SSIS crée la connexion SQL Server **##MS_SSISServerCleanupJobLogin##**. Cette connexion est réservée à un usage interne par SSIS.
  
 Les propriétés de catalogue **SSISDB** suivantes définissent le comportement de ce travail de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez afficher et modifier les propriétés à l’aide de la boîte de dialogue **Propriétés du catalogue** ou à l’aide de [catalog.catalog_properties &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) et [catalog.configure_catalog &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md).  
  
 **Nettoyer les journaux régulièrement**  
 L’étape de travail de nettoyage des opérations s’exécute quand cette propriété a la valeur **True**.  
  
 **Période de rétention (jours)**  
 Définit l'âge maximal des données opérationnelles autorisées (en jours). Les données plus anciennes sont supprimées.  
  
 La valeur minimale est de un jour. La valeur maximale est limitée uniquement par la valeur maximale des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **int** . Pour plus d’informations sur ce type de données, consultez [int, bigint, smallint et tinyint &#40;Transact-SQL&#41;](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md).  
  
 **Supprimer régulièrement les anciennes versions**  
 L’étape de travail de nettoyage des versions de projet s’exécute quand cette propriété a la valeur **True**.  
  
 **Nombre maximal de versions par projet**  
 Définit le nombre de versions d’un projet stockées dans le catalogue. Les versions antérieures des projets sont supprimées.  
  
###  <a name="a-nameencryptiona-encryption-algorithm"></a><a name="Encryption"></a> Algorithme de chiffrement  
 La propriété **Algorithme de chiffrement** spécifie le type de chiffrement utilisé pour chiffrer les valeurs des paramètres sensibles. Vous pouvez faire votre choix parmi les types de chiffrement suivants.  
  
-   AES_256 (par défaut)  
  
-   AES_192  
  
-   AES_128  
  
-   DESX  
  
-   TRIPLE_DES_3KEY  
  
-   TRIPLE_DES  
  
-   DES  
  
 Lorsque vous déployez un projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], le catalogue chiffre automatiquement les données du package et les valeurs sensibles. Le catalogue déchiffre automatiquement les données lorsque vous les récupérez. Le catalogue SSISDB utilise le niveau de protection **ServerStorage** . Pour plus d'informations, consultez [Access Control for Sensitive Data in Packages](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md).  
  
 La modification de l'algorithme de chiffrement est une opération qui prend du temps. Tout d'abord, le serveur doit utiliser l'algorithme précédemment spécifié pour déchiffrer toutes les valeurs de configuration. Le serveur doit ensuite utiliser le nouvel algorithme pour ré-chiffrer les valeurs. Pendant ce temps, aucune autre opération [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ne peut être effectuée sur le serveur. Ainsi, pour permettre aux opérations [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] de continuer de façon ininterrompue, l’algorithme de chiffrement est une valeur en lecture seule dans la boîte de dialogue dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
 Pour modifier le paramètre de la propriété **Algorithme de chiffrement** , définissez la base de données **SSISDB** en mode mono-utilisateur, puis appelez la procédure stockée catalog.configure_catalog. Utilisez ENCRYPTION_ALGORITHM pour l’argument *property_name*. Pour connaître les valeurs de propriétés prises en charge, consultez [catalog.catalog_properties &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md). Pour plus d’informations sur la procédure stockée, consultez [catalog.configure_catalog &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database.md).  
  
 Pour plus d’informations sur le mode mono-utilisateur, consultez [Définir une base de données en mode mono-utilisateur](../../relational-databases/databases/set-a-database-to-single-user-mode.md). Pour plus d’informations sur le chiffrement et les algorithmes de chiffrement dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez les rubriques de la section [Chiffrement SQL Server](../../relational-databases/security/encryption/sql-server-encryption.md).  
  
 Une clé principale de base de données est utilisée pour le chiffrement. La clé est générée lorsque vous créez le catalogue. Pour plus d’informations, consultez [Créer le catalogue SSIS](../../integration-services/service/create-the-ssis-catalog.md).  
  
 Le tableau suivant répertorie les noms des propriétés apparaissant dans la boîte de dialogue **Propriétés du catalogue** et les propriétés correspondantes en vue de base de données.  
  
|Nom de la propriété (boîte de dialogue**Propriétés du catalogue** )|Nom de la propriété (vue de base de données)|  
|---------------------------------------------------------|-------------------------------------|  
|Nom de l'algorithme de chiffrement|ENCRYPTION_ALGORITHM|  
|Nettoyer les journaux régulièrement|OPERATION_CLEANUP_ENABLED|  
|Période de rétention (jours)|RETENTION_WINDOW|  
|Supprimer régulièrement les anciennes versions|VERSION_CLEANUP_ENABLED|  
|Nombre maximal de versions par projet|MAX_PROJECT_VERSIONS|  
|Niveau d'enregistrement par défaut au niveau du serveur|SERVER_LOGGING_LEVEL|  
  
##  <a name="a-namepermissionsa-permissions"></a><a name="Permissions"></a> Autorisations  
 Les projets, les environnements et les packages sont contenus dans des dossiers qui sont des objets sécurisables. Vous pouvez accorder des autorisations à un dossier, notamment l'autorisation de MANAGE_OBJECT_PERMISSIONS. MANAGE_OBJECT_PERMISSIONS vous permet de déléguer l'administration du contenu du dossier à un utilisateur sans avoir à accorder à celui-ci l'appartenance au rôle ssis_admin. Vous pouvez également accorder des autorisations relatives à des projets, des environnements et des opérations. Les opérations incluent l'initialisation de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], le déploiement de projets, la création et le démarrage d'exécutions, la validation de projets et de packages, ainsi que la configuration du catalogue **SSISDB** .  
  
 Pour plus d’informations sur les rôles de base de données, consultez [Rôles au niveau de la base de données](../../relational-databases/security/authentication-access/database-level-roles.md).  
  
 Le catalogue SSISDB utilise un déclencheur DDL, ddl_cleanup_object_permissions, pour appliquer l'intégrité des informations d'autorisations sur les éléments sécurisables SSIS. Le déclencheur est activé lorsqu'un principal de base de données, tel qu'un utilisateur de base de données, un rôle de base de données ou un rôle d'application de base de données, est supprimé de la base de données SSISDB.  
  
 Si le principal a accordé ou refusé des autorisations à d'autres principaux, révoquez les autorisations données par le fournisseur d'autorisations, avant que le principal puisse être supprimé. Sinon, un message d'erreur est retourné lorsque le système essaie de supprimer le principal. Le déclencheur supprime tous les enregistrements d'autorisation dans lesquels le principal de la base de données est un bénéficiaire.  
  
 Il est recommandé de ne pas désactiver le déclencheur car il garantit qu'il n'existe aucun enregistrement d'autorisation orphelin après la suppression d'un principal de la base de données **SSISDB** .  
  
### <a name="managing-permissions"></a>Gestion des autorisations  
 Vous pouvez gérer les autorisations à l’aide de l’interface utilisateur de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , des procédures stockées et de l’espace de noms <xref:Microsoft.SqlServer.Management.IntegrationServices> .  
  
 Pour gérer les autorisations à l'aide de l'interface utilisateur de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , servez-vous des boîtes de dialogue suivantes.  
  
-   Dans le cas d'un dossier, utilisez la page **Autorisations** de la [Folder Properties Dialog Box](../../integration-services/service/folder-properties-dialog-box.md).  
  
-   Dans le cas d'un projet, utilisez la page **Autorisations** de la [Project Properties Dialog Box](../../integration-services/service/project-properties-dialog-box.md).  
  
-   Pour un environnement, utilisez la page **Autorisations** page de la [boîte de dialogue NIB : Propriétés d’environnement](http://msdn.microsoft.com/fr-fr/6a91a8d4-0006-4cfd-9759-3e4295ae452b).  
  
 Pour gérer les autorisations à l’aide de Transact-SQL, appelez [catalog.grant_permission &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-grant-permission-ssisdb-database.md), [catalog.deny_permission &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-deny-permission-ssisdb-database.md) et [catalog.revoke_permission &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-revoke-permission-ssisdb-database.md). Pour afficher les autorisations effectives pour le principal actuel pour tous les objets, interrogez [catalog.effective_object_permissions &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-effective-object-permissions-ssisdb-database.md). Cette rubrique fournit les descriptions des différents types d'autorisations. Pour afficher les autorisations affectées explicitement à l’utilisateur, interrogez [catalog.explicit_object_permissions &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-explicit-object-permissions-ssisdb-database.md).  
  
##  <a name="a-namefoldersa-folders"></a><a name="Folders"></a> Dossiers  
 Un dossier contient un ou plusieurs projets et environnements du catalogue **SSISDB** . Vous pouvez utiliser la vue [catalog.folders &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-folders-ssisdb-database.md) pour accéder aux informations relatives aux dossiers du catalogue. Vous pouvez utiliser les procédures stockées suivantes pour gérer des dossiers.  
  
-   [catalog.create_folder &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-create-folder-ssisdb-database.md)  
  
-   [catalog.delete_folder &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-delete-folder-ssisdb-database.md)  
  
-   [catalog.rename_folder &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-rename-folder-ssisdb-database.md)  
  
-   [catalog.set_folder_description &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-folder-description-ssisdb-database.md)  
  
##  <a name="a-nameprojectsandpackagesa-projects-and-packages"></a><a name="ProjectsAndPackages"></a> Projets et packages  
 Chaque projet peut contenir plusieurs packages. Les projets et les packages peuvent contenir des paramètres et des références aux environnements. Vous pouvez accéder aux paramètres et aux références d'environnement à l'aide de la [Configure Dialog Box](../../integration-services/service/configure-dialog-box.md).  
  
 Vous pouvez effectuer d'autres tâches de projet en appelant les procédures stockées suivantes.  
  
-   [catalog.delete_project &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-delete-project-ssisdb-database.md)  
  
-   [catalog.deploy_project &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-deploy-project-ssisdb-database.md)  
  
-   [catalog.get_project &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-get-project-ssisdb-database.md)  
  
-   [catalog.move_project &#40;&#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-move-project-ssisdb-database.md)  
  
-   [catalog.restore_project &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database.md)  
  
 Ces vues fournissent des détails sur les packages, les projets et les versions des projets.  
  
-   [catalog.projects &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-projects-ssisdb-database.md)  
  
-   [catalog.packages &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-packages-ssisdb-database.md)  
  
-   [catalog.object_versions &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-object-versions-ssisdb-database.md)  
  
##  <a name="a-nameparametersa-parameters"></a><a name="Parameters"></a> Paramètres  
 Vous utilisez des paramètres pour affecter des valeurs aux propriétés des packages au moment de l'exécution de ces packages. Pour définir la valeur d’un package ou d’un paramètres de projet et pour effacer la valeur, appelez [catalog.set_object_parameter_value &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database.md) et [catalog.clear_object_parameter_value &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database.md). Pour définir la valeur d’un paramètre pour une instance d’exécution, appelez [catalog.set_execution_parameter_value &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md). Vous pouvez récupérer les valeurs des paramètres par défaut en appelant [catalog.get_parameter_values &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-get-parameter-values-ssisdb-database.md).  
  
 Ces vues affichent les paramètres de tous les packages et projets, ainsi que les valeurs de paramètre utilisées pour une instance d'exécution.  
  
-   [catalog.object_parameters &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-object-parameters-ssisdb-database.md)  
  
-   [catalog.execution_parameter_values &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)  
  
##  <a name="a-nameserverenvironmentsa-server-environments-server-variables-and-server-environment-references"></a><a name="ServerEnvironments"></a> Environnements serveur, variables de serveur et références d’environnement serveur  
 Les environnements serveur contiennent des variables de serveur. Les valeurs des variables peuvent être utilisées lorsqu'un package est exécuté ou validé sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Les procédures stockées suivantes vous permettent d'exécuter de nombreuses autres tâches de gestion sur les environnements et les variables.  
  
-   [catalog.create_environment &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-ssisdb-database.md)  
  
-   [catalog.delete_environment &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-ssisdb-database.md)  
  
-   [catalog.move_environment &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-move-environment-ssisdb-database.md)  
  
-   [catalog.rename_environment &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-rename-environment-ssisdb-database.md)  
  
-   [catalog.set_environment_property &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-property-ssisdb-database.md)  
  
-   [catalog.create_environment_variable &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-variable-ssisdb-database.md)  
  
-   [catalog.delete_environment_variable &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-variable-ssisdb-database.md)  
  
-   [catalog.set_environment_variable_property &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-property-ssisdb-database.md)  
  
-   [catalog.set_environment_variable_value &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-value-ssisdb-database.md)  
  
 En appelant la procédure stockée [catalog.set_environment_variable_protection &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-variable-protection-ssisdb-database.md), vous pouvez définir le bit de sensibilité d’une variable.  
  
 Pour utiliser la valeur d'une variable de serveur, spécifiez la référence entre le projet et l'environnement serveur. Vous pouvez utiliser les procédures stockées suivantes pour créer et supprimer des références. Vous pouvez également indiquer si l'environnement peut se trouver dans le même dossier que le projet ou dans un dossier différent.  
  
-   [catalog.create_environment_reference &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-create-environment-reference-ssisdb-database.md)  
  
-   [catalog.delete_environment_reference &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-delete-environment-reference-ssisdb-database.md)  
  
-   [catalog.set_environment_reference_type &#40;Base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-environment-reference-type-ssisdb-database.md)  
  
 Pour plus de détails sur les environnements et les variables, interrogez ces vues.  
  
-   [catalog.environments &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-environments-ssisdb-database.md)  
  
-   [catalog.environment_variables &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-environment-variables-ssisdb-database.md)  
  
-   [catalog.environment_references &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-environment-references-ssisdb-database.md)  
  
##  <a name="a-nameexecutionsa-executions-and-validations"></a><a name="Executions"></a> Exécutions et validations  
 Une exécution est une instance d'une exécution de package. Appelez [catalog.create_execution &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md) et [catalog.start_execution &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md) pour créer et démarrer une exécution. Pour arrêter une exécution ou une validation de package/projet, appelez [catalog.stop_operation &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database.md).  
  
 Pour suspendre un package en cours d'exécution et créer un fichier de vidage, appelez la procédure stockée catalog.create_execution_dump. Le fichier de vidage fournit des informations sur l'exécution d'un package, ce qui peut vous aider à résoudre les problèmes d'exécution. Pour plus d'informations sur la génération et la configuration de fichiers de vidage, consultez [Generating Dump Files for Package Execution](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md).  
  
 Pour plus de détails sur les exécutions, les validations et les messages enregistrés pendant les opérations, ainsi que pour obtenir des informations contextuelles sur les erreurs, interrogez ces vues.  
  
-   [catalog.executions &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md)  
  
-   [catalog.operations &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)  
  
-   [catalog.operation_messages &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-operation-messages-ssisdb-database.md)  
  
-   [catalog.extended_operation_info &#40;Base de données SSISDB&#41;](../../integration-services/system-views/catalog-extended-operation-info-ssisdb-database.md)  
  
-   [catalog.event_messages](../../integration-services/system-views/catalog-event-messages.md)  
  
-   [catalog.event_message_context](../../integration-services/system-views/catalog-event-message-context.md)  
  
 Vous pouvez valider des projets et des packages en appelant les procédures stockées [catalog.validate_project &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-validate-project-ssisdb-database.md) et [catalog.validate_package &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-validate-package-ssisdb-database.md). La vue [catalog.validations &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-validations-ssisdb-database.md) fournit des informations sur les validations, telles que les références d’environnement serveur prises en compte dans la validation, s’il s’agit d’une validation de dépendance ou d’une validation complète, et si le runtime 32 bits ou 64 bits est utilisé pour exécuter le package.  
  
##  <a name="a-namealwaysona-alwayson-support"></a><a name="AlwaysOn"></a>Prise en charge d’AlwaysOn  
 La fonctionnalité de groupes de disponibilité AlwaysOn est une solution de haute disponibilité et de récupération d’urgence qui fournit une alternative au niveau de l’entreprise à la mise en miroir de bases de données. Un groupe de disponibilité prend en charge un environnement de basculement pour un ensemble discret de bases de données utilisateur, appelées bases de données de disponibilité, qui basculent de concert. Pour plus d’informations, veuillez consulter [Groupes de disponibilité AlwaysOn (SQL Server)](https://msdn.microsoft.com/library/hh510230.aspx).  
  
 Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], SQL Server Integration Services (SSIS) introduit de nouvelles fonctionnalités qui vous permettent d’effectuer facilement un déploiement vers un catalogue SSIS centralisé (par exemple une base de données utilisateur SSISDB). Pour assurer la haute disponibilité de la base de données SSISDB et de son contenu (projets, packages, journaux d’exécution, etc.), vous pouvez ajouter la base de données SSISDB (identique à toute autre base de données utilisateur) à un groupe de disponibilité AlwaysOn. Quand un basculement se produit, le nœud secondaire devient automatiquement le nouveau nœud primaire.  
  
 Pour obtenir une présentation détaillée et des instructions pas à pas concernant l’activation de la fonctionnalité AlwaysOn pour SSISDB, consultez [AlwaysOn pour le catalogue SSIS &#40;SSISDB&#41;](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md).  
  
##  <a name="a-namerelatedtasksa-related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Créer le catalogue SSIS](../../integration-services/service/create-the-ssis-catalog.md)  
  
-   [Sauvegarder, restaurer et déplacer le catalogue SSIS](../../integration-services/service/backup-restore-and-move-the-ssis-catalog.md)  
  
##  <a name="a-namerelatedcontenta-related-content"></a><a name="RelatedContent"></a> Contenu connexe  
  
-   Entrée de blog, [SSIS and PowerShell in SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=242539), sur blogs.msdn.com.  
  
-   Entrée de blog [Conseils pour le contrôle d'accès du catalogue SSIS](http://go.microsoft.com/fwlink/?LinkId=246669), sur blogs.msdn.com.  
  
-   Entrée de blog, [A Glimpse of the SSIS Catalog Managed Object Model](http://go.microsoft.com/fwlink/?LinkId=254267), sur blogs.msdn.com.  
  
  