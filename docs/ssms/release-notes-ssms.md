---
title: Notes de publication de SQL Server Management Studio (SSMS) | Microsoft Docs
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
author: markingmyname
ms.author: maghan
manager: craigg
ms.custom: ''
ms.date: 06/12/2019
ms.openlocfilehash: 74ec0cd11e1c13363905c71a64096f6c4eb8b053
ms.sourcegitcommit: a6949111461eda0cc9a71689f86b517de3c5d4c1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263538"
---
# <a name="release-notes-for-sql-server-management-studio-ssms"></a>Notes de publication de SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Cet article fournit des détails sur les mises à jour, les améliorations et les correctifs de bogues des versions actuelles et précédentes de SSMS.

<!--
The latest ## H2 section of this Release Notes article has been reformatted to match the new standard.
The new standard replaces the use of bullet lists with the 2-column markdown table format.
Please use the new 2-column table format going forward.
And please do include the final blank row of "| &nbsp;| &nbsp;|".

The ## H2 titles are also being shortened, by the removal of unnecessary repetitive strings.
In this case, "## SSMS 17.9" is being shortened to "## 17.9" (as one standard actual example).
And we are appending the 'Month yyyy'.

Also, this file has been renamed to the new standard, which calls for the file name to be with "release-notes-[techAreaName].md".
The old name for this file was 'sql-server-management-studio-changelog-ssms.md'.
But today the new file name is 'release-notes-ssms.md' (still in 'docs/ssms/').

Thank you.
GeneMi. 2019/04/02.
-->

## <a name="ssms-181"></a>SSMS 18.1

Télécharger : &nbsp; &nbsp; [Télécharger SSMS 18.1](download-sql-server-management-studio-ssms.md)<br/>
Numéro de build : &nbsp; &nbsp; 15.0.18131.0<br/>
Date de publication : &nbsp; &nbsp; 11 juin 2019

