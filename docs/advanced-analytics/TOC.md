# Vue d'ensemble

## [Qu’est-ce que SQL Server Machine Learning Services ?](what-is-sql-server-machine-learning.md)
### [Analytique dans la base de données](r/sql-server-r-services.md)
### [Serveur autonome](r/r-server-standalone.md)
## [Nouvelles fonctionnalités](what-s-new-in-sql-server-machine-learning-services.md)
## [Fonctionnalités par édition](r/differences-in-r-features-between-editions-of-sql-server.md)

# [Architecture](architecture-overview-machine-learning.md)
## [R](r/architecture-overview-sql-server-r.md)
### [Interopérabilité de R](r/r-interoperability-in-sql-server.md)
### [Composants prenant en charge l’intégration de R](r/new-components-in-sql-server-to-support-r.md)
### [Sécurité pour R](r/security-overview-sql-server-r.md)
## [Python](python/architecture-overview-sql-server-python.md)
### [Python dans Machine Learning Services](python/sql-server-python-services.md)
### [Interopérabilité de Python](python/python-interoperability.md)
### [Composants pour la prise en charge de Python](python/new-components-in-sql-server-to-support-python-integration.md)
### [Sécurité de Python](python/security-overview-sql-server-python-services.md)
<!-- ### [How To Create a Resource Pool for Python](python/how-to-create-a-resource-pool-for-python.md)-->
<!-- ### [Extended Events for Python](python/extended-events-for-python.md)-->
<!-- ### [DMVs for Python](python/dmvs-for-python.md)-->
<!-- ### [Resource Governance for Python](python/resource-governance-for-python.md)-->

# Install 

## SQL Server 2017
### [Analytique dans la base de données](install/sql-machine-learning-services-windows-install.md)
### [Serveur autonome](install/sql-machine-learning-standalone-windows-install.md)
## SQL Server 2016
### [R Services (dans la base de données)](install/sql-r-services-windows-install.md)
### [R Server (autonome)](install/sql-r-standalone-windows-install.md)
## [Modèles dont l’apprentissage a déjà été effectué](install/sql-pretrained-models-install.md)
## [Configuration de l’invite de commandes](install/sql-ml-component-commandline-install.md)
## [Configuration en mode hors connexion (sans Internet)](install/sql-ml-component-install-without-internet-access.md)
## [Mise à niveau de R et Python](r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)
## [Configurer les outils R](r/set-up-a-data-science-client.md)
## [Configurer les outils Python](python/setup-python-client-tools-sql.md)

# Démarrages rapides

## R
### [Hello World dans R et SQL](tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
### [Gérer les entrées et les sorties](tutorials/rtsql-working-with-inputs-and-outputs.md)
### [Gérer des types de données et des objets](tutorials/rtsql-r-and-sql-data-types-and-data-objects.md)
### [Créer un modèle prédictif](tutorials/rtsql-create-a-predictive-model-r.md)
### [Prédire et tracer à partir du modèle](tutorials/rtsql-predict-and-plot-from-model.md)

# [Didacticiels](tutorials/machine-learning-services-tutorials.md)
## [R](tutorials/sql-server-r-tutorials.md)
### [Découvrir l’analytique dans la base de données](tutorials/sqldev-in-database-r-for-sql-developers.md)
#### [1 - Obtenir les données et les scripts](tutorials/sqldev-download-the-sample-data.md)
#### [2 - Configurer l’environnement](r/sqldev-import-data-to-sql-server-using-powershell.md)
#### [3 - Visualiser les données](tutorials/sqldev-explore-and-visualize-the-data.md)
#### [4 - Créer des caractéristiques de données](tutorials/sqldev-create-data-features-using-t-sql.md)
#### [5 - Entraîner et enregistrer dans SQL](r/sqldev-train-and-save-a-model-using-t-sql.md)
#### [6 - Prédire les résultats](tutorials/sqldev-operationalize-the-model.md)

### [Procédure pas à pas pour une solution complète de science des données](tutorials/walkthrough-data-science-end-to-end-walkthrough.md)
#### [Préparer les données](tutorials/walkthrough-prepare-the-data.md)
#### [Explorer les données à l’aide de SQL](tutorials/walkthrough-view-and-explore-the-data.md)
#### [Résumer les données à l’aide de R](tutorials/walkthrough-view-and-summarize-data-using-r.md)
#### [Créer des graphes et des tracés](tutorials/walkthrough-create-graphs-and-plots-using-r.md)
#### [Créer des caractéristiques de données](tutorials/walkthrough-create-data-features.md)
#### [Créer et enregistrer le modèle](tutorials/walkthrough-build-and-save-the-model.md)
#### [Déployer et utiliser le modèle](tutorials/walkthrough-deploy-and-use-the-model.md)

