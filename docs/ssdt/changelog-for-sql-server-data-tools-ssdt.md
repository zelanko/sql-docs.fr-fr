---
title: Journal des modifications de SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b071f8b8-c8e5-44e0-bbb6-04804dd1863a
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 5bd0e1d3955d898824d285d28979089e2de6f322
ms.openlocfilehash: 243d2e6187a58554cee80066912de7dfcc0c52fc
ms.contentlocale: fr-fr
ms.lasthandoff: 07/31/2017

---
# <a name="changelog-for-sql-server-data-tools-ssdt"></a>Journal des modifications de SQL Server Data Tools (SSDT)
Ce journal des modifications concerne [SQL Server Data Tools (SSDT) pour Visual Studio 2015](https://msdn.microsoft.com/library/mt204009.aspx).  
  
Pour des publications détaillées sur les nouveautés et les modifications, visitez [le blog de l’équipe SSDT](https://blogs.msdn.microsoft.com/ssdt/).

## <a name="ssdt-171"></a>SSDT 17.1
Numéro de build : 14.0.61705.170

### <a name="whats-new"></a>Nouveautés
**Projets AS :**
- Les utilisateurs peuvent définir des indications sur le codage des colonnes dans l’interface utilisateur sur les modèles 1400
- IntelliSense non associé à un modèle est désormais disponible en mode hors connexion
- L’Explorateur de modèles tabulaires contient maintenant un nœud pour représenter des expressions M nommées disponibles sur le modèle (modèles tabulaires de niveau de compatibilité 1400)
- Un sélecteur de personnes Azure Active Directory similaire à la gestion des identités et des accès du portail Microsoft Azure est désormais disponible lors de la configuration des membres des rôles dans les modèles tabulaires

**Projets de base de données :**
- Mis à jour vers DacFx 17.1

### <a name="bug-fixes"></a>Correctifs de bogues
- Correction d’un problème où le nom du groupe des concepteurs Business Intelligence était affiché in correctement dans les options de Visual Studio dans VS2017
- Correction d’un problème où un blocage pouvait se produire lors de la génération d’une carte de code pour une solution avec un projet de rapport ou un projet AS
- Correction de plusieurs problèmes avec l’intégration de PowerQuery pour les modèles tabulaires Analysis Services de niveau de compatibilité 1400
- Correction d’un problème dans la fenêtre du nouvel éditeur DAX où l’opérateur d’assignation ne pouvait pas être sur une ligne distincte lors de la définition d’une mesure
- Correction d’un problème qui empêchait la mise à jour de l’affichage des mesures tabulaires lors du renommage des mesures dans une perspective
- Mise à jour du moteur de l’espace de travail intégré d’Analysis Services et du modèle d’objet tabulaire qui corrige une régression provoquant l’échec du déploiement de projets tabulaires 1200 contenant des traductions sur le serveur SQL Server 2016 Analysis Services
- Correction d’un problème de performances qui rendait la création et la suppression de nouvelles sources de données tabulaires 1400 très lentes
- Correction d’un problème où le diagramme de vue de source de données dans les modèles multidimensionnels pouvait cesser l’affichage en cas de changement rapide entre différentes vues de source de données

## <a name="dacfx-171"></a>DacFx 17.1
- Correction d’un problème lors du chiffrement d’une colonne avec des tables optimisées en mémoire avec d’autres colonnes d’identité
- Prise en charge de SQLDOM pour l’option CATALOG_COLLATION pour CREATE DATABASE

## <a name="dacfx-1701"></a>DacFx 17.0.1 
- Correction d’un problème pour les bases de données avec une clé asymétrique par un module de sécurité matériel (HSM) avec un fournisseur EKM [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3132749/sqlpackage-exe-fails-when-extracting-a-database-which-contains-an-asymmetric-key-using-an-ekm-provider)

## <a name="ssdt-170-supports-up-to-sql-server-2017"></a>SSDT 17.0 (prend en charge jusqu’à SQL Server 2017)
Numéro de build : 14.0.61704.140

### <a name="whats-new"></a>Nouveautés
**Projets de base de données :**
- La modification d’un index cluster sur une vue ne bloque plus le déploiement.
- Les chaînes de comparaison de schéma relatives au chiffrement des colonnes utilisent désormais le nom approprié au lieu du nom de l’instance.   
- Ajout d’une nouvelle option de ligne de commande à SqlPackage: ModelFilePath.  Ceci permet aux utilisateurs avancés de spécifier un fichier model.xml externe pour les opérations d’importation, de publication et de script.   
- L’API DacFx a été étendue pour prendre en charge l’authentification universelle Azure AD et l’authentification multifacteur

**Projets IS :**
- Le Gestionnaire de connexions OData et de sources OData de SSIS prend maintenant en charge la connexion aux flux OData de Microsoft Dynamics AX Online et Microsoft Dynamics CRM Online.
- Les projets SSIS prennent maintenant en charge la version de serveur cible « SQL Server 2017 ». 
- Prise en charge des tâches de contrôle CDC, du séparateur CDC et des sources CDC lors du ciblage de SQL Server 2017. 

**Projets AS :**
- Intégration de PowerQuery à Analysis Services (modèles tabulaires de niveau de compatibilité 1400) :
    - DirectQuery est disponible pour SQL Oracle et pour Teradata si l’utilisateur a installé les pilotes des tiers
    - Ajouter des colonnes par exemple dans PowerQuery
    - Options d’accès aux données dans les modèles 1400 (propriétés de niveau modèle utilisées par le moteur M)
        - Activer la combinaison rapide (la valeur par défaut est false ; quand la valeur est true, le moteur de mashup ignore les niveaux de confidentialité des sources de données lors de la combinaison des données)
        - Activer les redirections héritées (la valeur par défaut est false ; quand la valeur est true, le moteur de mashup suit les redirections HTTP qui sont potentiellement non sécurisées.  Par exemple, une redirection d’un URI HTTPS vers un URI HTTP)  
        - Retourner les valeurs d’erreur comme Null (la valeur par défaut est false ; quand la valeur est true, les erreurs de niveau cellule sont retournées comme Null. Quand la valeur est false, une exception est levée si une cellule contient une erreur)  
    - Sources de données supplémentaires (sources de données fichiers) avec PowerQuery
        - Excel 
        - Texte/CSV 
        - Xml 
        - JSON 
        - Dossier 
        - Base de données Access 
        - Stockage d'objets blob d'Azure 
    - Interface utilisateur de PowerQuery localisée
- Fenêtre de l’outil Éditeur DAX
    - Expérience améliorée de l’édition DAX pour les mesures, les colonnes calculées et les expressions de lignes de détails, disponibles via le menu Affichage, Autres fenêtres dans SSDT
    - Améliorations apportées à l’analyseur\Intellisense DAX


**Projets RS :**
- Les contrôles RVC intégrable sont désormais disponibles pour la prise en charge de SSRS 2016

### <a name="bug-fixes"></a>Correctifs de bogues
**Projets AS :**
- Correction de la priorité du modèle pour les projets BI pour qu’ils ne s’affichent plus en haut des catégories Nouveaux projets dans VS
- Correction d’un incident VS susceptible de survenir rarement lors de l’ouverture de la solution SSIS, SSAS ou SSRS
- Tabulaire : Améliorations et correctifs de performances pour l’analyse et la barre de formules DAX.
- Tabulaire : L’Explorateur de modèles tabulaires ne sera plus visible si aucun projet tabulaire SSAS n’est ouvert.
- Multidimensionnel : Résolution d’un problème où la boîte de dialogue de traitement était inutilisable sur les machines avec écran haute résolution.
- Tabulaire : Résolution d’un problème d’erreur de SSDT à l’ouverture de projets BI quand SSMS est déjà ouvert. [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3100900/ssdt-faults-when-opening-any-bi-project-when-ssms-is-already-open)
- Tabulaire : Résolution d’un problème où les hiérarchies n’étaient pas correctement enregistrées dans le fichier BIM dans un modèle 1103. [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3105222/vs-2015-ssdt)
- Tabulaire : Résolution d’un problème où le mode Espace de travail intégré était autorisé sur les ordinateurs 32 bits alors qu’il n’est pas pris en charge.
- Tabulaire : Résolution d’un problème où le fait de cliquer sur quoi que ce soit en mode de semi-sélection (par exemple en tapant une expression DAX mais en cliquant sur une mesure) peut provoquer des blocages.
- Tabulaire : Résolution d’un problème où l’Assistant Déploiement réinitialisait la propriété .Name du modèle à « Modèle ». [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3107018/ssas-deployment-wizard-resets-modelname-to-model)
- Tabulaire : Résolution d’un problème où la sélection d’une hiérarchie dans TME affichait des propriétés même si la vue Diagramme n’était pas sélectionnée.
- Tabulaire : Résolution d’un problème où l’opération coller dans la barre de formule DAX collait les images ou d’autres contenus au lieu du texte lors d’une opération coller à partir de certaines applications.
- Tabulaire : Résolution d’un problème où certains anciens modèles dans 1103 ne pouvaient pas être ouverts en raison de la présence de mesures avec une définition spécifique.
- Tabulaire : Résolution d’un problème où les sessions XEvent ne pouvaient pas être supprimées.
- Correction d’un problème lié à l’échec de la tentative de génération de fichiers « smproj » avec devenv.com
- Correction d’un problème lié à la finalisation trop fréquente des modifications de texte lors de l’utilisation de l’éditeur IME coréen dans les titres d’onglet de feuille de modèle tabulaire AS
- Correction d’un problème lié au dysfonctionnement de la fonction intellisense pour l’affichage de colonnes d’autres tables
- Amélioration de l’importation de projet tabulaire AS à partir de la boîte de dialogue de base de données par le tri de la liste des bases de données AS
- Correction d’un problème survenant lors de la création de tables calculées dans le modèle tabulaire AS où les tables ne sont pas répertoriées en tant qu’objets suggérés dans l’expression
- Correction d’un problème lié aux modèles AS 1400 d’aperçu lors de leur tentative d’ouverture à l’aide du serveur d’espace de travail intégré après affichage du code
- Correction d’un problème qui empêchait, dans certains cas, le fonctionnement correct de certaines sources de données (sans prise en charge du catalogue initial) 
- L’Assistant de déploiement doit appliquer les modifications aux partitions de tables calculées même lorsque l’option de conservation des partitions est activée
- Correction d’un problème où la boîte de dialogue Propriétés avancées de la connexion AS existante n’affiche pas la liste complète tant qu’elle n’est pas resélectionnée
- Correction de quelques problèmes avec les chaînes tronquées de l’interface utilisateur qui apparaissaient dans certaines versions localisées
- Correction de plusieurs problèmes avec l’intégration de PowerQuery dans les modèles tabulaires Analysis Services de niveau de compatibilité 1400
- Correction d’un problème avec les modèles de style de l’Assistant Rapport qui ne s’affichaient pas correctement
- Correction d’un problème avec l’Assistant Rapport qui pouvait aboutir à des paramètres de source de données incorrects lors du passage de SQL à AS
- Correction d’un problème provoquant l’échec de la génération des projets Analysis Services (tabulaire) à partir de la ligne de commande (devenv.com\exe)
- Correction d’un problème avec l’analyseur de mesure DAX dans l’affichage de la couleur correcte du texte mis en surbrillance lors de la présence de lettres au commencement avant : =
- Correction d’un problème de déclenchement d’une ObjectRefException si les chemins étaient trop longs pour Afficher tous les fichiers pour Projet tabulaire en mode Espace de travail intégré
- Correction d’un problème avec le Concepteur de Source de données pour le fournisseur de données du client Compact 4.0 où il apparaissait indisponible
- Correction d’un problème qui provoquait une erreur lors de la navigation dans un modèle d’exploration de données AS dans VS2017
- Correction d’un problème dans un modèle multidimensionnel AS dans VS2017 où le diagramme de vue de source de données cesse l’affichage après la modification des vues puis lève une exception
- Correction d’un problème dans l’aperçu des rapports avec un échec de connexion à AS dans VS2017
 

**Projets RS :**
- Correction d’un problème lié à la réduction de l’affichage de l’arborescence des paramètres, des sources de données et des jeux de données lorsque la plupart des modifications ont été effectuées survenant, lors de la conception de rapports dans SSDT 
- Résolution d’un problème où l’opération Enregistrer enregistrait la version de RDL et non pas la version la plus récente.
- Résolution d’un problème où SSDT RS sauvegardait des fichiers alors que la sauvegarde était désactivée et de plusieurs autres problèmes.
- Résolution d’un problème dans le Générateur de rapports où une erreur était affichée quand l’utilisateur cliquait sur « Fractionner les cellules ». [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3101818/ssdt-2015-ssrs-designer-error-by-matrix-cell-split)
- Résolution d’un problème où la mise en cache pouvait entraîner des données incorrectes dans un rapport. [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/3102158/ssdtbi-14-0-60812-report-preview-data-is-frequently-wrong-due-to-bad-caching)

**Projets IS :**
- Résolution d’un problème où le paramètre run64bitruntime n’était pas conservé.
- Résolution d’un problème où DataViewer n’enregistrait pas les colonnes affichées.
- Résolution d’un problème où Parties de package masque les annotations. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3106624/package-parts-hide-annotations)
- Résolution d’un problème où Parties de package ignore les dispositions et les annotations des flux de données. [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3109241/package-parts-discard-data-flow-layouts-and-annotations)
- Résolution d’un problème où SSDT se bloque lors de l’importation d’un projet depuis SQL Server.
- Correction d’un problème où la valeur par défaut de TimeoutInMinutes pour les tâches du système de fichiers Hadoop était définie sur 10 après l’ouverture d’un package SSIS enregistré et à l’exécution.

**Projets de base de données :**
- SSDT DACPAC : réinsertion du paramètre de déploiement/ajout pour IgnoreColumnOrder [Article de Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/1221587/ssdt-dacpac-deploy-add-setting-back-in-for-ignorecolumnorder)
- Échec de compilation en cas d’utilisation de STRING_SPLIT [Article de Microsoft Connect](http://connect.microsoft.com/SQLServer/feedback/details/2906200/ssdt-failing-to-compile-if-string-split-is-used)
- Correction du problème lié à l’accès de DeploymentContributors au modèle public, sans que le schéma de sauvegarde ait été initialisé [Problème de Github](https://github.com/Microsoft/DACExtensions/issues/8)
- Correctif temporel DacFx pour le positionnement de FILEGROUP
- Correction de l’erreur « Référence non résolue » pour les synonymes externes. 
- Always Encrypted : le chiffrement en ligne ne désactive pas le suivi des modifications lors de l’annulation et ne fonctionne pas correctement si le suivi des modifications n’a pas été désactivé avant le démarrage du chiffrement


## <a name="ssdt-165-supports-up-to-sql-server-2016"></a>SSDT 16.5 (prend en charge jusqu’à SQL Server 2016)
Date de publication : 20 octobre 2016

Numéro de build : 14.0.61021.0

**Nouveautés**


### <a name="connection-improvements"></a>Améliorations des connexions

* La nouvelle zone de recherche de l’onglet **Parcourir** vous permet de filtrer les serveurs locaux, les serveurs réseau et les bases de données SQL Azure. Si ces listes contiennent un grand nombre de serveurs ou de bases de données, cela peut être utile.
* L’onglet **Historique** propose des options de menu contextuel permettant d’épingler/désépingler des favoris, ainsi qu’une nouvelle option pour supprimer des connexions de l’historique.

### <a name="sqlpackage-and-dacfx-api-improvements"></a>Améliorations des API SqlPackage et DacFx

Avec les API SqlPackage.exe et DacFx, vous pouvez maintenant générer un rapport de déploiement et un script de déploiement, puis les publier dans une base de données en une seule opération. Cela fait gagner du temps à toute personne souhaitant conserver un rapport des éléments qui ont été publiés pendant un déploiement. Autre avantage dans les scénarios Azure, des scripts distincts sont créés pour la base de données MASTER et la base de donné cible de déploiement. Jusqu’à maintenant, un seul script était créé ce qui était inutile pour les déploiements répétés.

Deux nouveaux arguments ont été ajoutés aux actions Publier et Script de SqlPackage.

* DeployScriptPath (nom court : dsp). Il s’agit d’un chemin facultatif où écrire le script de déploiement. Dans un déploiement Azure, s’il existe des commandes TSQL pour créer et modifier la base de données, un script principal est écrit dans le même chemin, mais le nom du fichier de sortie est « NomFichier_Master.sql ».
* DeployReportPath (nom court : drp). Il s’agit d’un chemin facultatif où écrire le rapport de déploiement.

Notez que pour l’action Script, vous devez utiliser au choix les arguments de chemin de sortie existants ou les nouveaux arguments pour les scripts/rapports, mais pas les deux.

Exemple d’utilisation :

**Action Publier**

```Sqlpackage.exe /a:Publish /tsn:(localdb)\ProjectsV13 /tdn:MyDatabase /deployscriptpath:”My\DeployScript.sql” /deployreportpath:”My\DeployReport.xml”```

**Action Script**

```Sqlpackage.exe /a:Script /tsn:(localdb)\ProjectsV13 /tdn:MyDatabase /deployscriptpath:”My\DeployScript.sql” /deployreportpath:”My\DeployReport.xml”```

Dans DacFx, deux nouvelles API ont été ajoutées : DacServices.Publish() et DacServices.Script(). Celles-ci prennent également en charge les actions de publication + script + rapport dans une même opération. Exemple d’utilisation :

```
DacServices service = new DacServices(connectionString);
using(DacPackage package = DacPackage.Load(@"C:\My\db.dacpac")) {
var options = new PublishOptions() {
    GenerateDeploymentScript = true, // Should a deployment script be created?
    GenerateDeploymentReport = true, // Should an xml deploy report be created?
    DatabaseScriptPath = @"C:\My\OutputScript.sql", // optional path to save script to
    MasterDbScriptPath = @"C:\My\OutputScript_Master.sql", // optional path to save master script to
    DeployOptions = new DacDeployOptions()
};

// Call publish and receive deployment script & report in the results
PublishResult result = service.Publish(package, "TargetDb", options);
Console.WriteLine(result.DatabaseScript);
Console.WriteLine(result.MasterDbScript);
Console.WriteLine(result.DeploymentReport);

// Call script and receive deployment script & report in results
result = service.Script(package, "TargetDb", options);
Console.WriteLine(result.DatabaseScript);
Console.WriteLine(result.MasterDbScript);
Console.WriteLine(result.DeploymentReport);
```

**Analysis Services & Reporting Services**

Amélioration des performances de l’analyseur DAX du concepteur tabulaire SSAS lors de l’utilisation d’expressions DAX longues.
Pour plus d’informations, lisez le [billet du blog Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2016/09/20/introducing-integrated-workspace-mode-for-sql-server-data-tools-for-analysis-services-tabular-projects-ssdt-tabular/).

### <a name="fixed--improved-this-month"></a>Corrections et améliorations du mois

**Outils de base de données**

* [Bogue Connect 3055711](https://connect.microsoft.com/SQLServer/feedback/details/3055711/columns-cannot-be-selected-from-cross-apply-openjson-with-explicit-schema) : impossible de sélectionner des colonnes depuis CROSS APPLY OPENJSON avec un schéma explicite
* Correction : Problème avec les index de tables d’historique auto-générés, où DacFx supprimait l’index lors du redéploiement
* Correction : Problème avec l’analyseur de lot DacFx qui n’analysait pas le caractère crochet dans une séquence d’échappement ’]’, ce qui conduisait à l’échec de la publication
* Amélioration : SqlPackage comprend des descriptions de chaque action dans l’aide
* Correction : L’option « Mémoriser le mot de passe » de la boîte de dialogue de connexion n’était pas conservée lors de la modification des options avancées et d’une chaîne de connexion enregistrée dans Publier, Comparaison de schémas ou d’autres fichiers
* Correction : Pour les connexions affichées dans l’onglet Historique avec IntegratedAuthentication = true, le champ Authentification était vide dans les propriétés de la connexion. Maintenant, il indique « Authentification Windows » comme il se doit
* Correction : Les modifications apportées aux paramètres Intellisense des outils SQL Server sous Outils-> Options-> Éditeur de texte n’étaient pas conservées
* Amélioration : Le bouton Épingler/Désépingler dans l’onglet Historique de la boîte de dialogue de connexion est désormais plus compact, ce qui rend moins probable l’affichage d’une barre de défilement
* Correction : Plusieurs problèmes d’accessibilité ont été résolus dans la boîte de dialogue de connexion.

**Analysis Services & Reporting Services**

* Correction d’un problème dans le concepteur tabulaire SSDT AS où le fait de cliquer sur le curseur de la barre de défilement dans la grille de données générait un blocage dans certaines situations
* Correction d’un problème où l’option permettant de se connecter en tant qu’utilisateur actuel dans le concepteur tabulaire SSDT AS n’était pas disponible
* Correction d’un problème dans le concepteur tabulaire SSDT AS où si vous développiez trop la barre de formule, la réouverture du projet était impossible
* Correction d’un incident dans le concepteur tabulaire SSDT AS qui pouvait se produire quand vous appuyiez sur une touche alors que l’onglet de table était sélectionné
* Correction d’un problème dans les projets SSDT AS où Analyse dans Excel ne se connectait pas aux versions de bas niveau du serveur AS

**Integration Services**

* Correction du bogue Connect [1608896](https://connect.microsoft.com/SQLServer/feedback/details/1608896/move-multiple-integration-service-package-tasks) : déplacer plusieurs tâches du package Integration Services





## <a name="ssdt-164-for-sql-server-2016"></a>SSDT 16.4 (pour SQL Server 2016)
Date de publication : 20 septembre 2016

Numéro de build : 14.0.60918

**Nouveautés**

La comparaison de schémas est maintenant prise en charge dans SqlPackage.exe et l’API d’infrastructure d’application de couche Données (DacFx). Pour plus d’informations, consultez [Schema Compare in SqlPackage and the Data-Tier Application Framework](https://blogs.msdn.microsoft.com/ssdt/2016/09/20/schema-compare-in-sqlpackage-and-the-data-tier-application-framework-dacfx/).

**Analysis Services – Mode Espace de travail intégré pour le modèle tabulaire SSDT (SSAS)**

Le modèle tabulaire SSDT comprend désormais une instance SSAS interne qu’il démarre automatiquement en arrière-plan si le mode Espace de travail intégré est activé afin que vous puissiez ajouter et afficher des tables, des colonnes et des données dans le générateur de modèles sans avoir à fournir une instance de serveur d’espace de travail externe. Le mode d’espace de travail intégré ne modifie pas le fonctionnement du modèle tabulaire SSDT avec une base de données et un serveur d’espace de travail. Le changement réside dans l’emplacement où le modèle tabulaire SSDT héberge la base de données d’espace de travail. Pour activer le mode Espace de travail intégré, sélectionnez l’option Espace de travail intégré dans la boîte de dialogue Générateur de modèles tabulaires qui s’affiche lors de la création d’un projet tabulaire. Pour les projets tabulaires existants qui utilisent un serveur d’espace de travail explicite, vous pouvez basculer en mode Espace de travail intégré en définissant le paramètre Mode Espace de travail intégré avec la valeur True dans la fenêtre Propriétés qui s’affiche lorsque vous sélectionnez le fichier Model.bim dans l’Explorateur de solutions. Pour plus d’informations, consultez le [billet de blog Analysis Services](https://blogs.msdn.microsoft.com/analysisservices/2016/09/20/introducing-integrated-workspace-mode-for-sql-server-data-tools-for-analysis-services-tabular-projects-ssdt-tabular/).

**Mises à jour et corrections**
**Outils de base de données :**

- [Problème Connect 3087775](https://connect.microsoft.com/SQLServer/feedback/details/3087775) : Tables temporelles rompues dans Visual Studio Data Tools (mise à jour 14.0.60629.0 de juillet) : « La valeur ne peut pas être Null. Nom du paramètre : reportedElement »
- [Problème Connect 1026648](https://connect.microsoft.com/SQLServer/feedback/details/1026648) : IsPersistedNullable est différent dans la comparaison de SSDT
- [Problème Connect 2054735](https://connect.microsoft.com/SQLServer/feedback/details/2054735) : L’identité est réinitialisée lors de l’importation d’un fichier BACPAC
- [Problème Connect 2900167](https://connect.microsoft.com/SQLServer/feedback/details/2900167) : L’exécution de tests unitaires SSDT laisse des fichiers temporaires
- [Problème Connect 1807712](https://connect.microsoft.com/SQLServer/feedback/details/1807712) : Rupture de compatibilité descendante – AppLocal et Nugetization

**Analysis Services & Reporting Services**

* Correction d’un problème dans SSDT où des fenêtres contextuelles de conseil sur les erreurs s’affichaient lors de la modification des colonnes calculées DAX pour DirectQuery.
* Correction d’un problème dans la grille tabulaire SSDT AS où l’icône de KPI ne s’affichait pas dans la grille de mesure quand le facteur d’échelle Windows était défini avec une haute résolution de plus de 200 %.
* Correction d’un problème dans SSDT AS où le collage des données d’une grande table pouvait entraîner le blocage du projet tabulaire.
* Correction d’un problème dans l’éditeur de modèle tabulaire SSDT AS afin de marquer le modèle comme devant enregistrer les modifications lors du renommage d’une connexion.
* Correction d’un problème dans les projets tabulaires SSDT AS où il était impossible de redimensionner la largeur des colonnes dans la boîte de dialogue de gestion des relations.
* Correction d’un problème dans les modèles tabulaires SSDT AS de niveau 1200 où le collage des données depuis Excel avec des paramètres régionaux comme Allemand ne traitait pas correctement la virgule comme séparateur décimal.
* Correction d’un problème dans les projets SSDT AS où des jeux d’icônes de KPI pouvaient générer une erreur « Impossible de récupérer les données de cet élément visuel ».
* Correction d’un problème pour ancrer correctement la boîte de dialogue des propriétés de projet SSDT AS lors du redimensionnement à une résolution élevée.
* Correction d’un problème dans les projets SSDT AS qui peut avoir provoqué une erreur de mise à niveau de certains modèles avec les tables collées.
* Correction d’un problème dans SSDT AS où le collage de lignes de feuille entière depuis Excel était très lent et créait de nombreuses colonnes inutiles.
* Correction d’un problème dans SSDT AS où l’analyse et la sélection de grandes expressions DataTable statiques étaient très lentes ou se bloquaient.
* Correction d’un problème dans SSDT AS afin d’ajouter des mesures et des valeurs de KPI à la perspective actuelle sélectionnée dans l’éditeur.
* Correction d’un problème dans SSDT où l’importation de données dans un projet AS depuis SQL Azure ne prenait pas en charge les types de schémas autres que « dbo ».



## <a name="ssdt-163-for-sql-server-2016"></a>SSDT 16.3 (pour SQL Server 2016)
Date de publication : 15 août 2016

Numéro de build de : 14.0.60812.0  

**Nouveautés**

- **Gestion et numérotation des versions :** Les versions sont maintenant nommées avec des chiffres et non plus avec des mois. Cette initiative s’inscrit dans la nouvelle politique SSMS et simplifie les cas où plusieurs versions ou correctifs sont publiés au cours d’un même mois. Cette version est la 16.3, autrement dit la troisième mise à jour après la publication de la version RTM. Les correctifs seront numérotés 16.3.1 et ainsi de suite jusqu’à notre prochaine mise à jour (prévue le mois prochain) qui sera la version 16.4.
- **Analysis Services – Explorateur de modèles tabulaires :** L’Explorateur de modèles tabulaires vous permet de naviguer facilement dans les différents objets de métadonnées d’un modèle, tels que les sources de données, les tables, les mesures et les relations. Il est implémenté comme fenêtre d’outils distincte que vous pouvez afficher en ouvrant le menu Affichage dans Visual Studio, en pointant sur Autres fenêtres, puis en cliquant sur Explorateur de modèles tabulaires. L’Explorateur de modèles tabulaires s’affiche par défaut dans la zone Explorateur de solutions sous un onglet distinct. L’Explorateur de modèles tabulaires organise les objets de métadonnées dans une arborescence qui ressemble beaucoup au schéma d’un modèle tabulaire 1200 et propose beaucoup d’autres nouvelles fonctionnalités.
- **Outils de base de données – Always Encrypted** : Cette version propose de nouvelles boîtes de dialogue de [gestion des clés Always Encrypted](https://msdn.microsoft.com/library/mt708953.aspx) permettant de facilement ajouter des clés principales de colonne ou des clés de chiffrement de colonne à votre projet de base de données ou une base de données active dans l’Explorateur d’objets SQL Server. Cette version prend en charge les certificats dans le magasin de certificats Windows. Dans les versions à venir, Azure Key Vault et les fournisseurs CNG seront pris en charge.
    - Quand vous créez une clé principale de colonne ou une clé de chiffrement de colonne, vous pouvez constater que les modifications ne sont pas immédiatement répercutées dans l’Explorateur d’objets SQL Server après avoir cliqué sur Mettre à jour la base de données. Pour contourner ce problème, actualisez le nœud de base de données dans l’Explorateur d’objets SQL Server.
    - Si vous essayez de chiffrer une colonne dans une table contenant des données à partir de l’Explorateur d’objets SQL Server, vous risquez d’échouer. Actuellement, cette fonctionnalité est prise en charge uniquement dans les projets de base de données SSDT et SSMS. La prise en charge de l’Explorateur d’objets SQL Server est prévue dans une version ultérieure.


**Mises à jour et corrections**
* **Outils de base de données :**
    - **SSDT :**
        - Bogue Connect 1898001 [Correction d’un problème de description de colonne avec une limitation à 128 caractères](https://connect.microsoft.com/SQLServer/feedback/details/1898001/column-description-limited-to-128-characters).
        - Correction d’un problème où la publication d’une base de données à partir de Visual Studio n’appliquait pas la propriété DatabaseServiceObjective dans le profil de publication xml.
        - Bogue Connect 2900167 [Correction d’un problème de test unitaire qui laissait des fichiers temporaires](http://connect.microsoft.com/SQLServer/feedback/details/2900167/running-ssdt-unit-tests-leaves-temp-files-behind).
        - Correction d’un problème où la zone de liste modifiable Période de rétention dans les paramètres de base de données était tronquée.
        - Correction d’un problème où un ancien mot de passe vide dans les propriétés de projet SQL CLR n’était pas vérifié lors de la modification du mot de passe.
    - **DACFx :**
        - Correction d’un problème où le niveau de compatibilité de DACFx n’était pas mis à jour pour l’erreur SqlAzureV12.
        - Correction d’un problème où la propriété IsAutoGeneratedHistoryTable était exclue sans raison de la comparaison du modèle.

- **Analysis Services & Reporting Services**
    - **SSDT :**
        - Correction d’un problème où il était impossible d’enregistrer le modèle tabulaire lorsque la connexion au serveur était perdue.
        - Correction d’un problème où SSDT cessait de répondre en raison d’un possible problème de boucle infinie dans AS.
        - Correction d’un problème d’expression DAX qui conduisait à des comportements incohérents selon la façon dont vous validiez l’expression.
        - Correction d’un problème de blocage de VS lors de la création de KPI.
        - Correction d’un problème qui générait des rapports non valides pour SQL Server 2008 R2, 2012 et 2014.
        - Correction d’un problème d’ordre hiérarchique qui générait une erreur de boucle infinie pour un projet .dwpro.
        - Correction d’un problème RDL de RS où le passage à une version antérieure de RDL nécessitait une regénération complète qui entraînait une certaine confusion chez l’utilisateur.
        - Correction d’un problème de KPI où Masquer dans les outils clients n’avait aucun effet.
        

 
  
## <a name="ssdt-july-for-sql-server-2016"></a>SSDT Juillet (pour SQL Server 2016)  
Date de publication : 30 juin 2016  
  
Numéro de build : 14.0.60629.0  
  
**Nouveautés**  
* **Prise en charge d’Always Encrypted :** Pour les bases de données qui contiennent des colonnes Always Encrypted, cette version prend en charge Always Encrypted via nos API principales et notre outil de ligne de commande (SqlPackage.exe). Vous pouvez créer et publier des projets de base de données avec prise en charge complète de toutes les fonctionnalités Always Encrypted.  
* **Prise en charge améliorée des tables temporelles :** Expérience simplifiée avec suppression de la liaison des tables temporelles avant les changements, puis rétablissement de la liaison une fois les changements apportés. Cela signifie que les tables temporelles ont une parité avec d’autres types de table (standard, en mémoire) en terme d’opérations prises en charge. 
* **Modifications de SqlPackage.exe et de l’installation :** Modifications en vue d’isoler SSDT du moteur SQL Server et des mises à jour SSMS. Pour plus d’informations, consultez [Changes to SSDT and SqlPackage.exe installation and updates](https://blogs.msdn.microsoft.com/ssdt/2016/06/30/changes-to-ssdt-and-sqlpackage-exe-installation-and-updates/).

 

**Mises à jour et corrections**
* **Outils de base de données :**
    * À partir de maintenant, SSDT ne désactivera jamais TDE (Transparent Data Encryption) sur une base de données. Avant, si l’option de chiffrement par défaut dans les paramètres de base de données d’un projet était désactivée, le chiffrement l’était aussi. Avec ce correctif, le chiffrement peut être activé mais jamais désactivé au cours de la publication. 
    * Augmentation du nombre de tentatives et de la résilience pour les connexions de base de données SQL Azure au cours de la connexion initiale.
    * Si le groupe de fichiers par défaut n’est pas PRIMARY, Importer/Publier dans Azure V12 échouait. Maintenant ce paramètre est ignoré lors de la publication.
    * Correction d’un problème où lors de l’exportation d’une base de données contenant un objet avec Identificateur entre guillemets activé, la validation de l’exportation pouvait dans certains cas échouer.
    * Correction d’un problème où l’option TEXTIMAGE_ON était ajoutée lors de la création de tables Hekaton alors qu’elle n’était pas autorisée.
    * Correction d’un problème où l’exportation d’une grande quantité de données prenait beaucoup de temps en raison de l’écriture dans le fichier model.xml une fois la phase de données terminée, ce qui provoquait le réécriture du fichier .bacpac.
    * Correction d’un problème où les utilisateurs ne figuraient pas dans le dossier Sécurité des connexions APS et DW Azure SQL.


 * **Analysis Services & Reporting Services :**
    * Correction d’un problème SxS avec le fournisseur OLEDB MSOLAP où seul le fournisseur 32 bits était installé, ce qui impactait Excel 2016 64 bits lors de la connexion à SQL Server 2014 (ne se reproduisait pas avec les installations ClickOnce à partir d’Office365, seulement avec l’installation du MSI Excel).
    * Correction d’un problème concernant un « corner case » que nous avons renforcé quand le modèle AS est mis à niveau avec des tables collées de niveau de compatibilité 1103 à 1200 pouvant donner l’erreur « La relation utilise un ID de colonne non valide ».
    * Correction d’un problème SxS où SSDT-BI 2013, installé sur le même ordinateur, ne pouvait plus importer des données dans le modèle Analysis Services après la désinstallation de SSDT 2015 (paramètre du Registre partagé de cartouches).
    * Amélioration de la robustesse pour résoudre les problèmes/blocages lorsque la connexion au moteur AS est perdue (par exemple, SSDT laissé ouvert pendant la nuit et serveur AS recyclé ou d’autres cas où la connexion est perdue temporairement). 
    * Correction de problèmes liés à l’ouverture de boîtes de dialogue sur des écrans autres que Visual Studio dans le cas d’écrans multiples. 
    * Prise en charge corrigée/activée du collage à partir de tables HTML (données de grille) dans des tables collées du modèle AS. 
    * Correction d’un problème d’échec de mise à niveau d’une table collée vide vers 1200 (utilisée uniquement comme table de conteneur pour les mesures). 
    * Correction d’un problème de mise à niveau d’un modèle tabulaire AS avec des tables collées vers 1200 pour contourner un problème de moteur AS avec des CalcTables (utilisés pour les tables collées dans 1200) et effectuer un processus complet sur les nouvelles tables calculées après la mise à niveau. 
    * Correction d’un problème où l’annulation de la création d’une nouvelle table calculée de modèle AS 1200 avec une expression DAX incomplète pouvait causer un blocage. 
    * Correction d’un problème lors de l’importation du modèle 1200 du serveur AS dans le projet SSDT AS lorsque le nom de base de données et le nom de table étaient identiques. 
    * Correction d’un problème concernant la modification d’une mesure de KPI dans le modèle tabulaire 1103. 
    * Résolution d’une exception Référence d’objet non définie lorsqu’une mesure de KPI est collée dans la grille d’un modèle 1200 Analysis Services. 
    * Correction d’un problème où une colonne d’une table calculée ne pouvait pas être supprimée de la vue de diagramme dans les modèles 1200. 
    * Résolution d’une exception Référence d’objet non définie lors de l’affichage des propriétés du fichier projet model.bim en mode Code. 
    * Correction d’un problème où le collage de données dans la grille de modèle Analysis Services pour créer une table collée générait des valeurs incorrectes dans les paramètres régionaux internationaux utilisant la virgule comme séparateur décimal. 
    * Correction d’un problème lors de l’ouverture d’un projet Reporting Services 2008 dans SSDT en choisissant de ne pas le mettre à niveau. 
    * Correction d’un problème dans l’IU des tables calculées dans les modèles de niveau de compatibilité 1200 en cas d’utilisation de la mise en forme par défaut pour le type de colonne afin d’autoriser la modification du type de mise en forme à partir de l’IU. 
    

## <a name="ssdt-june-for-sql-server-2016"></a>SSDT Juin (pour SQL Server 2016)  
Date de publication : 1 juin 2016  
  
Numéro de build : 14.0.60525.0 

La version SSDT GA (General Availability) a été publiée. La mise à jour SSDT GA de juin 2016 prend en charge les dernières mises à jour de SQL Server 2016 RTM et diverses résolutions de bogues. Pour plus d’informations, consultez [SQL Server Data Tools GA update for June 2016](https://blogs.msdn.microsoft.com/ssdt/2016/06/01/sql-server-data-tools-ga-update-for-june-2016/).

      

## <a name="ssdt-april-for-sql-server-2016-rc3"></a>SSDT Avril (pour SQL Server 2016 RC3)  
Date de publication : 15 avril 2016  
  
Numéro de build : 14.0.60413.0  
  
**Base de données SQL Server**  
* **Prise en charge d’Always Encrypted :** Pour les bases de données contenant des colonnes Always Encrypted, SSDT et DacFx autorisent l’affichage et la modification de ces bases de données, ainsi que la publication dans ces bases de données à partir d’un projet de base de données. Notez que la prise en charge de la modification de colonnes avec chiffrement de colonne sera proposée dans une version ultérieure.  
* **Boîte de dialogue de connexion et Explorateur d’objets SQL Server :** plusieurs corrections et améliorations.  
    * La page Détails répertoriant les propriétés de connexion avancées a été repensée de manière à afficher la chaîne de connexion complète dans une zone multiligne et à améliorer la prise en charge sur les ordinateurs haute résolution.  
    * Nous avons rétabli la boîte de dialogue d’erreur traditionnelle présentant les erreurs de connexion détaillées. Les messages d’erreur plus clairs et l’arborescence des appels de procédure facilitent le diagnostic des problèmes de connexion ; les administrateurs de base de données ou le Support technique et Service clientèle Microsoft pouvant obtenir les informations dont ils ont besoin pour diagnostiquer vos problèmes.  
    * Pour les utilisateurs avec des autorisations minimales, nous avons résolu un certain nombre de problèmes liés à l’affichage de la liste des bases de données dans la boîte de dialogue de connexion et l’Explorateur d’objets SQL Server, à l’affichage du dossier Sécurité et plus encore.  
    * Les performances des bases de données SQL Azure lors du développement du nœud de bases de données pour répertorier toutes les bases de données ont été améliorées.  
* **Programme d’installation de SSDT :**  
    * Correction du problème où .Net était téléchargé lors de la désinstallation.  
    * La taille du programme d’installation est maintenant correctement définie sur les ordinateurs haute résolution.  
    * Suppression de la gestion de versions bloquant l’installation de SSDT si une version plus récente de SQL Server est présente.  
    * Comparaison de schémas : correction d’un problème de performance où l’activation/désactivation de plusieurs éléments prenait beaucoup de temps dans Visual Studio.  
    * Prise en charge de l’utilisation de LocalDN 2014 sur les ordinateurs x86, car il n’existe aucune version x86 de SQL Server 2016.  
* **Build et déploiement :**  
    * Correction du problème où les colonnes calculées n’étaient pas prises en charge sur les tables temporelles.  
    * L’option « Exécuter le script de déploiement en mode mono-utilisateur » est ignorée lors du déploiement vers Azure V12 car elle n’est pas pris en charge dans les scénarios de cloud.  
  
  
## <a name="ssdt-hotfix-for-sql-server-2016-rc2"></a>Correctif SSDT (pour SQL Server 2016 RC2)  
Date de publication : 5 avril 2016  
  
Numéro de build : 14.0.60329.0  
  
Cette build contient un correctif pour la version de SSDT proposant des fonctionnalités pour SQL Server Integration Services. La build 14.0.60316.0 peut également être utilisée avec Analysis Services et Reporting Services dans SQL Server 2016.   
  
Pour obtenir ce correctif, utilisez les [liens de téléchargement de ce billet de blog](https://blogs.msdn.microsoft.com/ssdt/2016/04/05/ssdt-preview-update-rc2/).  
  
Si vous êtes développeur d’états et créez de nouveaux rapports à l’aide de cette build de SSDT, [lisez le problème connu et la solution de contournement](https://blogs.msdn.microsoft.com/ssdt/2016/04/05/ssdt-preview-update-rc2/) concernant un problème temporaire dans les rapports SSRS ne se produisant que dans ce correctif logiciel.  
  
## <a name="ssdt-hotfix-for-sql-server-2016-rc0"></a>Correctif SSDT (pour SQL Server 2016 RC0)  
Date de publication : 18 mars 2016  
  
Numéro de build : 14.0.60316.0  
  
Cette build contient un correctif pour la version de SSDT proposant des fonctionnalités pour SQL Server 2016 RC0. Il n’existe aucune version RC1 de SSDT pour l’instant. La build 14.0.60316.0 peut être utilisée avec les versions RC0 ou RC1 de SQL Server 2016.  
      
## <a name="ssdt-february-2016-preview-for-sql-server-2016-rc0"></a>Préversion de SSDT de février 2016 (pour SQL Server 2016 RC0)  
Date de publication : 7 mars 2016  
  
Numéro de build : 14.0.60305.0  
  
-   **Modèles de projet SQL Server**  
  
    Aucune annonce pour cette préversion de SSDT. Consultez [Nouveautés de SQL Server 2016 (moteur de base de données)](https://msdn.microsoft.com/library/bb510411.aspx) pour en savoir plus sur les autres fonctionnalités de cette version.  
  
-   **Modèles de projet de package SSIS**  
  
    Le concepteur SSIS crée et gère les packages pour SQL Server 2016, 2014 ou 2012. Nouveaux modèles renommés en tant que parties. Le connecteur Hadoop SSIS prend en charge le format ORC. Pour plus d’informations, consultez [Nouveautés d’Integration Services dans SQL Server 2016](https://msdn.microsoft.com/library/bb522534.aspx).  
  
-   **Modèles de projet SSAS (projets de modèles tabulaires)**  
  
    Cette mise à jour mensuelle d’Analysis Services prend en charge l’affichage des dossiers des modèles tabulaires et tous les modèles créés avec le nouveau niveau de compatibilité SQL Server 2016 sont maintenant pris en charge dans les packages SSIS. Pour plus d’informations, consultez [What’s New in Analysis Services (billet de blog)](http://blogs.msdn.com/b/analysisservices/archive/2016/01/28/what-s-new-for-sql-server-2016-analysis-services-in-ctp3-3.aspx).  
  
-   **Modèles de projet de rapport SSRS**  
  
    Aucune annonce pour cette préversion de SSDT. Pour plus d’information sur les autres fonctionnalités de cette version, consultez [Nouveautés de SQL Server Reporting Services (SSRS)](https://msdn.microsoft.com/library/ms170438.aspx).  
  
## <a name="ssdt-january-2016-preview"></a>Préversion de janvier 2016 de SSDT  
Date de publication : 4 février 2016  
  
Numéro de build : 14.0.60203.0  
  
-   **Modèles de projet SQL Server**  
  
    Aucune annonce pour cette préversion de SSDT. Pour plus d’information sur les autres fonctionnalités de cette version CTP, consultez [Nouveautés de SQL Server 2016 (moteur de base de données)](https://msdn.microsoft.com/library/bb510411.aspx).  
  
-   **Modèles de projet de package SSIS**  
  
    Ajoute la prise en charge des composants sources et de destination ODBC, une tâche de contrôle CDC,  
      un composant source et de fractionnement CDC, Microsoft Connector for SAP BW et un Feature Pack Integration Services pour Azure. Pour plus d’informations, consultez [Nouveautés d’Integration Services dans SQL Server 2016](https://msdn.microsoft.com/library/bb522534.aspx).  
  
-   **Modèles de projet SSAS**  
  
    Inclut les améliorations apportées aux modèles tabulaires au niveau de compatibilité 1200, les colonnes calculées et la sécurité au niveau des lignes pour les modèles en mode DirectQuery, les traductions de métadonnées de modèle, l’exécution de script TMSL dans la tâche DDL d’exécution d’Analysis Services SSIS et de nombreuses résolutions de bogues.  
    Pour plus d’informations, consultez [Nouveautés d’Analysis Services (msdn)](https://msdn.microsoft.com/library/bb522628.aspx) ou [Nouveautés d’Analysis Services (billet de blog)](http://blogs.msdn.com/b/analysisservices/archive/2016/01/28/what-s-new-for-sql-server-2016-analysis-services-in-ctp3-3.aspx).  
  
-   **Modèles de projet de rapport SSRS**  
  
    Aucune annonce pour cette préversion de SSDT. Consultez [Nouveautés de Reporting Services](https://msdn.microsoft.com/library/ms170438.aspx) pour en savoir plus sur d’autres fonctionnalités de cette version CTP.  
  
## <a name="ssdt-december-2015-preview"></a>Préversion de SSDT de décembre 2015  
  
-   Les **modèles de projet SQL Server** incluent des résolutions de bogues pour la boîte de dialogue Connexion, des listes d’historiques récents, l’utilisation appropriée du contexte d’authentification défini dans la propriété de connexion lors du chargement d’une liste de bases de données.  
  
    -   Valeur du délai d’attente du test de connexion remplacée par 15 secondes.  
  
    -   Création d’une règle de pare-feu serveur Azure SQL Database si l’adresse IP du client n’est pas inscrite lors du chargement d’une liste de bases de données.  
  
    -   Prise en charge de la programmabilité des fonctionnalités SQL Server 2016 CTP 3.2.  
  
-   Les **modèles de projet SSAS** ajoutent la prise en charge de la création de tables calculées basées sur des expressions DAX et d’autres objets déjà définis dans le modèle.  
  
-   Les ajouts du **modèle de projet de package SSIS** incluent la prise en charge du connecteur Hadoop SSIS pour le format de fichier Avro et l’authentification Kerberos.   
    Notez que la prise en charge du concepteur SSIS pour SSIS 2012 et 2014 n’est pas encore incluse dans cette mise à jour.  
  
## <a name="ssdt-november-2015-preview"></a>Préversion de SSDT de novembre 2015  
  
-   **Modèles de projet SQL Server**. Aperçu de l’expérience de connexion améliorée pour SQL Server et Azure SQL Database.  
  
-   **Modèles de projet de package SSIS**. Amélioration des performances du catalogue SSIS : les performances de la plupart des affichages catalogue SSIS pour un utilisateur non-administrateur SSIS sont améliorées.  
  
-   Les **modèles de projet SSAS** incluent les améliorations apportées aux projets de modèles tabulaires dans Analysis Services. Vous pouvez utiliser la commande **Afficher le code** pour voir la définition de modèle dans JSON. Si vous n’utilisez pas une édition complète de Visual Studio 2015, vous devez en avoir une pour obtenir l’éditeur JSON. Vous pouvez télécharger gratuitement l’[édition Visual Studio Community](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx).  
  
## <a name="ssdt-october-2015-preview"></a>Préversion de SSDT d’octobre 2015  
  
-   Nouveaux modèles de projet pour BI (modèles Analysis Services, rapports Reporting Services et packages Integration Services). Tous les modèles de projet SQL Server se trouvent maintenant dans un seul et même SSDT.  
  
-   Nouvelles fonctionnalités de SSIS, notamment le connecteur Hadoop, le modèle de flux de contrôle, la taille maximale approximative de la mémoire tampon d’une tâche de flux de données.  
  
-   Prise en charge des fonctionnalités de SQL Server 2016 CTP 3.0 pour les projets de base de données relationnelle.  
  
-   Divers correctifs de bogues dans SSIS et prise en charge du système d’exploitation Windows 7.  
  
## <a name="ssdt-september-2015-preview"></a>SSDT version préliminaire de septembre 2015  
  
-   La prise en charge multilingue est nouvelle dans cette version préliminaire.  
  
## <a name="ssdt-august-2015-preview"></a>SSDT version préliminaire d’août 2015  
  
-   Nouveau programme Setup.exe autonome pour l’installation de SSDT.  Vous n’avez plus besoin d’utiliser une version modifiée du programme d’installation de SQL Server. Cette version de SSDT inclut un modèle de projet pour la création de bases de données relationnelles déployées sur SQL Server ou Azure SQL Database.  
  
## <a name="see-also"></a>Voir aussi  
[Télécharger SQL Server Data Tools &#40;SSDT&#41;](../ssdt/download-sql-server-data-tools-ssdt.md)  
[Versions antérieures de SQL Server Data Tools &#40;SSDT et SSDT-BI&#41;](../ssdt/previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md)  
[Nouveautés du moteur de base de données](https://msdn.microsoft.com/library/bb510411.aspx)  
[Nouveautés d’Analysis Services](https://msdn.microsoft.com/library/bb522628.aspx)  
[Nouveautés d’Integration Services](https://msdn.microsoft.com/library/bb522534.aspx)  
  