SSMS 18.1 est la dernière version en disponibilité générale (GA) de SSMS. Si vous avez besoin d’une version précédente de SSMS, consultez les [versions précédentes de SSMS](release-notes-ssms.md#previous-ssms-releases).

18.1 est une petite mise à jour de la version 18.0 qui introduit les nouveaux éléments et correctifs suivants.

## <a name="whats-new-in-181"></a>Nouveautés de la version 18.1

| Nouvel élément| Détails|
| :-------| :------|
| Diagrammes de base de données | Les diagrammes de base de données ont été rajoutés à SSMS. Pour plus d’informations, consultez [Diagrammes de base de données](https://feedback.azure.com/forums/908035/suggestions/37507828). |
| SSBDIAGNOSE.EXE |L’outil de ligne de commande SQL Server Diagnose a été rajouté au package SSMS.|
| Integration Services (SSIS) | Prise en charge de la planification du package SSIS, situé dans le catalogue SSIS dans Azure ou le système de fichiers, dans Azure. Il existe trois entrées pour le lancement de la boîte de dialogue Nouvelle planification, l’élément de menu *Nouvelle planification...* affiché lors d’un clic droit sur la package SSIS dans le catalogue SSIS au sein d’Azure, l’élément de menu *Planifier un package SSIS dans Azure* sous l’élément de menu *Migrer vers Azure* sous l’élément de menu *Outils* et « Planifier SSIS dans Azure » affiché lors d’un clic droit sur le dossier Travaux sous l’agent SQL Server de Azure SQL Database Managed Instance.|

## <a name="bug-fixes-in-181"></a>Correctifs de bogues dans la version 18.1

| Nouvel élément | Détail |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Accessibilité | Amélioration de l’accessibilité de l’interface utilisateur du travail d’agent. |
| Accessibilité | Amélioration de l’accessibilité dans la page du moniteur Stretch : ajout d’un nom accessible pour le bouton *Actualisation automatique* et d’un nom accessible intelligent qui permet aux utilisateurs de savoir sur quel bouton ils se trouvent et ce qui va arriver s’ils appuient sur ce bouton. |
| Intégration d’ADS| Correction d’un plantage possible dans SSMS lors d’une tentative d’utilisation des serveurs inscrits à ADS.|
| Concepteur de bases de données | Ajout de la prise en charge du classement Latin1_General_100_BIN2_UTF8 (disponible dans SQL Server 2019 CTP3.0). |
| Classification des données | Interdiction d’ajouter des étiquettes de sensibilité aux colonnes dans la table d’historique, ce qui n’est pas pris en charge. |
| Classification des données | Résolution d’un problème lié à la gestion incorrecte du niveau de compatibilité (serveur/base de données). |
| Concepteur de bases de données | Ajout de la prise en charge du classement Latin1_General_100_BIN2_UTF8 (disponible dans SQL2019 CTP3.0). |
| SSMS général | Correction d’un problème entraînant la génération d’un script incorrect des colonnes pseudo dans un index. |
| SSMS général | Correction d’un problème entraînant la levée d’une exception de référence null en cas de clic sur le bouton *Ajouter des informations d’identification* dans la page des propriétés de connexion. |
| SSMS général | Correction de l’affichage de la taille de la colonne Money dans la page des propriétés de l’index. |
| SSMS général | Correction d’un problème lié au fait que SSMS ne respectait pas les paramètres Intellisense provenant d’*Outils/Options* dans la fenêtre de l’éditeur SQL. |
| SSMS général | Correction d’un problème lié au fait que SSMS ne respectait pas les paramètres d’aide (en ligne/hors connexion). |
| Haute résolution | Correction de la disposition des contrôles dans les boîtes de dialogue d’erreur pour les options de requête non prises en charge. |
| Haute résolution | Correction de la disposition des contrôles dans la page *Nouveau groupe de disponibilité* sur certaines versions localisées de SSMS. |
| Haute résolution | Correction de la disposition de la page *Nouvelle planification du travail*. Pour plus d’informations, consultez le [forum de commentaires](https://feedback.azure.com/forums/908035/suggestions/37632094). |
| Importer un fichier plat | Correction d’un problème pouvant entraîner la perte silencieuse de lignes durant l’importation.|
| IntelliSense/éditeur | Réduction du trafic de requêtes basées sur SMO vers les bases de données Azure SQL pour IntelliSense. |
| IntelliSense/éditeur | Correction d’une erreur grammaticale dans l’info-bulle affichée lors de la saisie de T-SQL pour créer un utilisateur. Correction également du message d’erreur pour lever l’ambiguïté entre les utilisateurs et les connexions. |
| Visionneuse du journal | Correction d’un problème lié au fait que SSMS ouvre toujours le journal du serveur (ou de l’agent) actuel, même en cas de double-clic sur un ancien journal d’archivage dans l’explorateur d’objets. Pour plus d’informations, consultez le [forum de commentaires](https://feedback.azure.com/forums/908035/suggestions/37633648). |
| Installation de SSMS | Résolution du problème provoquant l’échec de l’installation de SSMS quand le chemin du journal d’installation contient des espaces. Pour plus d’informations, consultez le [forum de commentaires](https://feedback.azure.com/forums/908035/suggestions/37496110). |
| Installation de SSMS | Correction d’un problème provoquant la fermeture de SSMS juste après l’affichage de l’écran de démarrage. </br> Pour plus d’informations, consultez ces sites : [forum de commentaires](https://feedback.azure.com/forums/908035/suggestions/37502512), [SSMS refuse de démarrer](https://dba.stackexchange.com/questions/238609/ssms-refuses-to-start) et [Administrateurs de base de données](https://dba.stackexchange.com/questions/237086/sql-server-management-studio-18-wont-open-only-splash-screen-pops-up). |
| Explorateur d’objets | Levée de la restriction sur l’activation de *start PowerShell* en cas de connexion à SQL sur Linux. |
| Explorateur d’objets | Correction d’un problème entraînant le plantage de SSMS lors d’une tentative d’extension du nœud du groupe Polybase/Groupe de scale-out (en cas de connexion à un nœud de calcul). |
| Explorateur d’objets | Correction d’un problème lié au fait que l’élément de menu *désactivé* était toujours activé, même après la désactivation d’un index donné. Pour plus d’informations, consultez le [forum de commentaires](https://feedback.azure.com/forums/908035/suggestions/37735375). |
| Rapports | Correction du rapport pour afficher GrantedQueryMemory dans la base de connaissances (rapport de tableau de bord des performances SQL). Pour plus d’informations, consultez le [forum de commentaires](https://feedback.azure.com/forums/908035/suggestions/37167289). |
| Rapports | Amélioration du suivi du bloc de journal dans les scénarios Always-On. |
| ShowPlan | Ajout d’un nouvel élément du plan d’exécution de requêtes *SpillOccurred* au schéma du plan d’exécution de requêtes. |
| ShowPlan | Ajout de lectures à distance (*ActualPageServerReads*, *ActualPageServerReadAheads*, *ActualLobPageServerReads*, *ActualLobPageServerReadAheads* ) au schéma du plan d’exécution. |
| SMO/création de scripts | Évitez d’interroger les contraintes d’arête durant la création de scripts pour les tables non graphiques. |
| SMO/création de scripts | Suppression de la contrainte sur la classification de sensibilité lors de la création de scripts de colonnes avec la *classification des données*. |
| SMO/création de scripts | Correction d’un problème entraînant l’échec de « Générer un script » sur une table de graphe durant la génération de données. Pour plus d’informations, consultez le [forum de commentaires](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898466). |
| SMO/création de scripts | Correction d’un problème empêchant à la méthode EnumObjects() de récupérer le nom de schéma d’un synonyme. |
| SMO/création de scripts | Correction d’un problème dans UIConnectionInfo.LoadFromStream() empêchant la lecture de la section *AdvancedOptions* (quand un mot de passe n’est pas spécifié). |
| Agent SQL | Correction d’un problème provoquant le plantage de SSMS lors de l’utilisation de la fenêtre de propriétés d’un travail. Pour plus d’informations, consultez le [forum de commentaires](https://feedback.azure.com/forums/908035/suggestions/37164244). |
| Agent SQL | Correction d’un problème lié au fait que le bouton « Afficher » situé dans *Propriétés de l’étape du travail* n’était pas toujours activé, ce qui empêchait l’affichage de la sortie d’une étape de travail donnée. |
| Interface utilisateur XEvent | Ajout de la colonne « Package » à la liste XEvents pour distinguer les événements portant le même nom. |
| Interface utilisateur XEvent | Ajout du mappage de type de classe « EXTERNAL LIBRARY » manquant à XEventUI. |

## <a name="previous-ssms-releases"></a>Versions précédentes de SSMS

Téléchargez les versions précédentes de SSMS en cliquant sur le lien des titres dans les sections suivantes :

## <a name="downloadssdtmediadownloadpng-ssms-180httpsgomicrosoftcomfwlinklinkid2088649"></a>![télécharger](../ssdt/media/download.png) [SSMS 18.0](https://go.microsoft.com/fwlink/?linkid=2088649)

- Numéro de version : 18.0<br>
- Numéro de build : 15.0.18118.0<br>
- Date de publication : 24 avril 2019

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x40a)

### <a name="whats-new-in-180"></a>Nouveautés de la version 18.0

| Nouvel élément| Détails|
| :-------| :------|
|Prise en charge de SQL Server 2019|SSMS 18.0 est la première version qui prend entièrement *en charge* SQL Server 2019 (compatLevel 150).|
|Prise en charge de SQL Server 2019|Prise en charge de « BATCH_STARTED_GROUP » et de « BATCH_COMPLETED_GROUP » dans SQL Server 2019 et SQL Database Managed Instance.|
|Prise en charge de SQL Server 2019|SMO : Ajout de la prise en charge pour l’incorporation (inlining) des fonctions UDF.|
|Prise en charge de SQL Server 2019|GraphDB : Ajout d’un indicateur dans le plan d’exécution de requêtes pour Graph TC Sequence.|
|Prise en charge de SQL Server 2019|Always Encrypted : ajout de la prise en charge d’AEv2/des enclaves.|
|Prise en charge de SQL Server 2019|Always Encrypted : la boîte de dialogue Connexion contient un nouvel onglet « Always Encrypted » quand l’utilisateur clique sur le bouton « Options » pour activer/configurer la prise en charge des enclaves.|
|Taille de téléchargement de SSMS inférieure| La taille actuelle est environ 500 Mo, environ la moitié de l’offre groupée SSMS 17.x.
|SSMS est basé sur le shell isolé Visual Studio 2017|Le nouvel interpréteur de commandes (SSMS est basé sur Visual Studio 2017 15.9.11) déverrouille tous les correctifs d’accessibilité qui ont été intégrés à SSMS et Visual Studio, et inclut les derniers correctifs de sécurité.|
|Améliorations apportées à l’accessibilité de SSMS| Un travail important a été réalisé pour faire face aux problèmes d’accessibilité dans tous les outils (SSMS, DTA et Profiler)|
|SSMS peut désormais être installé dans un dossier personnalisé| Cette option est disponible depuis l’interface de ligne de commande (utile pour l’installation sans assistance) et l’interface utilisateur d’installation. En utilisant la ligne de commande, transmettez cet argument supplémentaire à SSMS-Setup-ENU.exe :<br> SSMSInstallRoot=C:\MySSMS18<br> Par défaut, le nouvel emplacement d’installation de SSMS est : %ProgramFiles(x86)%\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe<br>Cela ne signifie pas que SSMS est à instances multiples.|
|SSMS permet l’installation dans une langue autre que celle du système d’exploitation|Le blocage sur l’installation en plusieurs langues a été levé. Vous pouvez, par exemple, installer SSMS en allemand sur un Windows français. Si la langue du système d’exploitation ne correspond pas à la langue de SSMS, l’utilisateur doit modifier la langue sous **Outils** > **Options** > **Paramètres internationaux**, sinon SSMS affiche l’interface utilisateur en anglais.|
|SSMS ne partage plus de composants avec le moteur SQL|Beaucoup d’efforts ont été déployés pour éviter le partage de composants avec le moteur SQL, qui avait souvent pour effet de nuire à la facilité de gestion, compte tenu du fait que l’un écrasait les fichiers installés par l’autre.|
|SSMS nécessite NetFx 4.7.2 ou une version ultérieure|Nous avons mis à niveau notre configuration minimale requise de NetFx4.6.1 à NetFx4.7.2 : cela nous permet de tirer parti des nouvelles fonctionnalités exposées par la nouvelle infrastructure.|
|Possibilité de migrer les paramètres de SSMS| Au premier démarrage de SSMS 18, l’utilisateur est invité à migrer les paramètres de la version 17.x. Les fichiers de paramètres utilisateur sont maintenant stockés comme un fichier XML simple, ce qui améliore la portabilité et permet éventuellement la modification.|
|Prise en charge des résolutions élevées| La prise en charge des résolutions élevées est désormais activée par défaut.|
|SSMS est livré avec le pilote Microsoft OLE DB| Pour plus d’informations, consultez [Télécharger Microsoft OLE DB Driver pour SQL Server](https://docs.microsoft.com/sql/connect/oledb/download-oledb-driver-for-sql-server).|
|SSMS n’est pas pris en charge sur Windows 8. Windows 10 et Windows Server 2016 nécessitent la version 1607 (10.0.14393) ou ultérieure|Compte tenu de la nouvelle dépendance vis-à-vis de NetFx 4.7.2, SSMS 18.0 ne peut pas être installé sur Windows 8, les anciennes versions de Windows 10 et Windows Server 2016. Le programme d’installation de SSMS se bloque sur ces systèmes d’exploitation. Windows 8.1 est toujours pris en charge.|
|SSMS n’est plus ajouté à la variable d’environnement PATH|Le chemin de SSMS.EXE (et des outils en général) n’est plus ajouté au chemin. Les utilisateurs peuvent l’ajouter manuellement ou, s’ils utilisent une version moderne de Windows, passer par le menu Démarrer.|
|Les ID de package ne sont plus nécessaires pour développer des extensions SSMS| Avant, SSMS chargeait de façon sélective uniquement les packages connus, ce qui contraignait les développeurs à inscrire leur propre package. Cela n’est plus le cas.|
|SSMS général|Exposition de l’option de configuration AUTOGROW_ALL_FILES pour les groupes de fichiers dans SSMS.|
|SSMS général|Suppression des options risquées « regroupement léger » et « renforcement de priorité » de l’interface graphique utilisateur de SSMS. Pour plus d’informations, consultez l’article [Priority boost details – and why it’s not recommended](https://blogs.msdn.microsoft.com/arvindsh/2010/01/26/priority-boost-details-and-why-its-not-recommended/) (Détails sur le renforcement de priorité – et pourquoi ce n’est pas recommandé. Texte en anglais).
|SSMS général|Nouveau menu et nouvelles combinaisons de touches pour la création de fichiers : **CTRL+ALT+N**. **Ctrl+N** permet toujours de créer une requête.|
|SSMS général|La boîte de dialogue **Nouvelle règle de pare-feu** permet désormais à l’utilisateur de spécifier un nom de règle, au lieu d’en générer un automatiquement pour le compte de l’utilisateur.|
|SSMS général|Amélioration d’IntelliSense dans l’éditeur, en particulier pour T-SQL v140 et ultérieures.|
|SSMS général|Ajout de la prise en charge d’UTF-8 dans boîte de dialogue de classement de l’interface utilisateur de SSMS.|
|SSMS général|Adoption du « Gestionnaire des informations d’identification Windows » pour les mots de passe utilisés récemment dans la boîte de dialogue de connexion. Cela résout le problème de longue date lié à la persistance des mots de passe, qui n’était pas toujours fiable.|
|SSMS général|Prise en charge améliorée des systèmes multimoniteurs en faisant en sorte que de plus en plus de boîtes de dialogue et de fenêtres s’affichent sur le moniteur approprié.|
|SSMS général|Exposition de « paramètre par défaut de la somme de contrôle de sauvegarde » de la configuration du serveur dans la nouvelle page Paramètres de la base de données de la boîte de dialogue Propriétés du serveur. Pour plus d’informations, consultez [https://feedback.azure.com/forums/08035-sql-server/suggestions/34634974](https://feedback.azure.com/forums/08035-sql-server/suggestions/34634974).|
|SSMS général|Exposition de la taille maximale des fichiers journaux des erreurs sous « Configurer les journaux d’erreurs SQL Server ». Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035/suggestions/33624115](https://feedback.azure.com/forums/908035/suggestions/33624115).|
|SSMS général|Ajout de « Migrer vers Azure » sous le menu Outils : nous avons intégré l’Assistant Migration de base de données et Azure Database Migration Service pour fournir un accès simple et rapide afin d’accélérer vos migrations vers Azure.|
|SSMS général|Ajout d’une logique pour inviter l’utilisateur à valider les transactions ouvertes quand l’option « Modifier la connexion » est utilisée.|
|Intégration d’Azure Data Studio|Ajout d’un élément de menu pour démarrer/télécharger Azure Data Studio.|
|Intégration d’Azure Data Studio|Ajout de l’élément de menu « Démarrer Azure Data Studio » à l’Explorateur d’objets.|
|Intégration d’Azure Data Studio|Après un clic droit sur un nœud de base de données dans l’Explorateur d’objets, des menus contextuels s’affichent pour l’utilisateur afin d’exécuter une requête ou créer un nouveau notebook dans Azure Data Studio.|
|Prise en charge d’Azure SQL| Les propriétés de base de données SLO/Edition/MaxSize acceptent désormais les noms personnalisés, ce qui facilite la prise en charge des futures éditions des bases de données Azure SQL.|
|Prise en charge d’Azure SQL| Ajout de la prise en charge des références (SKU) vCore (À usage général et Critique pour l’entreprise) : Gen4_24 et Gen5 en intégralité.|
|Azure SQL Managed Instance|Ajout de « connexions AAD » comme nouveau type de connexion dans SMO et SSMS lors d’une connexion à Azure SQL Managed Instance.|
|Always On|Rehachage du temps de récupération estimé (RTO) et de la perte de données estimée (RPO) dans le tableau de bord Always On de SSMS. Consultez la documentation mise à jour à l’adresse [https://docs.microsoft.com/sql/database-engine/availability-groups/windows/monitor-performance-for-always-on-availability-groups](../database-engine/availability-groups/windows/monitor-performance-for-always-on-availability-groups.md).|
|Always Encrypted| La case à cocher Activer Always Encrypted sous le nouvel onglet Always Encrypted de la boîte de dialogue Se connecter au serveur offre désormais un moyen simple d’activer/de désactiver Always Encrypted pour une connexion de base de données.|
|Always Encrypted avec enclaves sécurisées| Plusieurs améliorations ont été apportées pour prendre en charge Always Encrypted avec enclaves sécurisées dans la préversion de SQL Server 2019 :<br>Champ de texte permettant de spécifier l’URL d’attestation d’enclave dans la boîte de dialogue Se connecter au serveur (sous le nouvel onglet Always Encrypted).<br>Nouvelle case à cocher dans la boîte de dialogue Nouvelle clé principale de colonne permettant d’indiquer si une nouvelle clé principale de colonne doit autoriser les calculs d’enclave.<br>D’autres boîtes de dialogue de gestion de clés Always Encrypted exposent désormais des informations indiquant sur quelles clés principales de colonne les calculs d’enclave sont autorisés.|
|Fichiers d’audit|Abandon de la méthode d’authentification basée sur la clé du compte de stockage au profit de l’authentification basée sur Azure AD.|
|Fichiers d’audit|Mise à jour de la liste des actions d’audit connues pour inclure FEATURE RESTRICTION ADD/CHANGE GROUP/DROP.|
|Classification des données| Réorganisation du menu des tâches de classification des données : ajout d’un sous-menu au menu des tâches de base de données et ajout d’une option pour ouvrir le rapport à partir du menu sans ouvrir au préalable la fenêtre de classification des données.|
|Classification des données|Ajout d’une nouvelle fonctionnalité de « classification des données » à SMO. L’objet Column expose de nouvelles propriétés : SensitivityLabelName, SensitivityLabelId, SensitivityInformationTypeName, SensitivityInformationTypeId et IsClassified (en lecture seule). Pour plus d’informations, consultez [ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/add-sensitivity-classification-transact-sql)|
|Classification des données|Ajout d’un nouvel élément de menu « Rapport de classification » au menu volant « Classification des données ».|
|Classification des données| Recommandations mises à jour.|
|Mise à niveau du niveau de compatibilité de la base de données|Ajout d’une nouvelle option sous **<Database name>**  > **Tâches** > **Mise à niveau de la base de données**. Celle-ci démarre le nouvel **Assistant Paramétrage de requêtes** pour guider l’utilisateur dans le processus suivant :<br>Collecte d’une ligne de base de performances avant la mise à niveau du niveau de compatibilité de la base de données.<br>Mise à niveau vers le niveau de compatibilité de la base de données souhaité.<br>Collecte d’un deuxième passage de données de performances sur la même charge de travail.<br>Détection des régressions de la charge de travail et indication de recommandations testées pour améliorer les performances de la charge de travail.<br>Ce processus est semblable au processus de mise à niveau de base de données documenté dans la rubrique [Scénarios d’utilisation du Magasin des requêtes](https://docs.microsoft.com/sql/relational-databases/performance/query-store-usage-scenarios#CEUpgrade), à l’exception de la dernière étape où l’Assistant Paramétrage de requêtes ne s’appuie pas sur un état valide antérieur connu pour générer des recommandations.|
|Assistant Application de la couche Données|Ajout de la prise en charge de l’importation/exportation de l’application de la couche Données avec des tables de graphe.|
|Assistant Importation d’un fichier plat|Ajout d’une logique pour notifier l’utilisateur que l’importation peut avoir abouti à un renommage des colonnes.|
|Integration Services (SSIS)|Les clients peuvent désormais planifier des packages SSIS sur les runtimes d’intégration Azure-SSIS qui se trouvent dans le cloud Azure Government.|
|Integration Services (SSIS)|Quand vous utilisez SQL Agent d’Azure SQL Managed Instance par SSMS, vous pouvez configurer les paramètres et le Gestionnaire des connexions à l’étape de travail de l’agent SSIS.|
|Integration Services (SSIS)|Quand vous vous connectez à Azure SQL Database/Managed Instance, vous pouvez le faire avec la base de données initiale *par défaut*.|
|Integration Services (SSIS)|Ajout d’un nouvel élément d’entrée **Essayer SSIS dans Azure Data Factory** sous le nœud « Catalogues Integration Services », utilisable pour lancer l’« Assistant Création d’Integration Runtime » et créer rapidement « Azure-SSIS Integration Runtime ».
|Integration Services (SSIS)|Ajout du bouton **Créer SSIS IR** dans l’« Assistant Création de catalogue », utilisable pour lancer l’« Assistant Création d’Integration Runtime » et créer rapidement « Azure-SSIS Integration Runtime ».|
|Integration Services (SSIS)|ISDeploymentWizard prend désormais en charge l’authentification SQL, l’authentification intégrée à Azure Active Directory et l’authentification par mot de passe Azure Active Directory en mode ligne de commande.|
|Integration Services (SSIS)|L’Assistant de déploiement prend désormais en charge la création et le déploiement sur le Runtime d’intégration SSIS d’Azure Data Factory.|
|Scripts d’objets|Ajout de nouveaux éléments de menu pour les instructions « CREATE ou ALTER » pendant la génération d’un script pour objets.|
|Magasin des requêtes|Amélioration de la facilité d’utilisation de certains rapports (Consommation globale des ressources) avec l’ajout d’un séparateur de milliers aux nombres affichés sur l’axe des ordonnées des graphiques.|
|Magasin des requêtes|Ajout d’un nouveau rapport Statistiques d’attente des requêtes.|
|Magasin des requêtes|Ajout de la métrique « Nombre d’exécutions » à l’affichage « Requête suivie ».|
|Outils de réplication|Ajout du support de la fonctionnalité de spécification de port non-définie par défaut dans le moniteur de réplication et SSMS.|
|ShowPlan|Ajout du temps écoulé réel, des lignes réelles/estimées sous le nœud d’opérateur de plan d’exécution de requêtes, le cas échéant. L’aspect du plan réel coïncide est en harmonie avec celui du plan Statistiques des requêtes en direct.|
|ShowPlan|Modification de l’info-bulle et ajout d’un commentaire quand l’utilisateur clique sur le bouton Modifier la requête pour un plan d’exécution de requêtes, l’objectif étant d’indiquer à l’utilisateur que le plan d’exécution de requêtes risque d’être tronqué par le moteur SQL si la requête comporte plus de 4 000 caractères.|
|ShowPlan|Ajout de la logique pour l’affichage de « Materializer Operator (External Select) ».|
|ShowPlan|Ajout d’un nouvel attribut de plan d’exécution de requêtes « BatchModeOnRowStoreUSed » pour identifier facilement les requêtes qui utilisent la fonctionnalité « analyse en mode batch sur les rowstores ». Chaque fois qu’une requête effectue une analyse en mode batch sur des rowstores, un nouvel attribut (BatchModeOnRowStoreUsed="true") est ajouté à l’élément StmtSimple.|
|ShowPlan|Ajout de la prise en charge du plan d’exécution de requêtes à LocalCube RelOp pour DW ROLLUP et CUBE.|
|ShowPlan|Nouvel opérateur LocalCube pour les nouvelles fonctionnalités d’agrégation ROLLUP et CUBE dans Azure SQL Data Warehouse.|
|SMO| Prise en charge étendue de SMO pour la création d’index reprenables.|
|SMO| Ajout d’un nouvel événement sur les objets SMO (« PropertyMissing ») pour aider les créateurs d’applications à détecter plus tôt les problèmes de performances de SMO.|
|SMO| Exposition de la nouvelle propriété DefaultBackupChecksum sur l’objet Configuration qui est mappée au « paramètre par défaut de la somme de contrôle de sauvegarde » dans la configuration du serveur.|
|SMO| Exposition de la nouvelle propriété ProductUpdateLevel sur l’objet Server, qui correspond au niveau de maintenance de la version de SQL en cours d’utilisation (par exemple, CU12, RTM).|
|SMO| Exposition de la nouvelle propriété LastGoodCheckDbTime pour l’objet Database, qui correspond à la propriété de base de données « lastgoodcheckdbtime ». Si cette propriété n’est pas disponible, la valeur par défaut 01/01/1900 00:00:00 est retournée.|
|SMO|Déplacement de l’emplacement du fichier RegSrvr.xml (fichier de configuration de serveur inscrit) vers « %AppData%\Microsoft\SQL Server Management Studio » (sans version ; il peut donc être partagé entre les versions de SSMS).|
|SMO|Ajout d’un « témoin cloud » comme nouveau type de quorum et nouveau type de ressource.|
|SMO|Ajout de la prise en charge des « contraintes d’arête » dans SMO et SSMS.|
|SMO|Ajout de la prise en charge de la suppression en cascade aux « contraintes d’arête » dans SMO et SSMS.|
|SMO|Ajout de la prise en charge des autorisations de « lecture/écriture » pour la classification de données.|
|Évaluation des vulnérabilités| Activation du menu de tâches Évaluation des vulnérabilités sur Azure SQL DW.|
|Évaluation des vulnérabilités|Changement de l’ensemble des règles d’évaluation des vulnérabilités exécutées sur des serveurs Azure SQL Managed Instance, pour que les résultats d’analyse de l’évaluation des vulnérabilités soient cohérents avec ceux d’Azure SQL Database.|
|Évaluation des vulnérabilités| L’évaluation des vulnérabilités prend désormais en charge Azure SQL DW.|
|Évaluation des vulnérabilités|Ajout d’une nouvelle fonctionnalité d’exportation permettant d’exporter les résultats d’analyse de l’évaluation des vulnérabilités dans Excel.|
|Observateur XEvent|Dans l’observateur XEvent, activation d’une fenêtre de plan d’exécution de requêtes pour plus d’événements XEvent.|

### <a name="bug-fixes-in-180"></a>Correctifs de bogues dans la version 18.0

| Nouvel élément| Détails|
| :-------| :------|
|Se bloque et gèle|Correction d’une source courante d’incidents SSMS liés aux objets GDI.|
|Se bloque et gèle|Correction d’une source courante de blocages et de performances médiocres quand « Générer un script en tant que Créer/Mettre à jour/Supprimer » est sélectionné (les objets SMO ne sont plus récupérés inutilement).|
|Se bloque et gèle|Correction d’un blocage qui se produisait pendant la connexion à une base de données Azure SQL DB avec MFA quand les traces ADAL étaient activées.|
|Se bloque et gèle|Correction d’un blocage (ou perçu comme tel) qui se produisait pendant l’appel aux Statistiques des requêtes en direct à partir du Moniteur d’activité (le problème se manifestait quand l’authentification SQL Server était utilisée sans que « Persist Security Info » soit défini).|
|Se bloque et gèle|Correction d’un blocage qui pouvait se manifester en sélectionnant « Rapports » dans l’Explorateur d’objets avec les connexions à latence élevée ou en cas de non-accessibilité temporaire des ressources.|
|Se bloque et gèle|Correction d’un plantage dans SSMS lié à l’utilisation du serveur de gestion centralisée et des serveurs Azure SQL Database. Pour plus d’informations, consultez [SSMS 17.5 application error + crash when using Central Management Server](https://feedback.azure.com/forums/908035/suggestions/33374884) (Erreur d’application SSMS et plantage lié à l’utilisation du serveur de gestion centralisée).|
|Se bloque et gèle|Correction d’un blocage dans l’Explorateur d’objets en optimisant la façon dont propriété la IsFullTextEnabled est récupérée.|
|Se bloque et gèle|Correction d’un blocage dans l’« Assistant Copie de base de données » en évitant de générer des requêtes inutiles pour récupérer les propriétés de la base de données.|
|Se bloque et gèle|Correction du problème à l’origine d’un blocage/plantage de SSMS lors de la modification de T-SQL.|
|Se bloque et gèle|Atténuation un problème où SSMS cessait de répondre lors de la modification de scripts T-SQL volumineux.|
|Se bloque et gèle|Correction d’un problème qui provoquait une mémoire insuffisante du SSMS lors de la gestion des jeux de données volumineux renvoyés par les requêtes.|
|SSMS général|Correction d’un problème empêchant la communication du paramètre « ApplicationIntent » dans les connexions des « Serveurs inscrits ».|
|SSMS général|Correction d’un problème lié au rendu incorrect du formulaire de la « nouvelle interface utilisateur de l’Assistant Session XEvent » sur des moniteurs haute résolution.|
|SSMS général|Correction d’un problème lors de l’import d’un fichier bacpac.|
|SSMS général|Correction du problème, lors d’une tentative d’affichage des propriétés d’une base de données (avec FILEGROWTH > 2048GB), qui générait une erreur de débordement arithmétique.|
|SSMS général|Correction du problème où le rapport du tableau de bord Performances signalait des attentes de verrous PAGELATCH et PAGEIOLATCH qui étaient introuvables dans les sous-rapports.|
|SSMS général|Autre série de correctifs pour une meilleure prise en charge des écrans multiples par SSMS, en lui faisant ouvrir une boîte de dialogue dans le moniteur approprié.|
|Analysis Services (AS)|Correction d’un problème lié à l’interface utilisateur XEvent AS où les « Paramètres avancés » étaient rognés.|
|Analysis Services (AS)|Correction d’un problème qui entraînait la levée d’une exception de fichier introuvable par une analyse DAX.|
|Azure SQL Database|Correction d’un problème lié au remplissage incorrect de la liste de bases de données pour la fenêtre de requête Azure SQL Database en cas de connexion à une base de données utilisateur dans Azure SQL Database et non à MASTER.|
|Azure SQL Database|Correction d’un problème empêchant l’ajout d’une « Table temporelle » à une base de données Azure SQL.|
|Azure SQL Database|Activation de l’option de sous-menu de propriétés Statistiques sous le menu Statistiques dans Azure, car elle est entièrement prise en charge depuis un certain temps maintenant.|
|Azure SQL - Prise en charge générale|Résolution des problèmes dans un contrôle commun de l’interface utilisateur Azure qui empêchait l’utilisateur d’afficher des abonnements Azure (au-delà de 50). Par ailleurs, le tri a été modifié pour porter sur le nom plutôt que sur l’ID d’abonnement. L’utilisateur pouvait rencontrer ce problème quand il essayait de restaurer une sauvegarde à partir d’une URL, par exemple.|
|Azure SQL - Prise en charge générale|Correction d’un problème dans un contrôle commun de l’interface utilisateur Azure à l’occasion de l’énumération des abonnements qui pouvait générer une erreur « L’index était hors limites. Il ne doit pas être négatif et sa taille doit être inférieure à celle de la collection » quand l’utilisateur ne disposait pas d’abonnements dans certains locataires. L’utilisateur pouvait rencontrer ce problème quand il essayait de restaurer une sauvegarde à partir d’une URL, par exemple.|
|Azure SQL - Prise en charge générale|Correction du problème selon lequel les objectifs de niveau de service étaient codés en dur, ce qui compliquait la prise en charge des nouveaux objectifs Azure SQL par SSMS. Désormais, les utilisateurs peuvent se connecter à Azure et autoriser SSMS à récupérer toutes les données SLO applicables (Édition et Taille maximale).|
|Prise en charge d’Azure SQL Managed Instance|Amélioration/perfectionnement de la prise en charge des instances managées : désactivation des options non prises en charge dans l’interface utilisateur et correction de l’option Afficher les journaux d’audit pour gérer la cible d’audit d’URL.|
|Prise en charge d’Azure SQL Managed Instance|L’Assistant « Génération et publication de scripts » génère un script pour les clauses CREATE DATABASE non prises en charge.|
|Prise en charge d’Azure SQL Managed Instance|Active les Statistiques des requêtes dynamiques pour les instances gérées.|
|Prise en charge d’Azure SQL Managed Instance|Propriétés de la base de données -> Fichiers générait un script incorrect pour ALTER DB ADD FILE.|
|Prise en charge d’Azure SQL Managed Instance|Correction de la régression au niveau du planificateur de l’Agent SQL qui choisissait la planification ONIDLE même quand un autre type de planification était choisi.|
|Prise en charge d’Azure SQL Managed Instance|Ajustement de MAXTRANSFERRATE, MAXBLOCKSIZE pour la création de sauvegardes dans Stockage Azure.|
|Prise en charge d’Azure SQL Managed Instance|Correction d’un problème lié à la génération d’un script pour la sauvegarde de la fin du journal avant l’opération RESTORE (cela n’est pas pris en charge par CL).|
|Prise en charge d’Azure SQL Managed Instance|Correction d’un problème lié à l’Assistant Création d’une base de données qui ne générait pas de script correct pour l’instruction CREATE DATABASE.|
|Prise en charge d’Azure SQL Managed Instance|Traitement spécial des packages SSIS dans SSMS lors des connexions à des instances gérées.|
|Prise en charge d’Azure SQL Managed Instance|Correction d’un problème lié à l’affichage d’une erreur quand le « Moniteur d’activité » était utilisé en étant connecté à des instances managées.|
|Prise en charge d’Azure SQL Managed Instance|Amélioration de la prise en charge des connexions AAD (dans l’Explorateur SSMS).|
|Prise en charge d’Azure SQL Managed Instance|Amélioration de la génération de script des objets de groupes de fichiers SMO.|
|Prise en charge d’Azure SQL Managed Instance|Amélioration de l’interface utilisateur des informations d’identification.|
|Prise en charge d’Azure SQL Managed Instance|Ajout de la prise en charge de la réplication logique.|
|Prise en charge d’Azure SQL Managed Instance|Correction d’un problème à l’origine de l’échec du clic droit sur une base de données et du choix de l’option « Importer une application de la couche Données ».|
|Prise en charge d’Azure SQL Managed Instance|Correction d’un problème à l’origine de l’affichage d’erreurs en cas de clic droit sur un « TempDB ».|
|Prise en charge d’Azure SQL Managed Instance|Correction d’un problème lié à l’écriture de scripts pour l’instruction ALTER DB ADD FILE dans SMO, à l’origine de la génération d’un script T-SQL vide.|
|Prise en charge d’Azure SQL Managed Instance|Amélioration de l’affichage des propriétés spécifiques au serveur des instances managées (génération de matériel, niveau de service, stockage utilisé et réservé).|
|Prise en charge d’Azure SQL Managed Instance|Correction d’un problème lié à l’écriture de scripts d’une base de données (« Script comme créer... ») qui ne créait pas de script sur les groupes de fichiers et fichiers supplémentaires. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035/suggestions/37326799](https://feedback.azure.com/forums/908035/suggestions/37326799). |
|Sauvegarde/restauration/attachement/détachement de base de données|Correction d’un problème qui empêchait l’utilisateur d’attacher une base de données quand le nom de fichier physique du fichier .mdf ne correspondait pas au nom de fichier d’origine.|
|Sauvegarde/restauration/attachement/détachement de base de données|Correction d’un problème qui empêchait SSMS de trouver un plan de restauration valide ou qui en trouvait un non optimal. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/32897752](https://feedback.azure.com/forums/908035-sql-server/suggestions/32897752). |
|Sauvegarde/restauration/attachement/détachement de base de données|Correction d’un problème empêchant l’Assistant Attachement de base de données d’afficher les fichiers secondaires renommés. À présent, le fichier s’affiche et un commentaire le concernant est ajouté (par exemple, « introuvable »). Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035/suggestions/32897434](https://feedback.azure.com/forums/908035/suggestions/32897434). |
|Assistant Copie de base de données|Générer des scripts/Transférer/Assistant Copie de base de données : la tentative de création d’une table avec une table en mémoire ne force pas l’option ansi_padding on.|
|Assistant Copie de base de données|Interruption de Tâche de transfert de bases de données/Assistant Copie de base de données sur SQL Server 2017 et SQL Server 2019.|
|Assistant Copie de base de données|Générer des scripts/Transférer/Assistant Copie de base de données : création d’une table de script avant la création d’une source de données externe associée.|
|Boîte de dialogue Connexion|Possibilité de supprimer des noms d’utilisateurs de la liste de noms d’utilisateurs précédente en appuyant sur la touche Suppr. Pour plus d’informations, consultez [Allow deletion of users from SSMS login window](https://feedback.azure.com/forums/908035/suggestions/32897632) (Autoriser la suppression d’utilisateurs depuis la fenêtre de connexion SSMS).|
|Assistant Importation de DAC|Correction d’un problème empêchant l’Assistant Importation de DAC de fonctionner avec une connexion utilisant AAD.|
|Classification des données|Correction d’un problème lors de l’enregistrement des classifications dans le volet de classification des données alors que d’autres volets de classification des données étaient ouverts sur d’autres bases de données.|
|Assistant Application de la couche Données|Correction d’un problème empêchant l’utilisateur d’importer une application de la couche Données (.dacpac) en raison d’un accès limité au serveur (par exemple, aucun accès à toutes les bases de données se trouvant sur le même serveur).|
|Assistant Application de la couche Données|Correction du problème qui ralentissait considérablement l’importation quand de nombreuses bases de données étaient hébergées sur le même serveur SQL Azure.|
|Tables externes|Ajout de la prise en charge de Rejected_Row_Location dans le modèle, SMO, IntelliSense et la grille de propriétés.|
|Assistant Importation d’un fichier plat|Correction d’un problème empêchant l’Assistant Importation de fichier plat de gérer correctement les guillemets doubles (échappement). Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035/suggestions/32897998](https://feedback.azure.com/forums/908035/suggestions/32897998). |
|Assistant Importation d’un fichier plat|Correction d’un problème lié à la gestion incorrecte des types virgule flottante (dans les paramètres régionaux qui utilisent un séparateur différent pour les virgules flottantes).|
|Assistant Importation d’un fichier plat|Correction d’un problème lié à l’importation de bits quand les valeurs sont 0 ou 1. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898535](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898535). |
|Assistant Importation d’un fichier plat|Correction d’un problème lié aux valeurs en virgule flottante qui étaient entrées comme valeurs Null.|
|Assistant Importation d’un fichier plat|Correction d’un problème empêchant l’Assistant Importation de traiter des valeurs décimales négatives.|
|Assistant Importation d’un fichier plat|Correction d’un problème empêchant l’Assistant d’effectuer l’importation à partir de fichiers CSV à colonne unique.|
|Assistant Importation d’un fichier plat|[prévue pour SSMS 17.9] Correction du problème où l’Assistant Importation d’un fichier plat n’autorisait pas le changement de table de destination quand une table existait déjà. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186](https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186). |
|Visionneuse de l’aide|Amélioration de la logique autour de la prise en compte des modes en ligne/hors connexion (il peut rester quelques problèmes nécessitant d’être traités).|
|Visionneuse de l’aide|Correction de l’option « Afficher l’aide » pour la prise en compte des paramètres en ligne/hors connexion. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/32897791](https://feedback.azure.com/forums/908035-sql-server/suggestions/32897791). |
|Haute disponibilité et reprise d’activité après sinistre (HADR)<BR> Groupes de disponibilité (AG)|Correction d’un problème lié à l’affichage systématique des rôles dans l’« Assistant de basculement de groupes de disponibilité » en tant que « Résolution ».|
|Haute disponibilité et reprise d’activité après sinistre (HADR)<BR> Groupes de disponibilité (AG)|Correction d’un problème lié au fait que SSMS affichait des avertissements tronqués dans le tableau de bord Groupe de disponibilité.|
|Integration Services (IS)|Correction d’un problème SxS qui empêche l’Assistant Déploiement de se connecter à SQL Server quand SQL Server 2019 et SSMS 18.0 sont installés sur la même machine.|
|Integration Services (IS)|Correction d’un problème qui empêche la modification d’une tâche de plan de maintenance durant la conception du plan de maintenance.|
|Integration Services (IS)|Résolution d’un problème qui entraînait le blocage de l’Assistant Déploiement quand le projet en cours de déploiement était renommé.|
|Integration Services (IS)|Activation du paramètre d’environnement dans la fonctionnalité de planification d’Azure-SSIS IR.|
|Integration Services (IS)|Correction d’un problème lié au fait que l’Assistant Création de SSIS Integration Runtime cesse de répondre quand le compte client appartient à plus d’un locataire.|
|Moniteur d'activité des travaux|Résolution d’un incident pendant l’utilisation du moniteur d’activité des travaux (avec des filtres).|
|Explorateur d’objets|Correction d’un problème lié à SSMS qui levait une exception « l’objet ne peut pas être converti du type DBNull en d’autres types » quand le nœud « Gestion » était développé dans l’Explorateur d’objets (DataCollector mal configuré).|
|Explorateur d’objets|Correction d’un problème empêchant l’échappement des guillemets dans l’Explorateur d’objets avant l’appel de « Modifier les N premières... », source de déroute les concepteurs.|
|Explorateur d’objets|Correction d’un problème qui empêchait le lancement de l’Assistant « Importation de l’application de la couche Données » à partir de l’arborescence de Stockage Azure.|
|Explorateur d’objets|Correction d’un problème dans « Configuration de Database Mail » où l’état de la case à cocher SSL n’était pas persistant. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/32895541](https://feedback.azure.com/forums/908035-sql-server/suggestions/32895541). |
|Explorateur d’objets|Correction d’un problème lié à SSMS qui grisait l’option permettant de fermer les connexions existantes à l’occasion d’une restauration de base de données avec is_auto_update_stats_async_on.|
|Explorateur d’objets|Correction d’un problème qui se manifestait quand l’utilisateur faisait un clic droit sur un nœud dans l’Explorateur d’objets (par exemple, « Tables ») et qu’il voulait effectuer une action comme filtrer les tables en accédant à Filtrer > Paramètres de filtre ; le formulaire Paramètres de filtre pouvait s’afficher sur un écran autre que celui où SSMS était actif. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/34284106](https://feedback.azure.com/forums/908035-sql-server/suggestions/34284106). |
|Explorateur d’objets|Correction d’un problème de longue date empêchant le fonctionnement de la touche Suppr dans l’Explorateur d’objets en cas de renommage d’un objet. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/33073510](https://feedback.azure.com/forums/908035-sql-server/suggestions/33073510), [https://feedback.azure.com/forums/908035/suggestions/32910247](https://feedback.azure.com/forums/908035/suggestions/32910247) et autres doublons.|
|Explorateur d’objets|Au moment d’afficher les propriétés de fichiers de base de données existants, la taille apparaît sous une colonne « Taille (Mo) » au lieu de « Taille initiale (Mo) » qui s’affiche lors de la création d’une base de données. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/32629024](https://feedback.azure.com/forums/908035-sql-server/suggestions/32629024). |
|Explorateur d’objets|Désactivation de l’élément de menu contextuel « Conception » dans « Tables de graphe », car ce type de tables n’est pas pris en charge dans la version actuelle de SSMS.|
|Explorateur d’objets|Correction d’un problème entraînant l’affichage incorrect de la boîte de dialogue « Nouvelle planification du travail » sur les écrans haute résolution. Pour plus d’informations, consultez [https://feedback.azure.com/admin/v3/suggestions/35541262](https://feedback.azure.com/admin/v3/suggestions/35541262). |
|Explorateur d’objets|Correction/amélioration de la façon dont la taille de base de données (« Taille (Mo) ») s’affiche dans l’Explorateur d’objets les détails de l’Explorateur d’objets : utilisation de seulement 2 décimales et mise en forme à l’aide du séparateur de milliers. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035/suggestions/34379308](https://feedback.azure.com/forums/908035/suggestions/34379308).|
|Explorateur d’objets|Correction d’un problème qui entraînait l’échec de la création d’un « index spatial » avec une erreur telle que « Pour effectuer cette action, définissez la propriété PartitionScheme ».|
|Explorateur d’objets|Optimisation mineure des performances dans l’Explorateur d’objets pour éviter l’émission de requêtes supplémentaires, quand cela est possible.|
|Explorateur d’objets|Extension à tous les objets de schéma de la logique de la demande de confirmation du renommage d’une base de données (vous pouvez paramétrer cette fonctionnalité).|
|Explorateur d’objets|Ajout de la séquence d’échappement appropriée pour le filtrage de l’Explorateur d’objets. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035/suggestions/36678803](https://feedback.azure.com/forums/908035/suggestions/36678803). |
|Explorateur d’objets|Correction/amélioration de la vue dans les Détails de l’Explorateur d’objets pour afficher les nombres avec les séparateurs appropriés. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035/suggestions/32900944](https://feedback.azure.com/forums/908035/suggestions/32900944). |
|Explorateur d’objets|Correction liée au menu contextuel au niveau du nœud « Tables » lors d’une connexion à SQL Express, où il manquait le menu volant « Nouveau » et la table avec versions gérées par le système, et où les tables de graphe n’étaient pas correctement répertoriées. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035/suggestions/37245529](https://feedback.azure.com/forums/908035/suggestions/37245529). |
|Scripts d’objets|Amélioration globale des performances - La génération de scripts de WideWorldImporters prend moitié moins de temps qu’avec SSMS 17.7.|
|Scripts d’objets|Pendant la génération de scripts pour des objets, la configuration dans l’étendue de la base de données qui comporte des valeurs par défaut est omise.|
|Scripts d’objets|Absence de génération de code T-SQL dynamique pendant la génération de scripts. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898391](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898391). |
|Scripts d’objets|Omission de la syntaxe de graphe « as edge » et « as node » pendant la génération d’un script pour une table sur SQL Server 2016 et versions antérieures.|
|Scripts d’objets|Correction d’un problème qui entraînait l’échec de la génération de scripts d’objets de base de données lors de la connexion à une base de données Azure SQL Database à l’aide d’AAD avec l’authentification multifacteur (MFA).|
|Scripts d’objets|Correction d’un problème entraînant une erreur à la suite d’une tentative de génération d’un script pour un index spatial avec GEOMETRY_AUTO_GRID/GEOGRAPHY_AUTO_GRID sur une base de données Azure SQL.|
|Scripts d’objets|Correction d’un problème à l’origine du ciblage permanent d’une instance SQL Server locale par les scripts de base de données (d’une base de données Azure SQL), même si les paramètres de script de l’Explorateur d’objetss sont définis pour correspondre à la source.|
|Scripts d’objets|Correction du problème lié à la tentative d’exécuter un script dans une table de base de données SQL DW impliquant des index cluster et non-cluster qui générait des instructions T-SQL incorrectes.|
|Scripts d’objets|Correction d’un problème lié à la tentative d’exécuter un script dans une table de base de données SQL DW avec des « index columnstore cluster » et des « index cluster », qui générait des instructions T-SQL incorrectes (instructions en double).|
|Scripts d’objets|Correction des scripts de table partitionnée sans valeurs de plage (bases de données SQL DW).|
|Scripts d’objets|Correction d’un problème où l’utilisateur ne pouvait pas générer de script d’audit/de spécification d’audit SERVER_PERMISSION_CHANGE_GROUP.|
|Scripts d’objets|Correction d’un problème où l’utilisateur est dans l’impossibilité de générer un script pour les statistiques à partir de SQL DW. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/32897296](https://feedback.azure.com/forums/908035-sql-server/suggestions/32897296). |
|Scripts d’objets|Correction d’un problème où l’« Assistant Générer un script » affiche une table incorrecte contenant une erreur de script lorsque le paramètre « Continuer l’exécution du script en cas d’erreur » est défini sur faux.|
|Scripts d’objets|Génération du script améliorée sur SQL Server 2019.|
|Profiler|Ajout de l’événement « Agrégation Table réécrire la requête » aux événements de Profiler.|
|Magasin de données des requêtes|Correction d’un problème où une exception « DocumentFrame (SQLEditors) » pouvait être levée.|
|Magasin de données des requêtes|Correction d’un problème empêchant l’utilisateur de sélectionner AM ou PM sur l’intervalle de début/fin lors de la tentative de définition d’un intervalle de temps personnalisé dans les rapports du magasin de données des requêtes intégré.|
|Grille de résultats|Correction d’un problème qui activait le mode Contraste élevé (numéros de ligne sélectionnés non visibles).|
|Grille de résultats|Correction du problème qui générait une exception « Index hors limites » quand vous cliquiez sur la grille.|
|Grille de résultats|Correction du problème où la couleur d’arrière-plan de la grille de résultats était ignorée. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035/suggestions/32895916](https://feedback.azure.com/forums/908035/suggestions/32895916). |
|ShowPlan|Les propriétés du nouvel opérateur d’allocation de mémoire ne s’affichent pas correctement quand il existe plusieurs threads.|
|ShowPlan|Ajoutez les 4 attributs suivants dans le RunTimeCountersPerThread du plan d’exécution XML réel : HpcRowCount (nombre de lignes traitées par l’appareil Hpc), HpcKernelElapsedUs (temps écoulé à attendre l’exécution du noyau en cours d’utilisation), HpcHostToDeviceBytes (octets transférés de l’hôte vers l’appareil) et HpcDeviceToHostBytes (octets transférés de l’appareil vers l’hôte).|
|ShowPlan|Correction d’un problème où les nœuds de plan similaires sont mis en surbrillance dans une position incorrecte.|
|SMO|Correction d’un problème qui empêchait SMO/ServerConnection de gérer correctement les connexions basées sur SqlCredential. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/33698941](https://feedback.azure.com/forums/908035-sql-server/suggestions/33698941). |
|SMO|Correction d’un problème où une application écrite à l’aide de SMO rencontrait une erreur si elle essayait d’énumérer les bases de données à partir du même serveur sur plusieurs threads, même si elle utilisait des instances de SqlConnection distinctes sur chaque thread.|
|SMO|Correction de la régression des performances de transfert à partir de tables externes.|
|SMO|Correction du problème lié au caractère thread-safe de ServerConnection qui entraînait une fuite des instances SqlConnection par SMO lors du ciblage d’Azure.|
|SMO|Correction d’un problème qui provoquait une erreur StringBuilder.FormatError lors des tentatives de restauration de bases de données contenant des accolades dans leur nom.|
|SMO|Correction du problème où les bases de données Azure dans SMO adoptaient par défaut le classement non sensible à la casse pour toutes les comparaisons de chaînes au lieu d’utiliser le classement spécifié pour la base de données.|
|Éditeur SSMS|Correction d’un problème lié à « Table système SQL » où la restauration des couleurs par défaut sélectionnait la couleur tilleul foncé, et non la couleur verte par défaut, ce qui rendait la lecture sur un arrière-plan blanc très difficile. Pour plus d’informations, consultez [Restoring wrong default color for SQL System Table](https://feedback.azure.com/forums/908035-sql-server/suggestions/32896906) (Restauration d’une couleur par défaut incorrecte pour la Table système SQL). Le problème persiste sur les versions non anglaises de SSMS.|
|Éditeur SSMS|Résolution d’un problème empêchant IntelliSense de fonctionner en cas de connexion à Azure SQL DW avec l’authentification AAD.|
|Éditeur SSMS|Résolution du problème lié à IntelliSense dans Azure quand l’utilisateur n’a pas d’accès à la base de données **MASTER**.|
|Éditeur SSMS|Correction d’extraits de code pour créer des « tables temporaires » à la suite de leur rupture causée par le respect de la casse de la base de données cible.|
|Éditeur SSMS|Nouvelle fonction TRANSLATE maintenant reconnue par IntelliSense. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898430](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898430). |
|Éditeur SSMS|Amélioration d’IntelliSense sur une fonction intégrée FORMAT. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898676](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898676). |
|Éditeur SSMS|LAG et LEAD sont désormais reconnues comme des fonctions intégrées. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898757](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898757). |
|Éditeur SSMS|Correction d’un problème où IntelliSense donnait un avertissement lors de l’utilisation de « ALTER TABLE...ADD CONSTRAINT...WITH(ONLINE=ON) ».|
|Éditeur SSMS|Correction du problème où plusieurs vues système et fonctions de valeurs de table n’étaient pas de la bonne couleur.|
|Éditeur SSMS|Correction d’un problème où l’onglet de l’éditeur était susceptible de se fermer au lieu d’être sélectionné au moment de cliquer dessus. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035/suggestions/37291114](https://feedback.azure.com/forums/908035/suggestions/37291114). |
|Options de SSMS|Correction d’un problème empêchant le bon redimensionnement de la page **Outils** > **Options** > **Explorateur d’objets SQL Server** > **Commandes**.|
|Options de SSMS|Maintenant, SSMS désactive par défaut le téléchargement automatique de la DTD dans l’éditeur XMLA : l’éditeur de script XMLA (qui utilise le service de langage XML) empêche par défaut le téléchargement automatiquement de la DTD pour les fichiers XMLA potentiellement malveillants. Vous pouvez le contrôler en désactivant le paramètre « Télécharger automatiquement les DTD et les schémas » dans **Outils** > **Options** > **Environnement** > **Éditeur de texte** > **XML** > **Divers**.|
|Options de SSMS|Restauration du raccourci **Ctrl+D** tel qu’il existait dans l’ancienne version de SSMS. Pour plus d’informations, consultez [https://feedback.azure.com/forums/908035/suggestions/35544754](https://feedback.azure.com/forums/908035/suggestions/35544754). |
|Concepteur de tables|Correction d’un incident dans « Modifier 200 lignes ».|
|Concepteur de tables|Correction d’un problème lié au concepteur qui autorisait l’ajout d’une table en étant connecté à une base de données Azure SQL Database.|
|Évaluation des vulnérabilités|Correction d’un problème empêchant le chargement des résultats d’analyse.|
|XEvent|Ajout de deux colonnes « action_name » et « class_type_desc » qui présentent les champs action ID et class type comme des chaînes lisibles.|
|XEvent|Suppression de la limite de l’Observateur XEvent de 1 000 000 événements.|
|XEvent Profiler|Correction d’un problème qui empêchait XEvent Profiler de se lancer en étant connecté à un serveur SQL Server à 96 cœurs.|
|Observateur XEvent|Correction d’un problème entraînant le plantage de l’observateur XEvent en cas de tentative de regroupement des événements à l’aide des « options de barre d’outils d’événements étendus ».|

### <a name="deprecated-and-removed-features-in-180"></a>Fonctionnalités dépréciées et supprimées dans la version 18.0

Liste des fonctionnalités dépréciées ou supprimées
- Débogueur T-SQL
- Diagrammes de base de données
- Les outils suivants ne sont plus installés avec SSMS :
  - OSQL.EXE
  - DReplay.exe
  - SQLdiag.exe
  - SSBDiagnose.exe
  - bcp.exe
  - sqlcmd.exe
- Outils du Gestionnaire de configuration :
  - Le Gestionnaire de configuration SQL Server et le Gestionnaire de configuration du serveur de rapports ne sont plus intégrés au programme d’installation de SSMS.
- Stratégies standard DMF
  - Les stratégies ne sont plus installées avec SSMS. Elles sont appelées à être transférées sur Git. Les utilisateurs pourront éventuellement y contribuer et les télécharger/installer.
- Suppression de l’option -P de la ligne de commande SSMS
  - Pour des raisons de sécurité, l’option qui permettait de spécifier des mots de passe en texte clair sur la ligne de commande a été supprimée.
- Suppression de Générer des scripts > Publier sur le service Web
  - Cette fonctionnalité déconseillée a été supprimée de l’interface utilisateur de SSMS.
- Suppression du nœud « Maintenance > Existant » dans l’Explorateur d’objets.
  - Les nœuds très anciens « Plan de maintenance de base de données » et « SQL Mail » ne seront plus accessibles. Les nœuds modernes « Database Mail » et « Plans de maintenance » continueront de fonctionner normalement.

### <a name="known-issues"></a>Problèmes connus

Lors de l’installation de la version 18.0, vous pouvez rencontrer un problème qui empêche l’exécution de SQL Server Management Studio. Si vous rencontrez ce problème, suivez les étapes de l’article [SSMS2018 - Installed, but will not run](https://feedback.azure.com/forums/908035-sql-server/suggestions/37502512-ssms2018-installed-but-will-not-run) (SSMS2018 - Installé, mais ne s’exécute pas).

## <a name="downloadssdtmediadownloadpng-ssms-1791httpsgomicrosoftcomfwlinklinkid2043154clcid0x409"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.9.1](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409)

- Numéro de version : 17.9.1<br>
- Numéro de build : 14.0.17289.0<br>
- Date de publication : 21 novembre 2018

17.9.1 est une petite mise à jour de la version 17.9 qui comporte les correctifs suivants :

- Correction d’un problème où les utilisateurs qui utilisaient l’authentification universelle Active Directory avec prise en charge de MFA dans l’Éditeur de requête SQL voyaient leur connexion se fermer et se rouvrir à chaque appel de requête. Cette fermeture pouvait avoir pour effet de supprimer de façon inattendue les tables temporaires globales, voire dans certains cas, d’attribuer un nouveau SPID à la connexion.
- Correction d’un problème de longue date où aucun plan de restauration n’était trouvé, ou lors duquel le plan de restauration était inefficace dans certains cas.
- Correction d’un problème dans l’Assistant « Importer une application de la couche Données », qui pouvait entraîner une erreur en cas de connexion à une base de données SQL Azure.

> [!NOTE]
> Les versions non anglaises localisées de SSMS 17.x nécessitent la [mise à jour de sécurité KB 2862966](https://support.microsoft.com/kb/2862966) si l’installation est effectuée sur : Windows 8, Windows 7, Windows Server 2012 et Windows Server 2008 R2.

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40a)

## <a name="downloadssdtmediadownloadpng-ssms-179httpsgomicrosoftcomfwlinklinkid2014306clcid0x409"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.9](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x409)

Numéro de build : 14.0.17285.0<br>
Date de publication : 4 septembre 2018

> [!NOTE]
> Les versions non anglaises localisées de SSMS 17.x nécessitent la [mise à jour de sécurité KB 2862966](https://support.microsoft.com/kb/2862966) si l’installation est effectuée sur : Windows 8, Windows 7, Windows Server 2012 et Windows Server 2008 R2.

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x40a)

### <a name="whats-new"></a>Nouveautés

**SSMS général**

Plan d’exécution de requêtes :

- Le plan d’exécution de requêtes graphique affiche à présent les nouveaux attributs de rétroaction d’allocation de mémoire en mode ligne quand la fonctionnalité est activée pour un plan spécifique : ajout d’IsMemoryGrantFeedbackAdjusted et de LastRequestedMemory à l’élément XML de plan de requête MemoryGrantInfo. Pour plus d’informations sur la rétroaction d’allocation de mémoire en mode ligne, consultez [Traitement de requêtes adaptatif dans les bases de données SQL](https://docs.microsoft.com/sql/relational-databases/performance/adaptive-query-processing).

Azure SQL :

- Ajout de la prise en charge des références SKU vCore dans la création de bases de données Azure. Pour plus d’informations, consultez [Modèle d’achat vCore](https://docs.microsoft.com/azure/sql-database/sql-database-service-tiers#vcore-based-purchasing-model).
 

### <a name="bug-fixes"></a>Correctifs de bogues

**SSMS général**

Moniteur de réplication :

- Correction du problème qui empêchait le démarrage du moniteur de réplication (SqlMonitor.exe) (élément UserVoice : https://feedback.azure.com/forums/908035-sql-server/suggestions/34791079).

Assistant Importation de fichier plat :

- Correction du lien vers la page d’aide dans la boîte de dialogue « Assistant Fichier plat ». 
- Correction du problème selon lequel l’Assistant n’autorisait pas la modification de la table de destination lorsqu’elle existait déjà : les utilisateurs peuvent ainsi réessayer sans avoir à quitter l’Assistant, supprimer la table ayant échoué, puis entrer de nouveau les informations dans l’Assistant (élément UserVoice : https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186).

Application de la couche Données d’importation/exportation :

- Correction d’un problème (dans DacFx) qui pouvait provoquer l’échec de l’importation d’un fichier .bacpac avec un message du type « Erreur SQL72014 : Fournisseur de données SqlClient .Net : Msg 9108, Niveau 16, État 10, Ligne 1. Ce type de statistiques n’est pas pris en charge pour être incrémentiel. en cas de traitement de tables avec des partitions définies et aucun index.

IntelliSense :

- Correction d’un problème empêchant la saisie semi-automatique IntelliSense de fonctionner en cas d’utilisation d’AAD avec l’authentification multifacteur.

Explorateur d'objets :

- Correction du problème selon lequel la « boîte de dialogue Filtre » s’affichait sur des moniteurs aléatoire au lieu de celui sur lequel SSMS était en cours d’exécution (systèmes multimoniteurs).

Azure SQL :

- Correction d’un problème lié à l’énumération des bases de données dans « Bases de données disponibles » : « master » ne s’affichait pas dans la liste déroulante en cas de connexion à une base de données spécifique.
- Correction d’un problème où toute tentative de génération d’un script (« Données » ou « Schéma et données ») échouait en cas de connexion à la base de données Azure SQL Database à l’aide d’AAD avec l’authentification multifacteur (MFA).
- Correction d’un problème dans le concepteur de vues (Vues) empêchant la sélection de l’option « Ajouter des tables » dans l’interface utilisateur en cas de connexion à une base de données Azure SQL Database.
- Correction du problème selon lequel l’éditeur de requête SSMS fermait et rouvrait des connexions pendant le renouvellement de jeton d’authentification multifacteur. Cela permet d’éviter que des effets secondaires (comme la fermeture d’une transaction, qui ne sera jamais rouverte) ne se produisent à l’insu de l’utilisateur. La modification a pour effet d’ajouter l’heure d’expiration du jeton à la fenêtre Propriétés. 
- Correction d’un problème empêchant SSMS d’appliquer les invites de mot de passe aux comptes MSA importés pour AAD avec connexion par authentification multifacteur. 

Moniteur d’activité :

- Correction d’un problème qui provoquait le blocage des « Statistiques des requêtes en direct » quand elles étaient lancées à partir du moniteur d’activité et que l’authentification SQL était utilisée. 

Intégration de Microsoft Azure : 

- Correction du problème selon lequel SSMS affichait seulement les 50 premiers abonnements (boîtes de dialogue Always Encrypted, Sauvegarder/Restaurer à partir d’une URL, et autres).
- Correction d’un problème lié à SSMS qui levait une exception (« Index hors limites ») quand il tentait de se connecter à un compte Microsoft Azure sans compte de stockage (dans la boîte de dialogue Restaurer la sauvegarde à partir d’une URL). 

Scripts d’objets : 

- Avec des scripts « Annuler et créer », SSMS évite désormais de générer du code T-SQL dynamique.
- Avec des scripts portant sur un objet de base de données, SSMS ne génère plus de script pour définir des configurations étendues à la base de données, si elles sont définies sur les valeurs par défaut.

Help :

- Correction d’un problème de longue date selon lequel « Aide sur l’aide » ne respectait pas le mode en ligne/hors connexion.
- Quand vous cliquez sur « Aide | Projets et exemples de la communauté », SSMS ouvre désormais le navigateur par défaut, qui pointe sur une page Git et ne montre aucune erreur ni aucun avertissement quant au fait d’utiliser un ancien navigateur.

### <a name="known-issues"></a>Problèmes connus

> [!IMPORTANT]
> Quand les utilisateurs ont recours à l’authentification *universelle Active Directory avec prise en charge de MFA* dans l’Éditeur de requête SQL, leur connexion peut se fermer et se rouvrir à chaque appel de requête. Cette fermeture peut avoir pour effet de supprimer de façon inattendue les tables temporaires globales voire dans certains d’attribuer un nouveau SPID à la connexion. Cette fermeture ne se produit pas en présence d’une transaction ouverte sur la connexion. Pour contourner ce problème, les utilisateurs peuvent définir `persist security info=true` dans les paramètres de connexion.

## <a name="downloadssdtmediadownloadpng-ssms-1781httpsgomicrosoftcomfwlinklinkid875802"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.8.1](https://go.microsoft.com/fwlink/?linkid=875802)
*Un bogue a été découvert dans la version 17.8 concernant l’approvisionnement des bases de données SQL. C’est pourquoi SSMS 17.8.1 remplace 17.8.*

Numéro de build : 14.0.17277.0<br>
Date de publication : 26 juin 2018

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x40a)

### <a name="whats-new"></a>Nouveautés

**SSMS général**

Propriétés de la base de données :

- Cette amélioration expose l’option de configuration **AUTOGROW_ALL_FILES** pour les groupes de fichiers. Cette nouvelle option de configuration est ajoutée sous Propriétés de la base de données > fenêtre Groupes de fichiers sous la forme d’une nouvelle colonne (Croissance automatique de tous les fichiers) de cases à cocher pour chaque groupe de fichiers disponible (à l’exception du flux de fichier et des groupes de fichiers à mémoire optimisée). L’utilisateur peut activer/désactiver AUTOGROW_ALL_FILES pour un groupe de fichiers donné en décochant la case Autogrow_All_Files correspondante. En conséquence, l’option **AUTOGROW_ALL_FILES** est écrite correctement lors de l’écriture de scripts de base de données pour CREATE / la génération de scripts pour la base de données (SQL 2016 et versions ultérieures).

Éditeur SQL :

- Expérience améliorée avec IntelliSense dans Azure SQL Database lorsque l’utilisateur n’a pas l’accès à MASTER.

Création de scripts :

- Amélioration générale des performances, en particulier sur les connexions à latence élevée.

**Analysis Services (AS)**

- Mise à jour des fournisseurs de données et des bibliothèques de client Analysis Services vers la dernière version, avec prise en charge de la nouvelle autorité AAD Azure Government (login.microsoftonline.us).

### <a name="bug-fixes"></a>Correctifs de bogues

**SSMS général**

Plans de maintenance :

- Correction du problème qui provoquait un échec de la tâche « Notifier l’opérateur » en cas de modification des plans de maintenance avec l’authentification SQL.
    
Création de scripts :

- Correction du problème qui provoquait des échecs de connexion SQL et une insuffisance de ressources en cas d’actions de post-traitement dans SMO.
    
SMO :

- Correction du problème qui provoquait l’échec de Table.Alter() en cas d’ajout d’une colonne avec contrainte par défaut à une table contenant déjà des données. Pour plus d’informations, voir [SQL Server SMO qui génère une contrainte par défaut inline en cas d’ajout d’une colonne à une table contenant des données](https://feedback.azure.com/forums/908035-sql-server/suggestions/32895625).
    
Always Encrypted :

- Correction du problème (dans DacFx) qui provoquait une erreur de dépassement de délai d’attente de verrou en cas d’activation de l’option Always Encrypted sur une table partitionnée.
    

**Analysis Services (AS)**

- Correction d’un problème qui se produisait lors de la modification d’une source de données OAuth dans un modèle de compatibilité de niveau 1400 Analysis Services tabulaire et empêchait la mise à jour des jetons OAuth dans la source de données.
- Correction d’un incident dans SSMS qui a pu se produire en cas d’utilisation d’identifiants de source de données non valides ou de modification de sources de données ne prenant pas en charge la migration Changer la source de données dans Power Query (par exemple, Oracle) dans les modèles de compatibilité de niveau 1400 tabulaires Analysis Services.


### <a name="known-issues"></a>Problèmes connus

- Si l’utilisateur clique sur le bouton *Script* après avoir modifié une propriété du groupe de fichiers dans la fenêtre *Propriétés*, deux scripts sont générés : l’un avec une instruction *USE<database>* et l’autre avec une instruction *USE master*.  Le script avec *USE master* est généré par erreur et doit être ignoré. Exécutez le script qui contient l’instruction *USE<database>* .
- Certaines boîtes de dialogue affichent une erreur d’édition non valide quand les nouvelles éditions *Usage général* ou *Critique pour l’entreprise* d’Azure SQL Database sont utilisées.
- Il peut se produire une latence dans l’observateur XEvents. Il s’agit d’un [problème connu de .NET Framework](https://github.com/Microsoft/dotnet/blob/master/releases/net472/dotnet472-changes.md#sql). Passez à la version NetFx 4.7.2.




## <a name="downloadssdtmediadownloadpng-ssms-177httpsgomicrosoftcomfwlinklinkid873126"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.7](https://go.microsoft.com/fwlink/?linkid=873126)

Numéro de build : 14.0.17254.0<br>
Date de publication : 9 mai 2018

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x40a)


### <a name="whats-new"></a>Nouveautés

**SSMS général**

Moniteur de réplication :   
- Le moniteur de réplication prend désormais en charge l’inscription d’un écouteur pour les scénarios où la base de données du serveur de publication et/ou la base de données du serveur de distribution font partie du groupe de disponibilité. Vous pouvez maintenant analyser les environnements de réplication quand la base de données du serveur de publication et ou la base de données de distribution font partie de groupes de disponibilité AlwaysOn. 
 
Azure SQL Data Warehouse : 
- Ajout de la prise en charge de l’emplacement de ligne rejetée pour les tables externes dans Azure SQL Data Warehouse. 

**Integration Services (IS)**

- Ajout d’une fonctionnalité de planification pour les packages SSIS déployés dans Azure SQL Database. Contrairement à SQL Server local et SQL Database Managed Instance, qui proposent SQL Server Agent comme planificateur de travaux de première classe, SQL Database n’intègre pas de planificateur. Cette nouvelle fonctionnalité SSMS propose une interface utilisateur bien connue qui s’apparente à celle de SQL Server Agent pour la planification des packages déployés dans SQL Database. Si vous utilisez SQL Database pour héberger la base de données de catalogues SSIS, SSISDB, vous pouvez utiliser cette fonctionnalité SSMS pour générer les pipelines, les activités et les déclencheurs Data Factory nécessaires à la planification de packages SSIS. Vous pouvez ensuite modifier et étendre ces objets dans Data Factory. Pour plus d’informations, consultez [Planifier l’exécution de packages SSIS sur Azure SQL Database avec SSMS](../integration-services/lift-shift/ssis-azure-schedule-packages-ssms.md). Pour en savoir plus sur les pipelines, les activités et les déclencheurs Azure Data Factory, consultez [Pipelines et activités dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-pipelines-activities) et [Exécution et déclencheurs du pipeline dans Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-pipeline-execution-triggers).
- Prise en charge de la planification de packages SSIS dans SQL Agent sur une instance managée SQL. Il est désormais possible de créer des travaux SQL Agent pour exécuter des packages SSIS sur l’instance managée. 

### <a name="bug-fixes"></a>Correctifs de bogues

**SSMS général** 

Plan de maintenance :   
- Correction d’un problème où toute tentative de modification de la planification d’un plan de maintenance existant se traduisait par la levée d’une exception. Pour plus d’informations, consultez [SSMS 17.6 crashes when clicking on a schedule in a maintenance plan](https://feedback.azure.com/forums/908035-sql-server/suggestions/33712924).

AlwaysOn : 
- Correction d’un problème empêchant le tableau de bord de latence AlwaysOn de fonctionner avec SQL Server 2012.
 
Création de scripts : 
- Correction d’un problème empêchant la création d’un script de procédure stockée pour Azure SQL Data Warehouse pour un utilisateur non-administrateur.
- Correction d’un problème lié au fait que la création d’un script de base de données pour Azure SQL Database ne donnait pas lieu à la création d’un script pour les propriétés *SCOPED CONFIGURATION*.
 
Télémétrie : 
- Correction d’un problème où SSMS se bloquait au moment de se connecter à un serveur après avoir renoncé à l’envoi de données de télémétrie.
 
Azure SQL Database : 
- Correction d’un problème empêchant l’utilisateur de définir ou modifier le niveau de compatibilité (liste déroulante vide). Pour définir le niveau de compatibilité à 150, l’utilisateur doit toujours utiliser le bouton *Script* et modifier manuellement le script. 
 
SMO : 
- Paramètre Taille du journal des erreurs affiché dans SMO. Pour plus d’informations, consultez [Set the Maximum Size of the SQL Server Error Logs](https://feedback.azure.com/forums/908035-sql-server/suggestions/33624115).  
- Correction de la création de scripts de sauts de ligne dans SMO sur Linux.
- Diverses améliorations sur le plan des performances pendant la récupération de propriétés rarement utilisées.  

IntelliSense : 
- Amélioration des performances : réduction du volume de requêtes IntelliSense pour les données de colonne. Cela est particulièrement utile quand les tables utilisées contiennent une multitude de colonnes. 

Paramètres utilisateur SSMS :
- Correction d’un problème entraînant le redimensionnement incorrect de la page d’options.

Divers :  
- Amélioration de l’affichage de texte dans la page de *détails des statistiques*. 

**Integration Services (IS)**

- Meilleure prise en charge d’Azure SQL Database Managed Instance.
- Correction d’un problème où l’utilisateur ne pouvait pas créer de catalogue pour SQL Server 2014 ou version antérieure.
- Correction de deux problèmes liés aux rapports :
   - Suppression du nom d’ordinateur pour les serveurs Azure.
   - Gestion améliorée du nom d’objet localisé.


### <a name="known-issues"></a>Problèmes connus

Certaines boîtes de dialogue affichent une erreur d’édition non valide quand les nouvelles éditions *Usage général* ou *Critique pour l’entreprise* d’Azure SQL Database sont utilisées.

## <a name="downloadssdtmediadownloadpng-ssms-176httpsgomicrosoftcomfwlinklinkid870039"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.6](https://go.microsoft.com/fwlink/?linkid=870039)

Numéro de build : 14.0.17230.0<br>
Date de publication : 20 mars 2018

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x40a)

### <a name="whats-new"></a>Nouveautés

**SSMS général**

SQL Database Managed Instance :

- Ajout de la prise en charge d’[Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance). Azure SQL Database Managed Instance offre une compatibilité proche de 100 % avec SQL Server local, une implémentation native de [réseau virtuel (VNet)](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) qui fait face aux problèmes de sécurité courants et un [modèle métier](https://azure.microsoft.com/pricing/details/sql-database/) favorable aux clients de SQL Server local.
- Prise en charge de scénarios de gestion courants tels que les suivants :
   - Créer et modifier des bases de données.
   - Sauvegarder et restaurer des bases de données.
   - Importation, exportation, extraction et publication d’applications de la couche Données.
   - Affichage et modification de propriétés du serveur.
   - Prise en charge complète de l’Explorateur d’objets.
   - Écriture d’objets de base de données sous forme de scripts.
   - Prise en charge des travaux de l’Agent SQL.
   - Prise en charge des serveurs liés.
- Vous pouvez en savoir plus sur les instances managées [ici](https://azure.microsoft.com/blog/migrate-your-databases-to-a-fully-managed-service-with-azure-sql-database-managed-instance/).

Explorateur d'objets :
- Paramètres ajoutés pour ne pas imposer des crochets autour des noms lors d’un glisser-déplacer à partir de l’Explorateur d’objets vers une fenêtre de requête. (Suggestions des utilisateurs [32911933](https://feedback.azure.com/forums/908035-sql-server/suggestions/32911933) et [32671051](https://feedback.azure.com/forums/908035-sql-server/suggestions/32671051).)

Classification des données :
- Améliorations générales et résolutions de bogues.

**Integration Services (IS)**

- Ajout de la prise en charge du déploiement de packages sur une instance [SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance).

### <a name="bug-fixes"></a>Correctifs de bogues

**SSMS général**

Classification des données :

- Correction d’un problème dans *Classification des données à cause duquel les classifications nouvellement ajoutées s’affichaient avec un *type d’informations* et une *étiquette sensibilité* obsolètes.
- Résolution d’un problème empêchant la *Classification des données* de fonctionner quand la cible était un serveur configuré avec un classement qui respecte la casse.
        
AlwaysOn :

- Correction d’un problème dans le tableau de bord d’affichage des groupes de disponibilité où le fait de cliquer sur *Collecter les données de latence* pouvait générer une erreur quand le serveur était configuré avec un classement qui respecte la casse.
- Correction d’un problème où SSMS signalait de façon erronée un groupe de disponibilité comme *Distribué* quand le service de cluster s’arrêtait.
- Correction d’un problème survenant lors de la création d’un groupe de disponibilité à l’aide de la boîte de dialogue *Créer le groupe de disponibilité* et où la valeur *ReadOnlyRoutingUrl* est exigée.
- Correction d’un problème survenant quand le serveur principal est en panne et que le basculement manuel vers un serveur secondaire lève une exception NullReferenceException.
- Correction d’un problème survenant pendant la création d’un groupe de disponibilité à l’aide de la fonctionnalité de sauvegarde/restauration pour initialiser une base de données et que les fichiers de base de données sont créés dans le répertoire par défaut sur les réplicas secondaires. Le correctif inclut les opérations suivantes :
   - Ajouter le validateur de répertoire de données/journaux.
   - Effectuer le déplacement des fichiers vers le réplica principal uniquement quand le réplica se trouve sur un autre système d’exploitation.
- Résolution d’un problème où l’Assistant SSMS ne génère pas l’option *CLUSTER_TYPE*, ce qui provoquait l’échec de la jointure secondaire.

Programme d’installation :
- Correction d’un problème où une tentative de mise à niveau de SSMS en installant le « package de mise à niveau » échouait quand SSMS était installé dans un emplacement autre que celui par défaut.

SMO :
- Correction d’un problème de performances où l’écriture du script des tables sur SQL Server 2016 et les versions ultérieures peut prendre jusqu’à 30 secondes (elle prend actuellement moins d’une seconde).

Explorateur d'objets :
- Correction d’un problème où SSMS pouvait lever une exception indiquant, par exemple, que « l’objet ne peut pas être converti de du type DBNull en d’autres types » quand vous tentez de développer le nœud *Gestion* dans l’Explorateur d’objets.
- Correction d’un problème lié au fait que *Démarrer PowerShell* ne détectait pas le module SQLServer quand un profil PS défini par l’utilisateur émet la sortie.
- Correction d’un blocage intermittent qui pouvait se produire lors d’un clic droit sur un nœud Table ou Index dans l’Explorateur d’objets.

Messagerie de base de données :
- Correction d’un problème où l’*Assistant Configuration de la messagerie de base de données* levait une exception en cas de tentative d’affichage/de gestion de plus de 16 profils.


**Analysis Services (AS)**

- Correction d’un problème où en cas de modification d’une source de données sur un modèle de niveau de compatibilité 1400 dans SSMS, les changements apportés n’étaient pas enregistrés sur le serveur.

**Integration Services (IS)**

- Correction d’un problème où SSMS n’affichait pas de nœud de catalogue SSIS ni de rapports quand une connexion était établie à SQL Database Managed Instance

### <a name="known-issues"></a>Problèmes connus

> [!WARNING]
> Il existe un problème connu où SSMS 17.6 devient instable et plante lors de l’utilisation de [Plans de maintenance](../relational-databases/maintenance-plans/maintenance-plans.md). Si vous utilisez des plans de maintenance, n’installez pas SSMS 17.6. Revenez à SSMS 17.5 si vous avez déjà installé 17.6 et que ce problème vous affecte. 



## <a name="downloadssdtmediadownloadpng-ssms-175httpsgomicrosoftcomfwlinklinkid867670"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.5](https://go.microsoft.com/fwlink/?linkid=867670)
Disponibilité générale | Numéro de build : 14.0.17224.0

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x40a)

### <a name="whats-new"></a>Nouveautés

**SSMS général**

Découverte et classification des données :

- Ajout d’une nouvelle fonctionnalité Découverte et classification des données SQL pour la découverte, la classification, l’étiquetage et la création de rapport concernant les données sensibles dans vos bases de données. 
- La découverte automatique et la classification de vos données les plus sensibles (par exemple, données professionnelles, financières, médicales, personnelles) peuvent jouer un rôle essentiel dans la protection des informations de votre organisation.
- Découvrez plus d’informations sur la [Découverte et classification des données SQL](../relational-databases/security/sql-data-discovery-and-classification.md).

Éditeur de requête :

- Ajout de la prise en charge de l’option SkipRows pour le format de fichier externe de texte délimité dans Azure SQL Data Warehouse. Cette fonctionnalité permet aux utilisateurs d’ignorer un nombre spécifié de lignes pendant le chargement de fichiers de texte délimité dans SQL DW. Ajout également de la prise en charge d’Intellisense/SMO correspondante pour le mot clé FIRST_ROW. 

Plan d’exécution de requêtes :

- Activation de l’affichage du bouton de plan estimé pour SQL Data Warehouse
- Ajout du nouvel attribut de plan d’exécution de requêtes *EstimateRowsWithoutRowGoal* et ajout de nouveaux attributs de plan d’exécution de requêtes à *QueryTimeStats* : *UdfCpuTime* et *UdfElapsedTime*. Pour plus d’informations, consultez [Informations sur l’objectif de lignes de l’optimiseur dans le plan d’exécution de requête ajouté dans SQL Server 2017 CU3](https://support.microsoft.com/help/4051361).



### <a name="bug-fixes"></a>Correctifs de bogues

**SSMS général**

Plan d’exécution de requêtes :

- Correction du temps écoulé des statistiques des requêtes actives, pour afficher la durée d’exécution du moteur plutôt que le temps écoulé de la connexion LQS.
- Correction d’un problème empêchant le plan d’exécution de requêtes de reconnaître les opérateurs logiques Apply comme GbApply et InnerApply.
- Correction d’un problème lié à ExchangeSpill.

Éditeur de requête :

- Correction d’un problème lié aux SPID entraînant la génération par SSMS d’une erreur de type « Le format de la chaîne d’entrée est incorrect. (mscorlib) » à l’exécution d’une requête simple précédée de « SET SHOWPLAN_ALL ON ». 


SMO :

- Correction d’un problème empêchant la récupération par SMO des propriétés AvailabilityReplica quand le classement du serveur est sensible à la casse (par conséquent, SSMS peut afficher un message d’erreur de type « L’identificateur en plusieurs parties "a.delimited" ne peut pas être lié ».
- Correction d’un problème dans la classe DatabaseScopedConfigurationCollection empêchant la bonne gestion des classements (ainsi, un SSMS s’exécutant sur un ordinateur avec des paramètres régionaux turcs peut afficher une erreur de type « L’estimation de cardinalité héritée n’est pas une configuration délimitée valide » lors d’un clic droit sur une base de données s’exécutant sur un serveur avec un classement sensible à la casse).
- Correction d’un problème dans la classe JobServer empêchant SMO de récupérer les propriétés de SQL Agent sur un serveur SQL 2005 (par conséquent, SSMS génère une erreur de type « Impossible d’attribuer une valeur par défaut à une variable locale. La variable scalaire « \@ServiceStartMode » doit être déclarée et, finalement, n’affiche pas le nœud SQL Agent dans l’Explorateur d’objets).

Modèles : 

- « Messagerie de base de données » : correction de quelques fautes de frappe [(https://feedback.azure.com/forums/908035/suggestions/33143512)](https://feedback.azure.com/forums/908035/suggestions/33143512).  

Explorateur d'objets :
- Correction d’un problème où la compression gérée échouait pour les index (https://feedback.azure.com/forums/908035-sql-server/suggestions/32610058-ssms-17-4-error-when-enabling-page-compression-o).

Audit :
- Correction d’un problème avec la fonctionnalité *Fusionner les fichiers d’audit*.
<br>

### <a name="known-issues"></a>Problèmes connus

Classification des données :
- La suppression d’une classification, puis l’ajout manuel d’une nouvelle classification pour la même colonne entraînait l’attribution de l’ancien type d’informations et de l’ancienne étiquette de sensibilité à la colonne dans la vue principale.<br>
*Solution de contournement*: Attribuez le nouveau type d’informations et la nouvelle étiquette de sensibilité après l’ajout de la classification à la vue principale et avant l’enregistrement.


## <a name="downloadssdtmediadownloadpng-ssms-174httpsgomicrosoftcomfwlinklinkid864329"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.4](https://go.microsoft.com/fwlink/?linkid=864329)
Disponibilité générale | Numéro de build : 14.0.17213.0

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40a)


### <a name="whats-new"></a>Nouveautés

**SSMS général**

Évaluation des vulnérabilités :
- Ajout d’un nouveau service d’évaluation des vulnérabilités SQL pour analyser la présence éventuelle de vulnérabilités et d’écarts par rapport aux meilleures pratiques dans les bases de données, par exemple, des erreurs de configuration, des autorisations excessives et des données sensibles exposées. 
- Les résultats de l’évaluation sont accompagnés d’étapes actionnables permettant de résoudre chaque problème et, le cas échéant, de scripts de correction personnalisés. Le rapport d’évaluation est adaptable à chaque environnement et aux exigences spécifiques. Pour en savoir plus, consultez la page [Évaluation des vulnérabilités SQL](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment).

SMO :
- Correction du problème à cause duquel *HasMemoryOptimizedObjects levait une exception sur Azure.
- Ajout de la prise en charge de la nouvelle fonctionnalité CATALOG_COLLATION.

Tableau de bord Always On :
- Amélioration de l’analyse de la latence dans les groupes de disponibilité.
- Ajout de deux nouveaux rapports : *AlwaysOn\_Latency\_Primary* et *AlwaysOn\_Latency\_Secondary*.

Plan d’exécution de requêtes :
- Mise à jour des liens, de sorte qu’ils pointent vers la documentation appropriée.
- Permet une analyse de plan unique directement à partir du plan réellement généré.
- Nouvel ensemble d’icônes.
- Ajout de la prise en charge permettant de reconnaître « Appliquer des opérateurs logiques », comme GbApply ou InnerApply.

XE Profiler :
- Renommé XEvent Profiler.
- À présent, les commandes de menu Arrêter/Démarrer arrêtent/démarrent la session par défaut.
- Activation des raccourcis clavier (par exemple, **CTRL+F** pour faire une recherche).
- Ajout des actions database\_name et client\_hostname aux événements concernés dans les sessions XEvent Profiler. Pour que la modification prenne effet, vous devrez peut-être supprimer les instances de sessions QuickSessionStandard et QuickSessionTSQL sur les serveurs - [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981).

Ligne de commande :
- Ajout d’une nouvelle option de ligne de commande («-G ») qui peut être utilisée pour faire en sorte que SSMS se connecte automatiquement à un serveur/une base de données avec l’authentification Active Directory (« Intégrée » ou « Mot de passe »). Pour plus d’informations, consultez la page [Utilitaire SSMS](ssms-utility.md).

Assistant Importation de fichier plat :
- Ajout de la possibilité de choisir un nom de schéma autre que le nom par défaut (« dbo ») lors de la création de la table.

Magasin des requêtes :
- Restauration du rapport « Requêtes ayant régressé » lors du développement de la liste de rapports disponibles dans le Magasin des requêtes.

**Integration Services (IS)**
- Ajout de la fonction de validation de package à l’Assistant Déploiement, ce qui permet à l’utilisateur d’identifier des composants à l’intérieur des packages SSIS non pris en charge dans Azure-SSIS IR.

### <a name="bug-fixes"></a>Correctifs de bogues

**SSMS général**

- Explorateur d'objets : Correction d’un problème empêchant l’affichage du nœud Fonction pour les captures instantanées de base de données - [Connect 3140161](https://connect.microsoft.com/SQLServer/feedback/details/3140161).
Amélioration des performances lors du développement du nœud *Bases de données* quand le serveur possède des bases de données autoclose.
- Éditeur de requête : Correction du problème à cause duquel IntelliSense échouait pour les utilisateurs n’ayant pas accès à la base de données MASTER.
Correction d’un problème qui était à l’origine d’un blocage de SSMS dans certains cas, lors de la fermeture de la connexion à un ordinateur distant - [Connect 3142557](https://connect.microsoft.com/SQLServer/feedback/details/3142557).
- Observateur XEvent : Réactivation de la fonctionnalité d’exportation vers XEL.
Correction de problèmes empêchant l’utilisateur de charger la totalité d’un fichier XEL dans certains cas.
- XEvent Profiler : Correction d’un problème qui était à l’origine d’un blocage de SSMS lorsque l’utilisateur ne disposait pas des autorisations *VIEW SERVER STATE*.
Correction du problème à cause duquel la fermeture de la fenêtre Données actives XE Profiler n’arrêtait pas la session sous-jacente.
- Serveurs inscrits : Correction d’un problème où la commande « Déplacer vers... » cessait de fonctionner : [Connect 3142862](https://connect.microsoft.com/SQLServer/feedback/details/3142862) et [Connect 3144359](https://connect.microsoft.com/SQLServer/feedback/details/3144359/).
- SMO : Correction d’un problème empêchant la méthode TransferData de fonctionner sur l’objet Transfer.
Correction du problème à cause duquel les bases de données de serveur levaient une exception pour les bases de données SQL Data Warehouse en pause.
Correction d’un problème où la création d’un script de base de données SQL sur SQL Data Warehouse générait des valeurs de paramètres T-SQL incorrectes.
Correction du problème à cause duquel les scripts d’une extension de base de données émettaient à tort l’option *DATA\_COMPRESSION*.
- Moniteur d’activité des travaux : Correction du problème à cause duquel l’utilisateur obtenait une erreur « Index hors plage. Il doit être non négatif et inférieur à la taille de la collection. 
      Nom du paramètre : index (System.Windows.Forms) » lorsqu’il tentait de filtrer par catégorie - [Connect 3138691](https://connect.microsoft.com/SQLServer/feedback/details/3138691).
- Dialogue de connexion : Correction d’un problème qui empêchait les utilisateurs de domaine ne disposant pas d’un accès en lecture/écriture à un contrôleur de domaine de se connecter à un serveur SQL Server avec l’authentification SQL : [Connect 2373381](https://connect.microsoft.com/SQLServer/feedback/details/2373381).
- Réplication : Correction du problème à cause duquel une erreur du type « Impossible d’appliquer la valeur "Null" à la propriété ServerInstance » s’affichait au moment de consulter les propriétés d’un abonnement par extraction dans SQL Server.
- Configuration de SSMS : Correction du problème à cause duquel la configuration de SSMS provoquait à tort la reconfiguration de tous les produits installés sur l’ordinateur.
- Paramètres utilisateurs :
   - Grâce à ce correctif, les utilisateurs Azure Government profitent d’un accès ininterrompu à leurs ressources Azure SQL Database et Azure Resource Manager avec SSMS par le biais de l’authentification universelle et de la connexion Azure Active Directory.  Les utilisateurs des versions antérieures de SSMS devront ouvrir Outils|Options|Services Azure et, sous Gestion des ressources, changer la configuration de la propriété « Autorité Active Directory » pour lui donner la valeur https://login.microsoftonline.us.

**Analysis Services (AS)**

- Profiler : correction d’un problème de connexion avec l’authentification Windows à Azure Analysis Services.
- Correction d’un problème qui pouvait provoquer un blocage en cas d’annulation des détails de connexion sur un modèle 1400.
- Lors de sa définition dans la boîte de dialogue Propriétés de connexion, dans le cadre de l’actualisation des informations d’identification, la clé Blob Azure sera désormais visuellement masquée.
- Correction d’un problème dans la boîte de dialogue de sélection de l’utilisateur Azure Analysis Services, pour afficher le GUID de l’ID application au lieu de l’ID objet lors de la recherche.
- Correction d’un problème dans la barre d’outils du concepteur de requêtes Parcourir la base de données/MDX, à cause duquel les icônes de certains boutons étaient incorrectement mappées.
- Correction d’un problème qui empêchait de se connecter à SSAS avec des adresses HTTP/HTTPS msmdpump IIS.
- Plusieurs chaînes de la boîte de dialogue Sélecteur d’utilisateur Azure Analysis Services ont maintenant été traduites dans des langues supplémentaires.
- La propriété MaxConnections est à présent visible pour les sources de données dans les modèles tabulaires.
- L’Assistant Déploiement générera désormais des définitions JSON correctes pour les membres du rôle Azure Analysis Services.
- Correction d’un problème dans SQL Profiler à cause duquel sélectionner l’authentification Windows à Azure Analysis Services invitait quand même à se connecter.



## <a name="downloadssdtmediadownloadpng-ssms-173httpsgomicrosoftcomfwlinklinkid858904"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.3](https://go.microsoft.com/fwlink/?linkid=858904)
Disponibilité générale | Numéro de build : 14.0.17199.0

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40a)


### <a name="enhancements"></a>Améliorations

- Ajout du nouvel Assistant d’importation de fichier plat pour simplifier l’importation des fichiers CSV avec une infrastructure intelligente, nécessitant une intervention de l’utilisateur ou des connaissances techniques minimes. Pour plus d’informations, consultez [Assistant Importer un fichier plat dans SQL](../relational-databases/import-export/import-flat-file-wizard.md).
- Ajout du nœud « XEvent Profiler » à l’Explorateur d’objets. Pour plus d’informations, consultez [Utiliser SSMS XEvent Profiler](../relational-databases/extended-events/use-the-ssms-xe-profiler.md).
- Mise à jour du filtrage et de la catégorisation des attentes dans le rapport des attentes historiques du Tableau de bord Performances.
- Ajout de la vérification syntaxique de la fonction « Predict ».
- Ajout de la vérification syntaxique des requêtes External Library Management.
- Ajout de la prise en charge SMO pour External Library Management.
- Ajout de la prise en charge de « Démarrer PowerShell » dans la fenêtre « Serveurs inscrits » (nécessite un nouveau module SQL PowerShell).
- AlwaysOn : ajout de la [prise en charge du routage en lecture seule](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md) pour les groupes de disponibilité.
- Ajout d’une option pour envoyer les informations de trace dans la fenêtre Sortie pour les connexions « Active Directory - Authentification universelle avec prise en charge de MFA » (option désactivée par défaut ; doit être activée dans les paramètres utilisateur sous « Outils > Options > Services Azure > Azure Cloud > Niveau de trace dans la fenêtre Sortie ADAL »). 
- Magasin des requêtes : 
  - L’interface utilisateur Magasin des requêtes est maintenant accessible même quand QDS est désactivé, si QDS a enregistré des données.
  - L’interface utilisateur Magasin des requêtes expose maintenant les attentes par catégorie dans tous les rapports existants. Cela permet aux clients de gérer les scénarios avec des requêtes principales en attente, par exemple.
- Ajout des en-têtes de paramètres de script rendu facultatif (désactivé par défaut ; peut être activé dans les paramètres utilisateur sous « Outils > Options > Explorateur d’objets SQL Server > Scripts > Inclure l’en-tête des paramètres de script ») - [Article Connect 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199).
- Suppression de la personnalisation « RC ».

### <a name="bug-fixes"></a>Correctifs de bogues

**SSMS général**

- XEvent : 
   - Correction d’un problème où SSMS ouvrait uniquement une partie des événements dans le fichier .xel.
   - Amélioration de l’expérience « Observer les données actives » quand la base de données par défaut n’est pas 'master' - [Article Connect 1222582](https://connect.microsoft.com/SQLServer/feedback/details/1222582).
- AlwaysOn : Correction du problème pouvant provoquer l’échec de la restauration des sauvegardes de journaux avec l’erreur « Le journal dans ce jeu de sauvegarde se termine au numéro de séquence d’enregistrement x, ce qui est trop tôt pour une application à la base de données ».
- Moniteur d’activité des travaux : correction des icônes incohérentes - [Article Connect 3133100](https://connect.microsoft.com/SQLServer/feedback/details/3133100).
- Magasin des requêtes : Correction du problème qui empêchait l’utilisateur de choisir une plage de dates « personnalisée » pour les rapports du magasin des requêtes. Consultez les articles Connect suivants :
   - [Article Connect 3139842](https://connect.microsoft.com/SQLServer/feedback/details/3139842)
   - [Article Connect 3139399](https://connect.microsoft.com/SQLServer/feedback/details/3139399)
- Correction du problème où la boîte de dialogue de connexion n’« effaçait » pas la dernière base de données utilisée quand les informations enregistrées contenaient une base de données nommée et que l’utilisateur sélectionnait la valeur par défaut.
- Scripts d’objets : Correction d’un problème qui empêchait la commande « Générer le script de la base de données » de fonctionner et générait une erreur quand l’utilisateur avait une base de données DW suspendue sur le serveur, mais qu’il sélectionnait une autre base de données non DW et tentait de créer un script de cette dernière.
Correction d’un problème de non-correspondance entre l’en-tête des procédures stockées faisant l’objet d’un script et les paramètres du script, d’où un script équivoque - [Article Connect 3139784](https://connect.microsoft.com/SQLServer/feedback/details/3139784).
Réactivation du « bouton Script » lors du ciblage d’objets Azure SQL.
  Correction d’un problème lié à SSMS empêchant la création d’un script pour les opérations « Modifier » ou « Exécuter » sur certains objets (UDF, View, SP, Trigger) avec une connexion à une base de données SQL Azure Database - [Article Connect 3136386](https://connect.microsoft.com/SQLServer/feedback/details/3136386).
- Éditeur de requête :
  - Amélioration d’Intellisense lors du ciblage de bases de données SQL Azure.
  - Correction d’un problème qui faisait échouer les requêtes en raison de l’expiration d’un jeton d’authentification (authentification universelle).
  - Amélioration d’Intellisense avec les bases de données Azure SQL. En particulier, dans le cas d’une connexion à Azure SQL Database, la dernière grammaire de T-SQL (140) est maintenant utilisée.
  - Correction d’un problème où l’ouverture d’une fenêtre de requête avec une connexion à une base de données autre que DataWarehouse sur un serveur générait différentes erreurs liées aux types/options non pris en charge pour toutes les fenêtres de requête ouvertes postérieurement sur ce serveur.
- AlwaysOn :
   - Ajout d’une colonne en mode amorçage au tableau de bord AlwaysOn et à la page de propriétés des groupes de disponibilité.
   - Correction d’un problème empêchant la création d’un groupe de disponibilité Linux quand le groupe de disponibilité principal est sur Windows - [Article Connect 3139856](https://connect.microsoft.com/SQLServer/feedback/details/3139856).
- Correction de plusieurs problèmes de « mémoire insuffisante » dans SSMS lors de l’exécution de requêtes - [Article Connect 2845190](https://connect.microsoft.com/SQLServer/feedback/details/2845190) et [Article Connect 3123864](https://connect.microsoft.com/SQLServer/feedback/details/3123864).
- Profiler : 
   - Correction d’un problème empêchant Profiler de fonctionner en cas de ciblage de SQL 2005.
   - Correction d’un problème de non-respect de l’option de connexion « Faire confiance au certificat de serveur » par Profiler.
- Moniteur d’activité : correction d’un problème qui empêchait le Moniteur d’activité de fonctionner quand il ciblait une instance SQL Server exécutée sur Linux.
- Correction d’un problème avec la classe de transfert SMO qui ne transférait pas les objets source de données externe ou les objets format de fichier externe. Les objets de ces types sont maintenant inclus dans le transfert.
- Serveurs inscrits :
   - Activation de la requête multiserveur pour les serveurs de l’agent utilisateur (elle essaie d’utiliser le même jeton pour chaque serveur de l’agent utilisateur dans le groupe).
- Authentification universelle AD :
   - Correction d’un problème de non-prise en charge de l’authentification Azure AD.
   - Correction d’un problème empêchant le concepteur de tables ou de vues de fonctionner.
   - Correction d’un problème qui empêchait le fonctionnement des commandes « Sélectionner les 1 000 premières lignes » et « Modifier les 200 premières lignes ».
- Restauration de base de données : correction d’un problème où la restauration ne prenait pas en compte le dernier dossier du chemin d’accès lors du déplacement de fichiers vers un autre emplacement.
- Assistant Compression :
   - Correction d’un problème avec l’Assistant Gestion de la compression pour les index. Correction du problème empêchant les Assistants Compression des données de fonctionner sur SQL 2016 et versions antérieures.
        https://connect.microsoft.com/SQLServer/feedback/details/3139342
   - Ajout d’un Assistant Compression pour les tables et index Azure.
- Plan d’exécution de requêtes : 
   - Correction d’un problème où les opérateurs PDW n’étaient pas reconnus.
- Propriétés du serveur :
   - Correction d’un problème qui empêchait la modification de l’affinité des processeurs de serveur.


**Analysis Services (AS)**

- Correction de plusieurs problèmes avec l’Assistant Déploiement pour prendre en charge les modèles tabulaires de niveau de compatibilité 1400 et les sources de données Power Query.
- L’Assistant Déploiement peut maintenant être déployé sur Azure AS quand il est exécuté à partir de la ligne de commande.
- Quand il utilise l’authentification Windows dans Azure AS, l’utilisateur voit désormais le nom de son compte d’utilisateur correctement affiché dans l’Explorateur d’objets.


### <a name="known-issues-in-this-173-release"></a>Problèmes connus dans cette version 17.3 :

**SSMS général**

- Les fonctionnalités SSMS suivantes ne sont pas prises en charge pour l’authentification Azure AD qui utilise l’agent utilisateur avec MFA :
   - L’Assistant Paramétrage du moteur de base de données n’est pas pris en charge pour l’authentification Azure AD. Il existe un problème connu qui fait que l’utilisateur voit apparaître un message d’erreur énigmatique : « Impossible de charger le fichier ou l’assembly "Microsoft.IdentityModel.Clients.ActiveDirectory",… » au lieu du message attendu « L’Assistant Paramétrage du moteur de base de données ne prend pas en charge Microsoft Azure SQL Database ». (DTAClient) ».
- La tentative d’analyse d’une requête dans les résultats DTA provoque une erreur : « L’objet doit implémenter IConvertible. mscorlib ».
- L’option *Requêtes régressées* ne figure pas dans la liste Magasin des requêtes des rapports affichés dans l’Explorateur d’objets.
   - Solution de contournement : Cliquez avec le bouton droit sur le nœud **Magasin des requêtes**, puis sélectionnez **Afficher les requêtes régressées**.

**Integration Services (IS)**

- Le paramètre [execution_path] dans [catalog].[event_message] n’est pas correct pour les exécutions de package dans Scale Out. [execution_path] commence par « \Package » au lieu du nom d’objet du package exécutable. Quand vous affichez le rapport Vue d’ensemble des exécutions de package dans SSMS, le lien « Chemin d’accès de l’exécution » dans Vue d’ensemble de l’exécution ne fonctionne pas. Solution de contournement : cliquez sur « Afficher les messages » dans le rapport Vue d’ensemble pour vérifier tous les messages d’événement.


## <a name="downloadssdtmediadownloadpng-ssms-172httpsgomicrosoftcomfwlinklinkid854085"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.2](https://go.microsoft.com/fwlink/?linkid=854085)
Disponibilité générale | Numéro de build : 14.0.17177.0

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40a)

### <a name="enhancements"></a>Améliorations

- L’authentification multifacteur (MFA)
  - L’authentification de plusieurs utilisateurs Azure AD pour une authentification universelle avec l’authentification multifacteur (agent utilisateur avec MFA)
  - Un nouveau champ d’entrée des informations d’identification de l’utilisateur a été ajouté pour l’authentification universelle avec MFA afin de prendre en charge l’authentification de plusieurs utilisateurs.
- La boîte de dialogue de connexion prend désormais en charge les 5 méthodes d’authentification suivantes :
  - Authentification Windows
  - Authentification SQL Server
  - Active Directory - Authentification universelle avec prise en charge de MFA
  - Active Directory - Authentification par mot de passe
  - Active Directory - Authentification intégrée

- L’Assistant Importation/exportation de base de données pour DacFx utilisant l’authentification universelle avec MFA.
- Pour la prise en charge de l’API, consultez [IUniversalAuthProvider Interface](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx) (Interface IUniversalAuthProvider).
- La bibliothèque ADAL gérée, utilisée par l’authentification universelle Azure AD avec MFA, a été mise à niveau vers la version 3.13.9.
- Par ailleurs, une nouvelle interface CLI a été publiée, prenant en charge le paramètre d’administration Azure AD pour SQL Database et SQL Data Warehouse.

 Pour plus d’informations sur les méthodes d’authentification Active Directory, consultez [Authentification universelle avec SQL Database et SQL Data Warehouse (prise en charge de SSMS pour MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) et [Configurer l’authentification multifacteur Azure SQL Database pour SQL Server Management Studio](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- La fenêtre Sortie a des entrées pour les requêtes exécutées pendant le développement des nœuds de l’Explorateur d’objets
- Concepteur de vues activé pour les bases de données Azure SQL Database
- Les options de script par défaut pour les objets de script dans l’Explorateur d’objets de SSMS ont changé :
  - Avant, la valeur par défaut pour une nouvelle installation spécifiait que le script généré devait cibler la dernière version de SQL Server (actuellement SQL Server 2017).
  - Dans SSMS 17.2, une nouvelle option a été ajoutée : *Faire correspondre les paramètres de script à la source*. Quand la valeur est définie sur *True*, le script généré cible les mêmes version, type de moteur et édition de moteur que le serveur à partir duquel l’objet est scripté.
  - Comme la valeur de *Faire correspondre les paramètres de script à la source* est définie sur *True* par défaut, les nouvelles installations de SSMS scriptent toujours automatiquement par défaut les objets sur la même cible que celle du serveur d’origine.
  - Quand la valeur de *Faire correspondre les paramètres de script à la source* est définie sur *False*, les options de cible de script normales sont activées et fonctionnent comme avant.
Par ailleurs, toutes les options de script ont été déplacées dans leur propre section - *Options de version*. Elles ne sont plus sous *Options de script générales*.

- Nouvelle prise en charge des clouds nationaux dans « Restaurer à partir de l’URL »
- Les rapports QueryStoreUI prennent désormais en charge des métriques supplémentaires (par exemple RowCount, DOP, CLR Time) de sys.query_store_runtime_stats.
- IntelliSense est maintenant pris en charge par Azure SQL Database https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases
- Sécurité : par défaut, la boîte de dialogue de connexion ne fait pas confiance aux certificats de serveur et demande le chiffrement des connexions Azure SQL Database
- Améliorations générales de la prise en charge de SQL Server sur Linux :
 - Le nœud Messagerie de base de données est de retour
 - Différents problèmes concernant les chemins ont été traités
 - Le moniteur d’activité est plus stable
 - La boîte de dialogue Propriétés de connexion affiche la plateforme appropriée
- Le rapport de serveur Tableau de bord des performances est désormais disponible comme rapport par défaut :
  - Peut se connecter à SQL Server 2008 et versions ultérieures.
  - Le sous-rapport Index manquants utilise la notation pour permettre d’identifier les index plus utiles.
  - Le sous-rapport Historique des statistiques d’attente regroupe maintenant les attentes par catégorie. Les attentes d’inactivité et de mise en veille sont filtrées par défaut.
  - Nouveau sous-rapport Historique des verrous.
- La recherche de nœuds de plan d’exécution de requêtes permet d’effectuer des recherches dans les propriétés de plan. Recherchez facilement n’importe quelle propriété d’opérateur, comme un nom de table. Pour utiliser cette option quand vous affichez un plan :
  - Cliquez avec le bouton droit sur le plan et, dans le menu contextuel, cliquez sur l’option Rechercher un nœud
  - Utiliser **Ctrl+F**


**Analysis Services (AS)**

- Une nouvelle sélection de membre du rôle AAD a été ajoutée pour les utilisateurs sans adresse e-mail dans les modèles Azure AS dans SSMS

**Integration Services (IS)**

- Ajout d’une nouvelle colonne (« Nombre d’exécutions ») dans le rapport d’exécution de SSIS

### <a name="known-issues-in-this-release"></a>Problèmes connus dans cette version :

- Les fenêtres de requête qui utilisent l’authentification « Active Directory – Authentification universelle avec prise en charge de MFA » peuvent rencontrer une erreur similaire à la suivante, quand vous tentez d’exécuter une requête ouverte depuis une heure :

   `Msg 0, Level 11, State 0, Line 0
The connection is broken and recovery isn't possible. The client driver attempted to recover the connection one or more times and all attempts failed. Increase the value of ConnectRetryCount to increase the number of recovery attempts.`

   La réexécution de la requête doit permettre de surmonter l’erreur.

- Les fonctionnalités SSMS suivantes ne sont pas prises en charge pour l’authentification Azure AD qui utilise l’authentification universelle avec MFA :
  - Le concepteur **Nouvelle table/vue** affiche l’ancienne invite de connexion et ne fonctionne pas pour l’authentification Azure AD.
  - La fonctionnalité **Modifier les 200 premières lignes** ne prend pas en charge l’authentification Azure AD.
  - Le composant **Serveur inscrit** ne prend pas en charge l’authentification Azure AD.
  - L’**Assistant Paramétrage du moteur de base de données** n’est pas pris en charge pour l’authentification Azure AD. Il existe un problème connu qui fait que l’utilisateur voit s’afficher un message d’erreur énigmatique : *Impossible de charger le fichier ou l’assembly "Microsoft.IdentityModel.Clients.ActiveDirectory", …* au lieu du message attendu *L’Assistant Paramétrage du moteur de base de données ne prend pas en charge Microsoft Azure SQL Database. (DTAClient)* .

**Analysis Services (AS)**

- L’Explorateur d’objets dans SSAS n’affiche pas le nom d’utilisateur de l’authentification Windows dans les propriétés de connexion d’Azure AS.

### <a name="bug-fixes"></a>Correctifs de bogues

- Correction d’un problème quand vous tentez d’imprimer les résultats d’une requête (sous forme de texte).  https://connect.microsoft.com/SQLServer/feedback/details/3055225/
- Correction d’un problème où SSMS supprimait sans raison des tables et d’autres objets lors de la mise en script de la suppression de ces objets sur une base de données Azure SQL.
- Correction d’un problème où SSMS refusait parfois de démarrer avec une erreur de type « Un ou plusieurs composants introuvables. Réinstallez l’application »
- Correction d’un problème où le SPID dans l’interface utilisateur de SSMS pouvait devenir obsolète et ne plus être synchronisé. https://connect.microsoft.com/SQLServer/feedback/details/1898875
- Correction d’un problème dans le programme d’installation (sans assistance) de SSMS où l’argument /passive était traité comme /quiet.
- Correction d’un problème où SSMS levait parfois une erreur « Référence d’objet non définie sur une instance de l’objet » au démarrage. https://connect.microsoft.com/SQLServer/feedback/details/3134698
- Correction d’un problème avec l’« Assistant Compression de données » qui était à l’origine du blocage de SSMS quand vous appuyiez sur « Calculer » sur la table graphique
- Correction d’un problème de performances survenant quand vous cliquiez avec le bouton droit sur l’index d’une table (avec une connexion Internet lente). https://connect.microsoft.com/SQLServer/feedback/details/3120783
- Correction d’un problème lié au fait que SSMS ne pouvait pas énumérer les fichiers de sauvegarde sur les serveurs avec un classement respectant la casse. https://connect.microsoft.com/SQLServer/feedback/details/3134787 et https://connect.microsoft.com/SQLServer/feedback/details/3137000
- Corrections assorties pour le plan d’exécution de requêtes et la comparaison de plans d’exécution de requêtes
- Correction d’un problème lié au fait que la boîte de dialogue Connexion ne permettait pas à l’utilisateur de spécifier le « Protocole réseau » à utiliser pour la connexion, à moins que SQL Server ne soit installé sur l’ordinateur exécutant SSMS. https://connect.microsoft.com/SQLServer/feedback/details/3134997
- Amélioration de la prise en charge des configurations multimoniteurs où des boîtes de dialogue SSMS s’affichaient dans des emplacements « aléatoires ». Ajout d’une nouvelle option « Boîtes de dialogue de tâches » sous les paramètres utilisateur « Explorateur d’objets SQL Server | Commandes » pour permettre la mémorisation de la position d’une boîte de dialogue de tâche ou d’une feuille de propriétés quand elle se ferme. https://connect.microsoft.com/SQLServer/feedback/details/889169, https://connect.microsoft.com/SQLServer/feedback/details/1158271, https://connect.microsoft.com/SQLServer/feedback/details/3135260 
- Correction d’un problème lié au fait que SSMS ne pouvait pas changer les propriétés d’une base de données Azure SQL Database chiffrée
- Amélioration de l’option « Ignorer les résultats après l’exécution ». https://connect.microsoft.com/SQLServer/feedback/details/1196581
- Amélioration/correction d’un problème où les utilisateurs ne pouvaient pas accéder aux abonnements Azure pour lesquels ils n’étaient pas administrateurs.
- Amélioration de l’Assistant « Restauration de la base de données » pour que la base de données cible reste sélectionnée dans l’Explorateur d’objets, indépendamment de la sélection de la base de données source. https://connect.microsoft.com/SQLServer/feedback/details/3118581
- Correction d’un problème lié au fait que l’Explorateur d’objets ne triait pas correctement les « Procédures stockées compilées en mode natif » récemment ajoutées. https://connect.microsoft.com/SQLServer/feedback/details/3133365
- Correction d’un problème où « SÉLECTIONNER LES N PREMIÈRES LIGNES » n’incluait pas la clause « TOP ». Pour Azure SQLDW. https://connect.microsoft.com/SQLServer/feedback/details/3133551 et https://connect.microsoft.com/SQLServer/feedback/details/3135874
- QueryStoreUI : Correction d’un problème où les intervalles de temps non personnalisés ne fonctionnaient pas correctement pour tous les rapports.
- Always Encrypted : Amélioration de la messagerie pour l’état de l’autorisation AKV dans la boîte de dialogue Nouvelle clé CMK. Ajout d’info-bulles à la liste déroulante des clés CEK pour faciliter la distinction entre les clés CEK avec des noms longs. Correction d’un problème qui empêchait l’affichage de certains fournisseurs de magasin de clés CNG dans la boîte de dialogue Nouvelle clé principale de colonne pour Always Encrypted
- Correction du « Nom d’application » incohérent pour les connexions SSMS. https://connect.microsoft.com/SQLServer/feedback/details/3135115
- Correction d’un problème lié au fait que SSMS ne générait pas de scripts corrects pour Azure SQL (tables et index avec l’option DATA_COMPRESSIONS). https://connect.microsoft.com/SQLServer/feedback/details/3133148
- Correction d’un problème lié au fait que l’utilisateur ne pouvait pas utiliser le raccourci **CTRL+Q** pour le Lancement rapide (les nouvelles combinaisons de touches pour activer/désactiver l’option « IntelliSense activé » dans l’éditeur de requête sont désormais **CTRL+B**, **CTRL+I**.) https://connect.microsoft.com/SQLServer/feedback/details/3131968
- Correction d’un problème dans la « Restauration de base de données » où SSMS levait une exception au moment de sélectionner un compte de stockage à partir d’un abonnement avec des comptes associés à des domaines personnalisés définis
- Correction d’un problème dans « Diagramme de base de données » où SSMS levait une erreur « L’index était en dehors des limites du tableau ». Par ailleurs, l’utilisateur pouvait seulement changer la « vue Table » en vue standard. https://connect.microsoft.com/SQLServer/feedback/details/3133792 et https://connect.microsoft.com/SQLServer/feedback/details/3135326
- Correction d’un problème dans « Sauvegarde/restauration vers l’URL » où SSMS n’énumérait pas les comptes de stockage classiques.
- Correction d’un problème où une exception était levée lors de la tentative d’ajout d’éléments sécurisables liés à un schéma à des rôles de base de données. https://connect.microsoft.com/SQLServer/feedback/details/3118143
- Correction d’un problème lié à SSMS qui affichait par intermittence l’erreur « Les données sont de type Null. Cette méthode ou propriété ne peut pas être appelée sur des valeurs Null. » lors du développement d’un nœud de table https://connect.microsoft.com/SQLServer/feedback/details/3136283
- DTA : Correction d’un problème où DTAEngine.exe se terminait avec un endommagement du tas lors de l’évaluation de la fonction de partition avec certaines valeurs limites.


**Analysis Services (AS)**

- Correction d’un problème où la commande AS Restaurer la base de données échouait avec une erreur si la base de données avait un nom différent de l’ID
- Correction d’un problème où la fenêtre de requête DAX ignorait l’option de menu permettant d’activer/désactiver IntelliSense activé
- Correction d’un problème qui empêchait de se connecter à SSAS avec des adresses http/https msmdpump IIS
- Autorisation de la connexion à Azure AS à l’aide d’un mot de passe contenant un point-virgule
- Le script de la commande AS Restaurer la base de données avec l’option « Ignorer l’appartenance » inclut la nouvelle option JSON correspondante quand il est utilisé avec le serveur SQL Server 2017 AS ou Azure AS
- Correction d’un problème très rare où la boîte de dialogue de suppression de base de données levait une erreur lors du chargement
- Correction d’un problème qui pouvait se produire quand vous tentiez d’afficher des partitions dans le modèle de niveau de compatibilité 1400 contenant un mélange de définitions de requête SQL et de partition M

**Integration Services (IS)**
- Correction d’un problème où il était impossible d’afficher les rapports d’informations sur l’exécution du catalogue SSISDB
- Correction de problèmes dans SSMS relatifs aux performances médiocres liées à un grand nombre de projets/packages

## <a name="downloadssdtmediadownloadpng-ssms-171httpsgomicrosoftcomfwlinklinkid849819"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.1](https://go.microsoft.com/fwlink/?linkid=849819)
Disponibilité générale | Numéro de build : 14.0.17119.0

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40a)

### <a name="enhancements"></a>Améliorations

- Profiler : Aide > À propos de affiche maintenant le numéro de version (par exemple, 17.1)
- Les utilisateurs Analysis Service peuvent actualiser les informations d’identification de leurs sources de données pour les modèles 1200 TM et supérieur dans le menu contextuel sur la source de données.
- Les rapports SSIS prédéfinis montrent maintenant les journaux de l’exécution de SSIS Scale Out dans CTP 2.1
- Application de gestion de SSIS Scale Out
  - Affichez les informations de base de Scale Out Master.
  - Ajoutez facilement un worker au déploiement de Scale Out.
  - Affichez tous les Scale Out workers et les informations de base les concernant. Vous pouvez aussi les activer ou les désactiver facilement.

### <a name="bug-fixes"></a>Correctifs de bogues
- AlwaysOn :
  - Correction d’un problème où les propriétés d’un réplica de disponibilité étaient toujours affichées avec le mode « Basculement automatique » pour les groupes de disponibilité WSFC.
  - Correction d’un problème où la liste de routage en lecture seule était remplacée lors de la mise à jour du groupe de disponibilité
- Always Encrypted : correction d’un problème où des informations générées par DacFx étaient manquantes dans le fichier journal généré.
- Plan d’exécution de requêtes : Correction d’un problème où l’interface utilisateur affichait toujours l’attribut de type de jointure réel pour les opérateurs de jointure non adaptatifs.
- Programme d’installation :
  - Correction d’un problème où SSMS 17.0 endommageait SSDT sur Visual Studio 2013 [Article de Microsoft Connect 3133479]
  - Correction d’un problème où cliquer sur « Redémarrer » à la fin du programme d’installation ne redémarrait pas la machine
- Script : empêchement temporaire de la suppression accidentelle d’objets de base de données Azure par SSMS lors de la création d’un script de suppression, via la désactivation de cette option.  Un correctif approprié sera apporté dans une prochaine version de SSMS.
- Explorateur d’objets : correction d’un problème où le nœud « Bases de données » n’était pas développé lors de la connexion à une base de données Azure créée avec « AS COPY »

## <a name="downloadssdtmediadownloadpng-ssms-170httpsgomicrosoftcomfwlinklinkid847722"></a>![télécharger](../ssdt/media/download.png) [SSMS 17.0](https://go.microsoft.com/fwlink/?LinkID=847722)
Disponibilité générale | Numéro de build : 14.0.17099.0

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x40a)

### <a name="enhancements"></a>Améliorations 

- Le package de mise à niveau et les versions de Windows Software Update Services (WSUS) 17.X comportent un package de mise à jour cumulative plus petit 
  - Le package de mise à jour sera également publié sur le catalogue WSUS  
- Mise à jour des icônes Les icônes ont été mises à jour pour être en cohérence avec les icônes fournies par VS Shell. Elles prennent en charge les nouvelles icônes de programme SSMS et Profiler à haute résolution pour différencier les versions 16.X et 17.X
- Module SQL PowerShell
  - Le module PowerShell SQL Server a été supprimé de SSMS et est désormais fourni via PowerShell Gallery (PowerShell 5.0 est maintenant obligatoire pour la prise en charge de la gestion des versions des modules)
  - Améliorations diverses à la « présentation » (mise en forme) de certains objets SMO (par exemple, les bases de données indiquent désormais la taille et la quantité d’espace disponible, et les tables indiquent le nombre de lignes et l’utilisation de l’espace)
  - Colorisation ajoutée quand l’invite de commandes PowerShell est appelée à partir du menu « Démarrer PowerShell » dans l’Explorateur d’objets
  - Les paramètres ClusterType et -RequiredCopiesToCommit ont été ajoutés aux applets de commande AG (New-SqlAvailabilityGroup, Join-SqlAvailabilityGroup, et les applets de commande Set-SqlAvailabilityGroup)
  - Les paramètres - ActiveDirectoryAuthority et - AzureKeyVaultResourceId ont été ajoutés à l’applet de commande Add-SqlAzureAuthenticationContext
  - Ajout des applets de commande Revoke-SqlAvailabilityGroupCreateAnyDatabase, Grant-SqlAvailabilityGroupCreateAnyDatabase et Set-SqlAvailabilityReplicaRoleToSecondary
  - Ajout du paramètre seedingMode aux applets de commande Set-SqlAvailabilityReplica et New-SqlAvailabilityReplica
  - Ajout du paramètre -ConnectionString à Get-SqlDatabase
- Améliorations d’ordre général de SQL Server sur Linux et correctifs pour la copie des journaux de transaction
  - Ajout de la prise en charge des chemins Linux natifs pour attacher, sauvegarder et restaurer une base de données
  - Ajout de la prise en charge des chemins Linux natifs pour le dossier de destination du journal d’audit
- Analysis Services
  - Fenêtre de requête DAX :
    - Mise en correspondance des parenthèses dans l’éditeur
    - Prise en charge de la syntaxe DEFINE MEASURE et DEFINE VAR
    - Différentes améliorations apportées à Intellisense
  - Authentification universelle
    - Permet aux utilisateurs de spécifier un nom d’utilisateur et aucun mot de passe : la boîte de dialogue de connexion d’Azure gère alors la connexion
  - Intégration de PQ SSMS : 
    - Écriture de scripts de travaux de sources de données structurées 
    - Affichage et modification de sources de données structurées dans l’interface utilisateur de PQ
- Nouveau modèle « Ajouter une contrainte Unique »
- Plan d’exécution de requêtes Affichage du maximum au lieu de la somme pour les threads dans la fenêtre Propriétés pour le temps écoulé Affichage des propriétés du nouvel opérateur d’allocation de mémoire Activation du bouton « Modifier la requête » dans les Statistiques des requêtes en direct Prise en charge de l’exécution entrelacée
  - Nouvelle option pour « Analyser le plan d’exécution réel »
  - Améliorations générales apportées à la comparaison du plan d’exécution de requêtes
  - Une fonction a été introduite dans la fonctionnalité de comparaison de plan d’exécution de requêtes pour rechercher des différences significatives dans l’estimation de la cardinalité entre les nœuds correspondants de deux plans de requête et pour effectuer une analyse des causes principales possibles.
- Suppression du gestionnaire de configuration à partir de l’Explorateur de serveurs inscrits
- Activation de la lecture des journaux d’audit à partir du stockage d’objets blob Azure
- Un paramétrage a été ajouté pour Always Encrypted. Reportez-vous à [cette page](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/) pour plus de détails 
- La connexion d’authentification universelle AAD à Azure SQL DB prend en charge les ID de locataire personnalisés 
- La génération de scripts pour Azure SQL Database inclut désormais le texte intégral, les règles et la base de données
- Correctifs de la personnalisation dans les écrans de démarrage pour SSMS et le profileur
- Suppression dans SSMS de l’interface utilisateur du point de contrôle de l’utilitaire
- SSMS peut maintenant créer des bases de données Azure SQL dans l’édition « PremiumRS »
- Groupes de disponibilité Always On
  - Ajout de la prise en charge de nouveaux types de cluster : EXTERNAL et NONE. Ajout de la prise en charge de SQL Server sur Linux. Ajout de l’amorçage automatique comme option pour la synchronisation de données initiale. Correction de certains problèmes, par exemple la gestion des URL de point de terminaison, l’actualisation des bases de données et la présentation de l’interface utilisateur. Suppression de fonctionnalités relatives aux réplicas Azure
  - Amélioration d’IntelliSense pour plusieurs mots clés des groupes de disponibilité
- Moniteur d'activité
  - Ajout d’un nouveau volet « Moniteur d’activité » à la fenêtre de sortie de SSMS
  - Modification du message d’erreur/de dépassement du délai de connexion pour journaliser des informations dans la fenêtre de sortie au lieu d’afficher un message contextuel
  - Suppression du graphique vide (graphique 5) dans la section Vue d’ensemble
  - Ajout de « (en pause) » au titre Vue d’ensemble si la collecte de données du moniteur d’activité est mise en pause
  - Extensions graphiques de SQL Server Nouvelles icônes pour les tables de nœud et d’arête des graphiques Les tables de nœud et d’arête des graphiques seront affichées sous le dossier Tables de graphe Des modèles sont disponibles pour créer des tables de nœud et d’arête des graphiques
- Mode de présentation 3 nouvelles tâches disponibles via le menu de lancement rapide (Ctrl-Q) PresentOn - Activation du mode de présentation PresentEdit - Modification de la taille des polices pour le mode de présentation.  « Police Éditeur de texte » pour l’éditeur de requête.  « Police Environnement » pour les autres composants.
RestoreDefaultFonts - Rétablissement des paramètres par défaut. Il n’existe à l’heure actuelle aucune commande PresentOff. Utilisez RestoreDefaultFonts pour désactiver le mode de présentation*

### <a name="bug-fixes"></a>Correctifs de bogues

- Correction d’un problème lié à SSMS qui se bloquait quand l’utilisateur faisait défiler le plan d’exécution de requêtes via le pavé tactile d’un Surface Book
- Correction d’un problème où SSMS se bloquait pendant un long moment lors de l’obtention des propriétés d’une base de données en cours de restauration ou hors connexion 
- Correction d’un problème où la « Visionneuse d’aide » ne pouvait pas être ouverte dans les builds RC
- Correction d’un problème où les éléments de la « Boîte à outils des tâches des plans de maintenance » peuvent être manquants dans SSMS.
- Correction d’un problème dans SSMS où l’utilisateur ne pouvait pas réduire une base de données quand le nom de cette base de données contenait des accolades. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3122618)
- Correction d’un problème où SSMS, au moment où il essayait de créer un script pour supprimer une base de données Azure, provoquait la suppression de la base de données elle-même. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3131458/)
- Correction d’un problème où les valeurs par défaut ne faisaient pas l’objet d’un script pour les types de tables définis par l’utilisateur. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3119027)
- Autre série d’améliorations des performances liées au menu contextuel des index. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3120783)
- Correction du problème qui provoquait un scintillement excessif lorsque des index manquants du plan d’exécution faisaient l’objet d’un pointage de la souris. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3118510)
- Correction d’un problème où SSMS prenait la base de données hors connexion lors de l’écriture de scripts [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3118550)
- Divers correctifs liés à l’interface utilisateur sur les versions localisées (dans une langue que l’anglais) de SSMS.
- Correction du problème où le nœud de « Always Encrypted Keys » était manquant lors du ciblage de SQL 2016 SP1 Édition Standard.
- Always Encrypted : Activation incorrecte du menu « Always Encrypted » quand SQL 2016 RTM Édition Standard ou n’importe quel serveur SQL 2014 (et les versions antérieures) était ciblé. Correction d’un problème lié à IntelliSense qui signalait une erreur quand la syntaxe CREATE ou ALTER était utilisée. Correction du problème lié à l’échec du chiffrement quand CMK/CEK contenait des caractères qui devaient être placés dans une séquence d’échappement, c’est-à-dire entre crochets. En cas d’exception liée à une mémoire insuffisante dans SSMS, l’utilisateur reçoit une erreur proposant d’utiliser plutôt le module PowerShell (64 bits) natif.
Correction du problème lié à l’échec de l’Assistant AE si l’utilisateur utilisait des abonnements de responsable de groupe de ressources au lieu d’abonnements Azure classiques Correction du problème lié à l’Assistant AE qui affichait une erreur incorrecte quand l’utilisateur ne disposait d’aucune autorisation dans ces abonnements ou qu’il ne possédait pas de coffres de clé Azure dans ces derniers.
Correction d’un problème dans l’Assistant AE dont la page de connexion Azure Key Vault n’affichait pas d’abonnements Azure en présence de plusieurs instances AAD Correction d’un problème dans l’Assistant AE dont la page de connexion Azure Key Vault n’affichait pas les abonnements Azure pour lesquels l’utilisateur disposait d’une autorisation d’accès en lecture
  - Correction d’un problème où les fichiers de ressources ne pouvaient pas être chargés correctement, ce qui provoquait des messages d’erreur imprécis
- Amélioration du contraste des liens hypertexte sur la page Installation de SSMS
- Correction du problème selon lequel les nœuds PolyBase ne s’affichaient pas en cas de connexion à SQL Server Express (2016 SP1)
- Correction d’un problème où SSMS ne pouvait pas changer le niveau de compatibilité d’une base de données Azure pour le faire passer à v140
- Amélioration des performances de l’Explorateur d’objets lors du développement de la liste des bases de données Azure [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3100675)
- Correction d’un problème où l’élément de menu contextuel Afficher le journal SQL Server apparaît de manière incorrecte pour les types de serveurs non relationnels (AS\RS\IS) 
- Correction d’un problème dans lequel la vérification de la syntaxe d’une requête de partition Analysis Services à l’aide de l’authentification SQL pouvait entraîner un message d’échec de connexion
- Correction d’un problème dans lequel le fait de renommer un modèle tabulaire AS de niveau de compatibilité 1400 d’aperçu pouvait échouer dans SSMS
- Correction d’un problème lié au message « échec de l’opération sur le modèle » qui pouvait se produire après avoir tenté une opération non valide sur le serveur AS dans de rares circonstances et rétablir les modifications locales suite à un échec d’enregistrement sur le modèle
- Correction d’une faute d’orthographe dans la boîte de dialogue contextuelle de synchronisation des bases de données Analysis Services
- Les boîtes de dialogue de sauvegarde/restauration de conteneur se trouvent en dehors de l’écran dans les configurations avec plusieurs moniteurs. 
- La création d’une stratégie de sécurité échoue si le nom de l’objet cible contient le caractère `]`.
- Le menu « Ouvrir un fichier récent » de SSMS 2016 n’affiche pas les fichiers récemment enregistrés. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)
- Suppression de la réinitialisation des paramètres utilisateur lors de la mise à jour du shell VS.
- Correction d’un problème qui empêchait l’utilisateur de pouvoir changer le niveau de compatibilité d’une base de données sur SQL Server 2017.
- Les fenêtres de requête utilisant l’authentification universelle AAD ne peuvent pas actualiser la requête au bout d’une heure.
- Suppression dans SSMS de l’interface utilisateur du point de contrôle de l’utilitaire.
- Les connexions d’authentification universelle AAD échouent à interroger des données après l’expiration du jeton initial.
- Impossible de générer des scripts de règles depuis Azure SQL Database vers Azure SQL Database.
- Résolution d’un problème lié au fait que SQL PowerShell ne pouvait pas se connecter aux instances SQL existantes (version 2014 et antérieures). [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/1138754/sql-server-sqlps-powershell-module-fails-connection-to-sql-2012-instance)
- Résolution d’un problème qui provoquait le blocage de SSMS lors d’un échec d’importation des serveurs inscrits.
- Résolution d’un problème qui provoquait le plantage de SSMS si un utilisateur avait certaines autorisations dans une base de données.
- SSMS - des tables disparaissent de l’aire de conception pendant l’examen des vues. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/2946125/ssms-tables-disappears-from-design-surface-while-reviewing-views) 
- La barre de défilement des tables ne permet pas à l’utilisateur de faire défiler le contenu d’une table : seule la flèche haut/bas le permet. Il est également possible de faire défiler le contenu de la table après avoir essayé d’effectuer un défilement à l’aide de la barre de défilement, ce qui est un bogue. [Article de Microsoft Connect](
https://connect.microsoft.com/SQLServer/feedback/details/3106561/sql-server-manager-2016-bug-in-design-view) 
- Les icônes ne s’affichent pas pour les serveurs inscrits une fois le nœud racine actualisé.
- Le bouton du script pour créer une base de données sur les serveurs v12 Azure exécute un script, puis affiche le message « Aucune action pour le script ».
- La boîte de dialogue SSMS Se connecter au serveur n’efface pas l’onglet « Propriétés supplémentaires » pour chaque nouvelle connexion.
- Le script de génération de tâches ne génère pas de scripts de création de base de données pour une base de données Azure SQL Database.
- La barre de défilement du Concepteur de vues apparaît désactivée.
- Les chemins de clés AVK d’Always Encrypted n’incluent pas les ID de version.
- Réduction du nombre de requêtes de l’édition du moteur dans la fenêtre de requête. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3113387)
- Les erreurs Always Encrypted provenant de l’actualisation des modules après chiffrement ne sont pas gérées correctement.
- Changement du délai d’expiration de la connexion par défaut pour OLTP et OLAP de 15 à 30 secondes, pour résoudre une classe d’échecs de connexion ignorés. 
- Correction d’un blocage dans SSMS lors du lancement d’un rapport personnalisé. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3118856)
- Correction du problème qui provoquait l’échec de « Générer le script… » pour les bases de données SQL Azure.
- Correction de « Générer un script en tant que » et « Assistant Génération de scripts », qui n’ajoutaient pas de sauts de ligne supplémentaires lors de la génération de scripts pour des objets comme les procédures stockées. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3115850)
- Fournisseur SQLAS PowerShell : Ajout de la propriété LastProcessed aux dossiers Dimension et MeasureGroup. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3111879)
- Statistiques sur les requêtes en direct : Résolution d’un problème où elles montraient seulement la première requête dans un lot. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3114221)  
- Plan d’exécution de requêtes : Affichage du maximum au lieu de la somme pour les threads dans la fenêtre Propriétés.
- Magasin de requêtes : Ajout d’un nouveau rapport sur les requêtes avec les variation fortes des exécutions.
- Problèmes de performances de l’Explorateur d’objets : [Article Connect](https://connect.microsoft.com/SQLServer/feedback/details/3114074) Le menu contextuel pour les tables se bloque momentanément. SSMS est lent quand l’utilisateur clique avec le bouton droit sur un index pour une table (via une connexion (Internet) à distance). Éviter d’émettre des requêtes sur des tables qui sont triées sur le serveur
- Suppression dans SSMS de l’Assistant Déploiement Azure (pour déployer une base de données sur une machine virtuelle Azure)
- Résolution d’un problème où les index manquants n’étaient pas affichés dans les plans d’exécution dans SSMS [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3114194)
- Résolution du problème courant de blocage lors de l’arrêt dans SSMS
- Résolution du problème de l’Explorateur d’objets qui provoquait une erreur lors de l’affichage du menu contextuel sur les nœuds de groupe de scale out PolyBase [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3115128)
- Résolution d’un problème où SSMS pouvait se bloquer lors d’une tentative d’affichage des autorisations sur une base de données
- Magasin de requêtes : améliorations générales apportées aux éléments du menu contextuel pour les grilles de résultats des rapports du magasin de requêtes
- La configuration d’Always Encrypted pour une table existante échoue avec des erreurs sur des objets non associés. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3103181)
- La configuration d’Always Encrypted pour une base de données existante avec plusieurs schémas ne fonctionne pas. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3109591)
- L’Assistant Colonne chiffrée d’Always Encrypted échoue parce que la base de données contient des vues qui référencent des vues système. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3111925)
- Lors du chiffrement à l’aide d’Always Encrypted, les erreurs provenant de l’actualisation des modules après le chiffrement ne sont pas gérées correctement.
- Résolution du problème de troncation de l’interface utilisateur dans la boîte de dialogue « Nouvelle inscription de serveur »
- Correction de la mise à jour incorrecte par l’interface utilisateur des conditions DMF pour les expressions contenant des valeurs de constante de chaîne incluant des guillemets
- Résolution d’un problème pouvant provoquer le blocage de SSMS lors de l’exécution de rapports personnalisés
- Ajouter l’élément de menu « Execution in Scale Out... » (Exécution en mode scale-out) au nœud de dossier
- Correction d’un problème lié à la fonctionnalité de liste verte des adresses IP du pare-feu SQL Azure DB
- Correction d’un problème dans SSMS qui provoquait une exception de référence d’objet non définie lors de la modification de la source d’une partition multidimensionnelle AS
- Correction d’un problème dans SSMS qui provoquait une exception de référence d’objet non définie lors de la suppression d’un assembly de client d’un serveur AS multidimensionnel
- Correction d’un problème où le renommage d’une base de données 1400 tabulaire AS échouait
- Correction d’un problème de génération de script d’une source de données tabulaire AS de niveau de compatibilité 1400 à partir de la boîte de dialogue des propriétés de connexion
- Suppression de l’hypothèse selon laquelle les tables d’un modèle de niveau de compatibilité 1400 ont au moins une partition
- CTRL+R affiche/masque maintenant le volet de résultats dans l’éditeur de requête SSMS DAX


## <a name="downloadssdtmediadownloadpng-ssms-1653httpsgomicrosoftcomfwlinklinkid840946"></a>![télécharger](../ssdt/media/download.png) [SSMS 16.5.3](https://go.microsoft.com/fwlink/?LinkID=840946)
Disponibilité générale | Numéro de build : 13.0.16106.4

[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x804)| [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x404)| [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x409)| [Français](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40c)| [Allemand](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x407)| [Italien](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x410)| [Japonais](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x411)| [Coréen](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x412)| [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x416)| [Russe](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x419)| [Espagnol](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40a)

Les problèmes suivants ont été résolus dans cette version :

* Résolution du problème introduit dans SSMS 16.5.2 qui provoquait l’expansion du nœud « Table » quand la table comportait plusieurs colonnes éparses.

* Les utilisateurs peuvent déployer des packages SSIS contenant le Gestionnaire de connexions OData qui connectent une ressource Microsoft Dynamics AX/CRM Online au catalogue SSIS. Pour plus d’informations, consultez [Gestionnaire de connexions OData](../integration-services/connection-manager/odata-connection-manager.md).

* La configuration d’Always Encrypted sur une table existante échoue avec des erreurs sur des objets non associés. [Microsoft Connect - ID 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects)

* La configuration d’Always Encrypted pour une base de données existante avec plusieurs schémas ne fonctionne pas. [Microsoft Connect - ID 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work)

* L’Assistant Colonne chiffrée d’Always Encrypted échoue parce que la base de données contient des vues qui référencent des vues système. [Microsoft Connect - ID 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors)

* Lors du chiffrement à l’aide d’Always Encrypted, les erreurs provenant de l’actualisation des modules après le chiffrement ne sont pas gérées correctement.

* Le menu *Ouvrir un fichier récent* n’affiche pas les fichiers récemment enregistrés. [Microsoft Connect - ID 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)

* SSMS est lent quand l’utilisateur clique avec le bouton droit sur un index pour une table (via une connexion (Internet) à distance). [Microsoft Connect - ID 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection)

* Correction d’un problème avec la barre de défilement de SQL Designer. [Microsoft Connect - ID 3114856](https://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016)

* Le menu contextuel pour les tables se bloque momentanément 
 
* Il peut arriver que SSMS lève des exceptions dans le moniteur d’activité et se bloque. [Microsoft Connect - ID 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/)

* SSMS 2016 se bloque avec l’erreur « Le processus a été arrêté en raison d’une erreur interne dans le runtime .NET à l’adresse IP 71AF8579 (71AE0000) avec le code de sortie 80131506 »


## <a name="uninstall-and-reinstall-ssms-17x"></a>Désinstaller et réinstaller SSMS 17.x

Si votre installation de SSMS rencontre des problèmes et qu’une désinstallation et réinstallation standard ne les résolvent pas, vous pouvez d’abord essayer de [réparer](https://support.microsoft.com/help/4028054/windows-10-repair-or-remove-programs) le shell isolé de Visual Studio 2015. Si la réparation du shell isolé de Visual Studio 2015 ne résout pas le problème, les étapes suivantes ont été trouvées pour résoudre de nombreux problèmes aléatoires :

1. Désinstallez SSMS comme vous désinstallez n’importe quelle application (avec *Applications et fonctionnalités*, *Programmes et fonctionnalités*, selon votre version de Windows).

2. Désinstallez le shell isolé de Visual Studio 2015 **à partir d’une invite de commandes avec élévation de privilèges** :

    ```PUSHD "C:\ProgramData\Package Cache\FE948F0DAB52EB8CB5A740A77D8934B9E1A8E301\redist"```

    ```vs_isoshell.exe /Uninstall /Force /PromptRestart```

3. Désinstallez Microsoft Visual C++ 2015 Redistributable comme vous désinstallez n’importe quelle application. Désinstallez x86 et x64 s’ils sont sur votre ordinateur.

4. Réinstallez le shell isolé de Visual Studio 2015 **à partir d’une invite de commandes avec élévation de privilèges** :  

    ```PUSHD "C:\ProgramData\Package Cache\FE948F0DAB52EB8CB5A740A77D8934B9E1A8E301\redist"```  

    ```vs_isoshell.exe /PromptRestart```

5. Réinstallez SSMS.

6. Effectuez une mise à niveau avec la [version la plus récente de Visual C++ 2015 Redistributable](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads) si vous n’êtes plus à jour.

## <a name="additional-downloads"></a>Téléchargements supplémentaires

Pour obtenir la liste de tous les téléchargements de SQL Server Management Studio, rechercher dans le [Centre de téléchargement Microsoft](https://www.microsoft.com/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending).  
  
Pour obtenir la dernière version de SQL Server Management Studio, consultez [Télécharger SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md).  