### [Immersion avec RevoScaleR](tutorials/deepdive-data-science-deep-dive-using-the-revoscaler-packages.md)
#### [Créer une base de données et des autorisations](tutorials/deepdive-work-with-sql-server-data-using-r.md)
#### [Créer des objets de données à l’aide de RxSqlServerData](tutorials/deepdive-create-sql-server-data-objects-using-rxsqlserverdata.md)
#### [Interroger et modifier des données](tutorials/deepdive-query-and-modify-the-sql-server-data.md)
#### [Définir un contexte de calcul](tutorials/deepdive-define-and-use-compute-contexts.md)
#### [Créer et exécuter des scripts R](tutorials/deepdive-create-and-run-r-scripts.md)
#### [Visualiser les données](tutorials/deepdive-visualize-sql-server-data-using-r.md)
#### [Créer des modèles](tutorials/deepdive-create-models.md)
#### [Affecter un score à de nouvelles données](tutorials/deepdive-score-new-data.md)
#### [Transformer des données](tutorials/deepdive-transform-data-using-r.md)
#### [Charger des données en mémoire à l’aide de rxImport](tutorials/deepdive-load-data-into-memory-using-rximport.md)
#### [Créer une table avec rxDataStep](tutorials/deepdive-create-new-sql-server-table-using-rxdatastep.md)
#### [Effectuer une analyse de segmentation à l’aide de rxDataStep](tutorials/deepdive-perform-chunking-analysis-using-rxdatastep.md)
#### [Analyser des données dans un contexte de calcul local](tutorials/deepdive-analyze-data-in-local-compute-context.md)
#### [Déplacer des données entre SQL Server et un fichier XDF](tutorials/deepdive-move-data-between-sql-server-and-xdf-file.md)
#### [Créer une simulation simple](tutorials/deepdive-create-a-simple-simulation.md)

## [Python](tutorials/sql-server-python-tutorials.md)
### [Exécuter Python avec T-SQL](tutorials/run-python-using-t-sql.md)
#### [Empaqueter Python dans une procédure stockée](tutorials/wrap-python-in-tsql-stored-procedure.md)
#### [Formation et score à partir d’un modèle Python dans SQL Server](tutorials/train-score-using-python-in-tsql.md)
#### [Créer un modèle à l’aide de revoscalepy dans un contexte de calcul SQL Server](tutorials/use-python-revoscalepy-to-create-model.md)
### [Découvrir l’analytique dans la base de données](tutorials/sqldev-in-database-python-for-sql-developers.md)
#### [Obtenir les données et les scripts](tutorials/sqldev-py1-download-the-sample-data.md)
#### [Importer des données](tutorials/sqldev-py2-import-data-to-sql-server-using-powershell.md)
#### [Explorer et visualiser des données](tutorials/sqldev-py3-explore-and-visualize-the-data.md)
#### [Créer des caractéristiques de données](tutorials/sqldev-py4-create-data-features-using-t-sql.md)
#### [Entraîner et enregistrer le modèle](tutorials/sqldev-py5-train-and-save-a-model-using-t-sql.md)
#### [Rendre le modèle opérationnel](tutorials/sqldev-py6-operationalize-the-model.md)

# [Exemples](https://github.com/Microsoft/sql-server-samples)

# [Solutions](tutorials/data-science-scenarios-and-solution-templates.md)

# [Procédure](r/sql-server-machine-learning-tasks.md)

## Gestion des packages
### [Packages par défaut](r/installing-and-managing-r-packages.md)
### [Obtenir les informations sur le package](r/determine-which-packages-are-installed-on-sql-server.md)
### [Installer de nouveaux packages Python](python/install-additional-python-packages-on-sql-server.md)
### [Installer de nouveaux packages R](r/install-additional-r-packages-on-sql-server.md)
#### [Utiliser des gestionnaires de package R](r/use-r-package-managers-on-sql-server.md)
#### [Utiliser T-SQL](r/install-r-packages-tsql.md)
#### [Utiliser RevoScaleR](r/use-revoscaler-to-manage-r-packages.md)
##### [Activer la gestion de packages R à distance](r/r-package-how-to-enable-or-disable.md)
##### [Synchroniser des packages R](r/package-install-uninstall-and-sync.md)
#### [Créer un dépôt miniCRAN](r/create-a-local-package-repository-using-minicran.md)
#### [Conseils pour l’utilisation de packages R](r/packages-installed-in-user-libraries.md)

## Exploration et modélisation des données
### [Bibliothèques et types de données R](r/r-libraries-and-data-types.md)
### [Bibliothèques et types de données Python](python/python-libraries-and-data-types.md)
### [Calcul de score en natif](sql-native-scoring.md)
### [Calcul de score en temps réel](real-time-scoring.md)
### [Modélisation prédictive avec R](r/data-exploration-and-predictive-modeling-with-r.md)
### [Guide pratique pour effectuer le calcul de score en temps réel ou en natif](r/how-to-do-realtime-scoring.md)
### [Charger des objets R à l’aide d’ODBC](r/save-and-load-r-objects-from-sql-server-using-odbc.md)
### [Conversion du code R pour une utilisation dans Machine Learning Services](r/converting-r-code-for-use-in-sql-server.md)
### [Création de plusieurs modèles à l’aide de rxExecBy](r/creating-multiple-models-using-rxexecby.md)
### [Utilisation de données de cubes OLAP dans R](r/using-data-from-olap-cubes-in-r.md)
### [Créer une procédure stockée à l’aide de sqlrutils](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## Performances
### [Optimisation des performances pour R - Vue d’ensemble](r/sql-server-r-services-performance-tuning.md)
### [Optimisation des performances pour R - Configuration de SQL Server](r/sql-server-configuration-r-services.md)
### [Optimisation des performances pour R - R et optimisation des données](r/r-and-data-optimization-r-services.md)
### [Optimisation des performances pour R - Résultats](r/performance-case-study-r-services.md)
### [Utiliser les fonctions de profilage de code R](r/using-r-code-profiling-functions.md)

## Administration
### [Configurer et gérer R](r/configuration-sql-server-r-services.md)
### [Options de configuration avancées pour Machine Learning Services](r/configure-and-manage-advanced-analytics-extensions.md)
### [Considérations sur la sécurité pour le runtime R dans SQL Server](r/security-considerations-for-the-r-runtime-in-sql-server.md)
### [Modifier le pool de comptes d’utilisateur pour SQL Server Machine Learning Services](r/modify-the-user-account-pool-for-sql-server-r-services.md)
### [Ajouter SQLRUserGroup comme utilisateur de base de données](r/add-sqlrusergroup-to-database.md)
### [Déployer et utiliser des modèles à l’aide de services web](operationalization-with-mrsdeploy.md)
### [Gérer et surveiller des solutions](r/managing-and-monitoring-r-solutions.md)
### [Gouvernance des ressources pour Machine Learning Services](r/resource-governance-for-r-services.md)
### [Créer un pool de ressources pour Machine Learning](r/how-to-create-a-resource-pool-for-r.md)
### [Événements étendus pour Machine Learning Services](r/extended-events-for-sql-server-r-services.md)
### [Événements étendus pour la surveillance d’instructions PREDICT](xe-event-predict-tsql.md)
### [DMV pour Machine Learning Services](r/dmvs-for-sql-server-r-services.md)
### [Utilisation des fonctions de profilage de code R](r/using-r-code-profiling-functions.md)
### [Surveiller Machine Learning Services à l’aide de rapports personnalisés dans Management Studio](r/monitor-r-services-using-custom-reports-in-management-studio.md)

# [Informations de référence sur les packages](r/machine-learning-services-r-reference.md)

## [MicrosoftML dans SQL](using-the-microsoftml-package.md)
## [RevoScaleR dans SQL](r/revoscaler-overview.md)
## [Liste de fonctions RevoScaleR pour les données SQL Server](r/scaler-functions-for-working-with-sql-server-data.md)
## [sqlrutils dans SQL](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
## [olapR dans SQL](r/how-to-create-mdx-queries-using-olapr.md)
## [revoscalepy dans SQL](python/what-is-revoscalepy.md)

# Ressources

## [Problèmes connus](known-issues-for-sql-server-machine-learning-services.md)
## [Notes de publication](https://docs.microsoft.com/sql/sql-server/sql-server-2017-release-notes)
## [Configurer une machine virtuelle](r/installing-sql-server-r-services-on-an-azure-virtual-machine.md)
## [Dépannage](machine-learning-troubleshooting-faq.md)
### [Collecte de données](data-collection-ml-troubleshooting-process.md)
### [Erreurs d’installation et de mise à niveau](r/upgrade-and-installation-faq-sql-server-r-services.md)
### [Erreurs de Launchpad et d’exécution de script externe](common-issues-external-script-execution.md)
### [Erreurs de scripts R](r-script-execution-errors.md)

## Blogs
### [SQL Server](https://blogs.technet.microsoft.com/dataplatforminsider/)
### [R Server](https://blogs.msdn.microsoft.com/microsoftrservertigerteam/)
### [Machine Learning](https://blogs.technet.microsoft.com/machinelearning/)

## Forums
### [SQL Server](https://social.msdn.microsoft.com/Forums/sqlserver/home?category=sqlserver)
### [Machine Learning Server](https://social.msdn.microsoft.com/Forums/home?forum=MicrosoftR)
