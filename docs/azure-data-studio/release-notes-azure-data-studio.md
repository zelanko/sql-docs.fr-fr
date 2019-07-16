---
title: Notes de publication
titleSuffix: Azure Data Studio
description: Notes de publication Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 07/11/2019
ms.openlocfilehash: 8f19424b1e7946c7fb3d7a7056c1bda94b83b79b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959388"
---
# <a name="release-notes-for-azure-data-studio"></a>Notes de publication pour Azure Data Studio

**[Téléchargez et installez la dernière version !](download.md)**

## <a name="july-2019"></a>Juillet 2019

Le 11 juillet 2019 &nbsp;  /  &nbsp; version : 1.9.0 

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Version de l’extension de l’Explorateur de Plan de SentryOne | Notre partenaire privilégié de Microsoft, SentryOne, allez expédier leurs [extension de l’Explorateur de Plan de SentryOne pour Azure Data Studio](https://www.sentryone.com/products/sentryone-plan-explorer-extension-azure-data-studio). <br> Il s’agit d’une extension gratuite, qui fournit des diagrammes de plan améliorée pour les requêtes s’exécuter dans Azure Data Studio, avec les algorithmes de disposition optimisée et le codage en couleurs intuitif pour aider à identifier rapidement les opérateurs plus coûteuses qui affectent les performances des requêtes. Pour en savoir plus sur l’extension, consultez billet de blog de SentryOne [ici](https://sqlperformance.com/2019/07/sentryone/plan-explorer-extension-azure-data-studio). |
| Nouvelles fonctionnalités proposées par comparaison de schémas | &bull; &nbsp; Prise en charge des fichiers de comparaison de schéma (. SCMP) <br/>&bull; &nbsp; Annuler la prise en charge de la comparaison de schéma <br/>&bull; &nbsp; Terminer les modifications, vous pouvez trouver [ici](https://github.com/microsoft/azuredatastudio/issues?utf8=%E2%9C%93&q=is%3Aissue+milestone%3A%22July+2019+Release%22+label%3A%22Area%3A+Schema+Compare%22+is%3Aclosed+)|
| Améliorations du bloc-notes | &bull; &nbsp; Prise en charge Python plotly <br/>&bull; &nbsp; Ouvrir le bloc-notes à partir du navigateur <br/> &bull; &nbsp; Boîte de dialogue Gestion des packages Python <br/> &bull; &nbsp; Améliorations des performances et Markdown <br/> &bull; &nbsp; Mise à jour des raccourcis clavier <br/>  &bull; &nbsp; Correctifs de bogues et fonctionnalités mineures, vous pouvez trouver [ici](https://github.com/microsoft/azuredatastudio/issues?utf8=%E2%9C%93&q=is%3Aissue+milestone%3A%22July+2019+Release%22+is%3Aclosed+label%3A%22Area%3A+Notebooks%22+) |
| Prise en charge SQL Server 2019 |  Cette version inclut la prise en charge des fonctionnalités de SQL Server 2019 Big Data Cluster supplémentaires, notamment : <br/> &bull; &nbsp; Table de points de terminaison de service dans le tableau de bord de gestion qui répertorie tous les services clés dans le cluster. <br/> &bull; &nbsp; Cluster état bloc-notes montre comment vous pouvez interroger et résoudre les problèmes d’état du cluster dans l’ensemble des services et des pods.| 
| Mise à jour linguistiques disponibles| 10 modules linguistiques sont désormais disponibles dans la place de marché du Gestionnaire d’extensions. Simplement, recherchez le langage spécifique à l’aide de la place de marché d’extension et installer. Une fois que vous installez la langue sélectionnée, Azure Data Studio vous invitera à redémarrer avec le nouveau langage. |
| Mise à jour SQL Server Profiler | L’extension de profil SQL Server a été mis à jour pour inclure les nouvelles fonctionnalités, notamment : <br/> &bull; &nbsp; Filtrage par nom de la base de données <br/> &bull; &nbsp; Copiez et collez la prise en charge <br/> &bull; &nbsp; Enregistrer/charger le filtre <br/>Une liste complète des améliorations pour l’Extension de SQL Server Profiler peut être trouvée [ici](https://github.com/microsoft/azuredatastudio/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aclosed+milestone%3A%22July+2019+Release%22+label%3A%22Area%3A+SQL+Profiler%22+).  |
| Visual Studio Code la version de mai fusion 1.35 | Vous pouvez trouver les dernières améliorations [ici](https://code.visualstudio.com/updates/v1_35). |
| Problèmes et bogues résolus | Dans les versions précédentes d’Azure Data Studio, si une base de données utilisateur a été sélectionnée lors de la connexion à partir de la boîte de dialogue de connexion, l’entrée de l’Explorateur d’objets qui en résulte a été étendue entièrement à cette base de données unique. À compter de cette version, que comportement est en cours de modification afin que les propriétés de niveau serveur sont également affichées dans l’Explorateur d’objets. <br/> Pour obtenir la liste complète des correctifs consultez [bogues et des problèmes, sur GitHub](https://github.com/microsoft/azuredatastudio/milestone/35?closed=1). |
| &nbsp; | &nbsp; |


## <a name="june-2019"></a>Juin 2019

Le 6 juin 2019 &nbsp;  /  &nbsp; version : 1.8.0 

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Version de l’extension de serveurs d’administration centrale (CMS) | Serveurs de gestion centralisée stocker une liste d’instances de SQL Server qui sont organisées en un ou plusieurs groupes de serveurs de gestion centralisée. Les utilisateurs peuvent se connecter à leurs propres serveurs CMS existants et gérer leurs serveurs, comme l’ajout et suppression de serveurs. Pour en savoir plus, vous pouvez lire [ici](https://docs.microsoft.com/sql/relational-databases/administer-multiple-servers-using-central-management-servers) |
| Version des Extensions de l’outil Administration de base de données pour Windows | Cette extension lance deux des expériences plus utilisés dans SQL Server Management Studio à partir de Studio de données Azure. Les utilisateurs peuvent cliquez avec le bouton droit sur de nombreux objets différents (par exemple, les bases de données, Tables, colonnes, vues, etc.) et sélectionner Propriétés pour afficher la boîte de dialogue de propriétés de SSMS pour cet objet. En outre, les utilisateurs peuvent cliquez avec le bouton droit sur une base de données et sélectionnez Générer des Scripts pour lancer le connue SSMS Assistant génération de Scripts. 
| Améliorations de comparaison de schéma | &bull; &nbsp; Options inclure/exclure ajouté <br/>&bull; &nbsp; Générer un Script de script s’ouvre après avoir généré <br/>&bull; &nbsp; Supprimer les barres de défilement double  <br/>&bull; &nbsp; Améliorations de mise en forme et la disposition <br/>&bull; &nbsp; Terminer les modifications, vous pouvez trouver [ici](https://github.com/microsoft/azuredatastudio/issues?q=is%3Aissue+milestone%3A%22June+2019+Release%22+label%3A%22Area%3A+Schema+Compare%22+is%3Aclosed)|
| Section des Messages déplacée à l’onglet propre | Lorsque les utilisateurs exécutaient des requêtes SQL, résultats et les messages ont été dans les panneaux empilées. Elles sont désormais dans des onglets séparés dans un panneau, comme dans SSMS. |
| Améliorations du bloc-notes SQL | &bull; &nbsp; Les utilisateurs peuvent désormais choisir d’utiliser leurs propres installations de Python 3 ou Anaconda dans des notebooks <br/>&bull; &nbsp; Plusieurs stabilité + correctifs d’ajuster/terminer <br/> &bull; &nbsp; Afficher la liste complète des améliorations [ici](https://github.com/microsoft/azuredatastudio/issues?q=is%3Aissue+milestone%3A%22June+2019+Release%22+is%3Aclosed+label%3A%22Area%3A+Notebooks%22)|
| Visual Studio Code la version de mai fusion 1.34 | Vous pouvez trouver les dernières améliorations [ici](https://code.visualstudio.com/updates/v1_34) |
| Bogues résolus et les problèmes. | Consultez [bogues et des problèmes, sur GitHub](https://github.com/microsoft/azuredatastudio/milestone/32?closed=1). |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus
- Extensions de l’outil Administration de base de données pour Windows
    - Impossible de lancer les propriétés à partir du nœud de serveur déconnecté
    - Impossible de lancer les propriétés pour les serveurs Azure
    - Pas tous les objets ont des boîtes de dialogue de propriété
    - Boîtes de dialogue prennent beaucoup de temps à démarrer
    - Erreurs de lancement de serveurs avec certains types de connexions (par exemple, AAD)
- Notebooks
    - [5838](https://github.com/microsoft/azuredatastudio/issues/5838) permettre aux utilisateurs d’utiliser le système de Python pour les blocs-notes
- Comparaison de schémas
    - [5804](https://github.com/microsoft/azuredatastudio/issues/5804) tâches de comparaison de schémas affichent le menu de contexte d’annulation par défaut qui n’a aucun effet

## <a name="may-2019"></a>Mai 2019

Le 8 mai 2019 &nbsp;  /  &nbsp; version : 1.7.0 

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Version de l’extension de comparaison de schémas | Comparaison de schémas est une fonctionnalité bien connue dans SQL Server Data Tools (SSDT) et son est principalement utilisé pour comparer et visualiser les différences entre les bases de données et fichiers .dacpac et d’exécuter des actions pour que la même. |
| Déplacé d’affichage de la tâche dans la fenêtre Sortie | Les utilisateurs peuvent désormais afficher l’état des tâches longues telles que la sauvegarde, la restauration et la comparaison de schémas dans la vue tâches dans la fenêtre Sortie
| Page d’accueil ajouté | &bull; &nbsp; Des liens vers des actions courantes telles que la nouvelle requête, le nouveau fichier, nouveau bloc-notes <br/>&bull; &nbsp; Liens vers la documentation et GitHub |
| Améliorations du bloc-notes SQL | &bull; &nbsp; Améliorations de rendu markdown, y compris une meilleure prise en charge pour les tables et les notes de publication <br/>&bull; &nbsp; Améliorations de la convivialité de la barre d’outils <br/>&bull; &nbsp; Liens markdown pour les blocs-notes approuvés n’est plus nécessitent Cmd/Ctrl + cliquez sur et peuvent être activés directement <br/>&bull; &nbsp; Améliorations de nettoyage des processus de Jupyter après la fermeture des ordinateurs portables et en réduisant les erreurs lors du démarrage de plusieurs blocs-notes simultanément <br/>&bull; &nbsp; Améliorations aux connexions de bloc-notes SQL pour vous assurer d’erreurs ne se produisent pas lors de l’exécution de 2 ordinateurs portables par rapport à la même base de données <br/>&bull; &nbsp; Améliorations pour le défilement automatique de l’ordinateur portable à la cellule en cours d’exécution lorsque vous cliquez sur le bouton Exécuter les cellules à partir de la barre d’outils <br/>&bull; &nbsp; Améliorations de stabilité et de performances générales |
| Bogues résolus et les problèmes. | Consultez [bogues et des problèmes, sur GitHub](https://github.com/microsoft/azuredatastudio/milestone/31?closed=1). |
| &nbsp; | &nbsp; |

## <a name="april-2019"></a>Avril 2019

Le 18 avril 2019 &nbsp;  /  &nbsp; version : 1.6.0 

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Renommé **serveurs** TAB pour accéder à **connexions** | |
| Déplacé d’Azure Resource Explorer en tant que les vues font un Azure sous connexions | Les utilisateurs peuvent maintenant afficher leurs instances de SQL Azure via les vues font Azure dans la vue de connexions et se développent pour afficher les objets sous chaque serveur ou une base de données.|
| Améliorations du bloc-notes SQL | &bull; &nbsp; Bouton ajouté dans la barre d’outils pour effacer la sortie pour toutes les cellules <br/>&bull; &nbsp; Bouton ajouté dans la barre d’outils pour exécuter toutes les cellules <br/>&bull; &nbsp; Nom de connexion fixe au lieu du nom du serveur (si défini) dans l’attacher à la liste déroulante <br/>&bull; &nbsp; Correctif pour les images dans un fichier markdown ne pas rendu lors de l’utilisation de chemins d’accès relatif de l’image <br/>&bull; &nbsp; Fonctionnalités améliorées dans les grilles de bloc-notes en ajoutant double-cliquez sur la taille de la colonne-redimensionnement automatique et prise en charge de la molette de souris améliorée <br/>&bull; &nbsp; Améliorations apportées à la gestion des erreurs et python installer résilience lors de l’installation de python via les blocs-notes <br/>&bull; &nbsp; Améliorations apportées à la fonctionnalité « sélectionner tout » lors de la sélection des cellules de bloc-notes <br/>&bull; &nbsp; Améliorations apportées à des connexions de bloc-notes pour empêcher la fermeture d’un ordinateur portable et ayant un impact sur une connexion de l’Explorateur d’objets <br/>&bull; &nbsp; Expérience de bloc-notes amélioré pour afficher un message à l’utilisateur lorsque le notebook déconnecté et nécessite une connexion à l’exécution des cellules<br/>&bull; &nbsp; Prise en charge améliorée pour les blocs-notes non enregistrées à rafraîchir des publicités au prochain démarrage de publicités |
| Bogues résolus et les problèmes. | Consultez [bogues et des problèmes, sur GitHub](https://github.com/Microsoft/azuredatastudio/milestone/26?closed=1). |
| &nbsp; | &nbsp; |

## <a name="march-2019-hotfix"></a>Mars 2019 (correctif)

Le 22 mars 2019 &nbsp;  /  &nbsp; version : 1.5.2 &nbsp;  /  &nbsp; version de correctif logiciel

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Correction de quelques problèmes découverts dans 1.5.1. | Consultez [mars de version de correctif logiciel, sur GitHub](https://github.com/Microsoft/azuredatastudio/milestone/28).<br/> <br/>&bull; &nbsp; Résolution du problème où utilisateur Impossible de fermer le bloc-notes ouvert à partir de la tâche « Ouvrir le bloc-notes » dans le tableau de bord <br/>&bull; &nbsp; Problème résolu où bloc-notes JSON a très} après l’enregistrement <br/>&bull; &nbsp; Résolution du problème où des grilles de notebook ne répondent pas aux modifications de thème <br/>&bull; &nbsp; Résolution du problème où le chemin d’accès du carnet de notes complète a été affichée dans l’en-tête de l’onglet. Maintenant seulement le nom de fichier s’affiche. |
| &nbsp; | &nbsp; |

## <a name="march-2019"></a>Mars 2019

Le 18 mars 2019 &nbsp;  /  &nbsp; version : 1.5.1

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Ajouté [extension PostgreSQL pour Azure Data Studio](postgres-extension.md) | Fonctionnalités prises en charge : <br/>&bull; &nbsp; Boîte de dialogue Connexion <br/>&bull; &nbsp; Explorateur d’objets <br/>&bull; &nbsp; Éditeur de requête <br/>&bull; &nbsp; Création de graphiques <br/>&bull; &nbsp; Tableaux de bord <br/>&bull; &nbsp; Extraits de code <br/>&bull; &nbsp; Modifier des données <br/>&bull; &nbsp; Ordinateurs portables |
| Blocs-notes SQL ajouté | Noyau de SQL prise en charge à la visionneuse de bloc-notes intégrée : <br/>&bull; &nbsp; Prend en charge T-SQL <br/>&bull; &nbsp; Prise en charge PGSQL |
| Ajout d’Extension PowerShell  | Permet d’afficher le [extension PowerShell](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell) à partir de VS Code.  |
| Ajout d’extension dacpac SQL Server  | Supprime l’Assistant Création d’applications de couche données à partir de l’extension de SQL Server Import dans une nouvelle extension.  |
| Ajout d’extension Communauté QueryPlan.show | Ajoute la prise en charge de l’intégration pour visualiser les plans de requête  |
| Extension de SQL Server 2019 Preview mis à jour | &bull; &nbsp; Prise en charge de Jupyter Notebook, en particulier les noyaux Python3 et Spark, ont déplacés dans l’outil d’Azure Data Studio core. <br/>&bull; &nbsp; Correctifs de bogues pour l’Assistant de données externes  |
| Bogues résolus et les problèmes. | Consultez [bogues et des problèmes, sur GitHub](https://github.com/Microsoft/azuredatastudio/milestone/25?closed=1). |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus
- [#4427](https://github.com/Microsoft/azuredatastudio/issues/4427): En cliquant sur Exécuter sur la cellule avant de noyau est prêt pour Spark entraîne une erreur irrécupérable **solution de contournement :** Attendez que les noyaux sont chargés jusqu'à ce que toutes les cellules en cours d’exécution
- [#4493](https://github.com/Microsoft/azuredatastudio/issues/4493): ANNONCES lancés à partir de SSMS via l’authentification SQL - invite l’utilisateur pour le mot de passe **solution de contournement :** Utiliser l’authentification de Windows pour l’instant. 
- [#4494](https://github.com/Microsoft/azuredatastudio/issues/4494): Impossible d’installer la fonctionnalité de bloc-notes SQL <br/>
**Solution de contournement :** Suivez les étapes de la solution de contournement [ici](https://github.com/Microsoft/azuredatastudio/issues/4494#issuecomment-473043832). 
- [#4503](https://github.com/Microsoft/azuredatastudio/issues/4503): Azure Data Studio ne peut pas être ouvert directement à partir du dossier Téléchargements (Mac) <br />
**Solution de contournement :** Redémarrez l’ordinateur après avoir décompressé l’application. Seront examinés. 
- [#4539](https://github.com/Microsoft/azuredatastudio/issues/4539):  Enregistrer comme bloc-notes perd le contexte de connexion <br />
**Solution de contournement :** Sera résolu dans une prochaine version. 
- [#4458](https://github.com/Microsoft/azuredatastudio/issues/4458): Extraction de dacpac tombe en panne SqlToolsService si une version non valide est utilisée. <br/>
**Solution de contournement :** Redémarrez Azure Data Studio et vérifiez la version appropriée est utilisée.
- Nouvelles icônes de bloc-notes et ouvrir le bloc-notes sont perdues <br/> 
**Solution de contournement :** Le type de connexion héritée est déconseillé. Nous vous recommandons de se connecter au point de terminaison SQL Server et vous obtiendrez toutes les actions (nouveau bloc-notes, travail Spark) comme prévu. 

## <a name="february-2019"></a>Février 2019

Le 13 février 2019 &nbsp;  /  &nbsp; version : 1.4.5

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Ajouté **pack d’administration pour SQL Server** pack d’extension. | Cela rend plus facile d’installer les extensions dépendant de l’administrateur de SQL Server. notamment :<br/>&bull; &nbsp; [Agent SQL Server](sql-server-agent-extension.md?view=sql-server-2017)<br/>&bull; &nbsp; [SQL Server Profiler](https://docs.microsoft.com/sql/azure-data-studio/sql-server-profiler-extension)<br/>&bull; &nbsp; [SQL Server Import](sql-server-import-extension.md?view=sql-server-2017) |
| Filtrage ajouté étendu la prise en charge des événements dans l’extension de Profiler. | &nbsp; |
| Added enregistrer en tant que fonctionnalité XML qui peut enregistrer des résultats de T-SQL au format XML. | &nbsp; |
| Améliorations de l’Assistant d’Application de couche données ajoutées. | &bull; &nbsp; Bouton Générer un script ajouté<br/>&bull; &nbsp; Ajout d’affichage pour donner des avertissements de perte de données pendant le déploiement. |
| Mises à jour à l’extension de la version préliminaire de SQL Server 2019. | Consultez [extension de la version préliminaire de SQL Server 2019](sql-server-2019-extension.md?view=sql-server-ver15). |
| Activé par défaut pour le long de la diffusion en continu des résultats des requêtes en cours d’exécution. | &nbsp; |
| Bogues résolus et les problèmes. | Consultez [bogues et des problèmes, sur GitHub](https://github.com/Microsoft/azuredatastudio/milestone/23?closed=1). |
| &nbsp; | &nbsp; |

## <a name="january-2019-hotfix"></a>Janvier 2019 (correctif)

Le 16 janvier 2019 &nbsp;  /  &nbsp; version : 1.3.9 &nbsp;  /  &nbsp; version de correctif logiciel

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Correction de quelques problèmes découverts dans 1.3.8. | Consultez [version de correctif logiciel de janvier, sur GitHub](https://github.com/Microsoft/azuredatastudio/milestone/24?closed=1).<br/><br/>Pour plus d’informations, consultez :<br/>&bull; &nbsp; [Journal des modifications, sur GitHub](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md).<br/>&bull; &nbsp; [Les versions, sur GitHub](https://github.com/Microsoft/azuredatastudio/releases). |
| &nbsp; | &nbsp; |

## <a name="january-2019"></a>Janvier 2019

09 janvier 2019 &nbsp;  /  &nbsp; version : 1.3.8

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Ajouter un nouveau programme d’installation utilisateur pour Windows. | Contrairement au programme d’installation de système existant, le nouveau programme d’installation de l’utilisateur ne nécessite pas de privilèges d’administrateur. Cela permet également une expérience de mise à niveau plus facile pour les non-administrateurs. |
| Prise en charge l’authentification Azure Active Directory. | &nbsp; |
| Annonce de Idera SQL DM Performance Insights (version préliminaire). | &nbsp; |
| La prise en charge de l’Assistant Création d’applications de couche données dans l’extension de SQL Server Import. | &nbsp; |
| Mettre à jour à l’extension de la version préliminaire de SQL Server 2019. | Consultez [extension de la version préliminaire de SQL Server 2019](sql-server-2019-extension.md?view=sql-server-ver15). |
| Améliorations de SQL Server Profiler. | &nbsp; |
| Résultats de la diffusion en continu pour les grandes requêtes (version préliminaire). | &nbsp; |
| Extensions de la Communauté : sp_executesql to sql et de la nouvelle base de données. | &nbsp; |
| Bogues résolus et les problèmes. | Consultez [bogues et des problèmes, sur GitHub](https://github.com/Microsoft/azuredatastudio/milestone/19?closed=1). |
| &nbsp; | &nbsp; |

## <a name="november-2018"></a>Novembre 2018

6 novembre 2018 &nbsp;  /  &nbsp; version : 1.2.4

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Mettre à jour à l’extension de la version préliminaire de SQL Server 2019. | Consultez [extension de la version préliminaire de SQL Server 2019](sql-server-2019-extension.md?view=sql-server-ver15). |
| Présentation de coller l’extension de Plan. | &nbsp; |
| Présentation des extensions de requêtes de couleur haute, y compris de thème de l’éditeur SSMS. | &nbsp; |
| Correctifs inclus dans SQL Server Agent, Profiler et importer des extensions. | &nbsp; |
| Corriger les.Net Core à l’origine du problème Socket KeepAlive supprimé des connexions inactives sur macOS. | &nbsp; |
| Service des outils SQL mise à niveau vers.Net Core 2,2 Preview 3 (pour une éventuelle prise en charge AAD). | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-november-2018"></a>Correctifs de bogues, novembre 2018

- Corriger [émettre #2933](https://github.com/Microsoft/azuredatastudio/issues/2933): Connexion perdue à la base de données SQL Azure
- Corriger [émettre #2914](https://github.com/Microsoft/azuredatastudio/issues/2914): Nœud de la base de données « Argument non valide » exception de l’Explorateur d’objets en expansion
- Corriger [émettre #2935](https://github.com/Microsoft/azuredatastudio/pull/2935): Les messages de plusieurs lignes s’affichent correctement dans les résultats de la requête
- Corriger [émettre #2906](https://github.com/Microsoft/azuredatastudio/pull/2906): Corrigez le nom de document de modifier les données lorsque le nom de la table contient des caractères spéciaux
- Corriger [émettre #2929](https://github.com/Microsoft/azuredatastudio/issues/2929): Intégré dans l’extension de journal des modifications indique que vérifier les Notes de publication de VSCode pour les modifications
- Corriger [émettre #2719](https://github.com/Microsoft/azuredatastudio/issues/2719): Thème à contraste élevé doubles/triplets icônes
- Corriger [émettre #3047](https://github.com/Microsoft/azuredatastudio/pull/3047): Ajouter une interface de ligne de commande pour la connexion à un serveur SQL Server
- Corriger [émettre #3031](https://github.com/Microsoft/azuredatastudio/pull/3031): Ajouter la prise en charge du thème query plan

## <a name="october-2018"></a>Octobre 2018

Le 29 octobre 2018 &nbsp;  /  &nbsp; version : 1.1.4

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Présentation de l’Explorateur de ressources Azure pour parcourir les bases de données SQL Azure. | &nbsp; |
| Améliorer la robustesse de connectivité de l’Explorateur d’objets et de l’éditeur de requête. | &nbsp; |
| Améliorations d’extensions de l’Agent SQL. | &nbsp; |
| Mettre à jour à l’extension de la version préliminaire de SQL Server 2019. | Consultez [extension de la version préliminaire de SQL Server 2019](sql-server-2019-extension.md?view=sql-server-ver15). |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-october-2018"></a>Correctifs de bogues, octobre 2018

- Corriger [émettre #2717](https://github.com/Microsoft/azuredatastudio/issues/2717): Résultat de la colonne XML sur la mise en forme
- Corriger [émettre #2993](https://github.com/Microsoft/azuredatastudio/issues/2993): Les fenêtres de résultats de la largeur est incomplète
- Corriger [émettre #2999](https://github.com/Microsoft/azuredatastudio/issues/2999): Pas de charger le fichier System.Diagnostics.Tracing sur Mac lors de la connexion à la base de données
- Corriger [émettre #2851](https://github.com/Microsoft/azuredatastudio/issues/2851): Graphique de TimeSeries ne sont pas rendus correctement
- Corriger [émettre #2996](https://github.com/Microsoft/azuredatastudio/issues/2996): Perte de la table temporaire en raison du changement de session soudaine

Pour plus d’informations, consultez le [journal des modifications](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), et [versions](https://github.com/Microsoft/azuredatastudio/releases).

## <a name="september-2018-ga-release"></a>Septembre 2018 (disponibilité générale)

Le 24 septembre 2018 &nbsp;  /  &nbsp; version : 1.0 &nbsp;  /  &nbsp; version GA

Version disponibilité générale d’Azure Data Studio (anciennement SQL Operations Studio).

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Grille de résultats améliorations des performances et l’expérience utilisateur pour un grand nombre de jeux de résultats de requête. | &nbsp; |
| Visual Studio de Code source code Actualiser à partir de 1.23 à 1.26.1 avec disposition en grille et l’éditeur de paramètres amélioré (version préliminaire). | &nbsp; |
| Améliorations de l’accessibilité pour le lecteur d’écran, la navigation au clavier et à contraste élevé. | &nbsp; |
| Ajouté `Connection name` possibilité de fournir un nom d’affichage autre dans la vue-permettent de serveurs. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="announcing-the-sql-server-2019-preview-extension"></a>Annonce de l’extension de la version préliminaire de SQL Server 2019

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Prise en charge des fonctionnalités en version préliminaire de SQL Server 2019 notamment [cluster big data](../big-data-cluster/big-data-cluster-overview.md) prennent en charge. | Se connecter à la passerelle HDFS/Spark fournis avec la version préliminaire de SQL Server 2019.<br/><br/>Parcourir HDFS, de télécharger des fichiers, d’enregistrer des fichiers et de lancer des actions utiles telles que d’analyser dans le bloc-notes pour les fichiers CSV.<br/><br/>Envoyer des travaux Spark à partir du tableau de bord ou avec le bouton droit sur une connexion de HDFS/Spark dans l’Explorateur d’objets. |
| Azure Data Studio blocs-notes. | Créez ou ouvrez des ordinateurs portables à l’aide d’une visionneuse de Notebook intégrée. Dans cette version du bloc-notes viewer prend en charge la connexion à noyaux locaux et de cluster SQL Server 2019 big data.<br/><br/>Utiliser les bibliothèques d’accélérateur de Code PROSE dans votre bloc-notes pour en savoir plus de types de données et de format de fichier pour la préparation des données rapide. |
| Explorateur de ressources Azure. | La vue Explorateur de ressources Azure vous permet de parcourir les points de terminaison liées aux données de vos comptes Azure et créer des connexions avec eux dans l’Explorateur d’objets. Dans cette version prise en charge les serveurs et les bases de données SQL Azure. |
| Assistant de Table externe de création de SQL Server PolyBase. | Créer une table externe et ses structures de métadonnées de prise en charge avec un Assistant facile à utiliser. Dans cette version, les serveurs SQL Server et Oracle à distance sont pris en charge. |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-september-2018"></a>Correctifs de bogues, septembre 2018

- Corriger [émettre #2647](https://github.com/Microsoft/azuredatastudio/issues/143): Les graphiques a pris un grand pas vers l’arrière.
- Corriger [émettre #2648](https://github.com/Microsoft/azuredatastudio/issues/143): SELECT qui retourne un lien hypertexte est JSON toute la colonne.

Pour plus d’informations, consultez le [journal des modifications](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md), et [versions](https://github.com/Microsoft/azuredatastudio/releases).

## <a name="august-2018"></a>Août 2018

Le 30 août 2018 &nbsp;  /  &nbsp; version : 0.32.8 &nbsp;  /  &nbsp; version préliminaire publique

Le *version préliminaire publique d’août* se concentre sur les correctifs de bogues, stabilisation de produit et le remplissage des écarts dans les scénarios existants.

_0.32.8 contient des correctifs pour quelques régression trouvée dans 0.32.7 ([#1971](https://github.com/Microsoft/azuredatastudio/issues/1971), [#2372](https://github.com/Microsoft/azuredatastudio/issues/2372))_

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Annonce de l’Extension d’importation SQL Server. | &nbsp; |
| Gestion de la Session de SQL Server Profiler. | &nbsp; |
| Prise en charge du modèle de session de SQL Server Profiler. | &nbsp; |
| Améliorations de l’Agent SQL Server. | &nbsp; |
| Nouvelle extension de la Communauté : Premier kit de répondeur. | &nbsp; |
| Améliorations de la qualité de vie : Chaînes de connexion | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-august-2018"></a>Correctifs de bogues, août 2018

- Analyser SQL dans une fenêtre d’éditeur de requête à l’aide de la `Parse Syntax` commande.
- Corriger [émettre #143](https://github.com/Microsoft/azuredatastudio/issues/143): Double-cliquez sur désélectionnez dans le nom de la variable.
- Corriger [émettre #387](https://github.com/Microsoft/azuredatastudio/issues/387): Icône de base de données SQL onglet est rouge.
- Corriger [émettre #825](https://github.com/Microsoft/azuredatastudio/issues/825): Demande : Automatique se connecter au serveur actuel après le Script en tant que... 
- Corriger [émettre #1278](https://github.com/Microsoft/azuredatastudio/issues/1278): sqlops.desktop [entrée du bureau] - valeur redondant pour nom & commentaire.
- Corriger [émettre #1285](https://github.com/Microsoft/azuredatastudio/issues/1285): Icône d’application entraîne la mise à jour pour être supprimé/remplacé dans Windows.
- Corriger [émettre #1317](https://github.com/Microsoft/azuredatastudio/issues/1317): Correction du séparateur décimal.
- Corriger [émettre #1474](https://github.com/Microsoft/azuredatastudio/issues/1474): Modifier la connexion à annuler déconnecte la connexion actuelle.
- Corriger [émettre #1497](https://github.com/Microsoft/azuredatastudio/issues/1497): Afficher en tant que graphique options sont tronquées en bas.
- Corriger [émettre #1524](https://github.com/Microsoft/azuredatastudio/issues/1524): Interpréteur de commandes/tableau de bord : Les vues font principales icônes sont déplaçables et peuvent se bloquer l’application.
- Corriger [émettre #1578](https://github.com/Microsoft/azuredatastudio/issues/1578): Impossible de développer/réduire le dossier de navigateur de fichier distant en cliquant sur le nom.
- Corriger [émettre #1620](https://github.com/Microsoft/azuredatastudio/issues/1620): Suggestion de fonctionnalité : Obtenir la chaîne de connexion pour la connexion existante.
- Corriger [émettre #1624](https://github.com/Microsoft/azuredatastudio/issues/1624): SelectBox ne change pas lorsque désactivé
- Corriger [émettre #1728](https://github.com/Microsoft/azuredatastudio/issues/1728): Enregistrer en tant que JSON/EXCEL/CSV non professionnel.
- Corriger [émettre #1744](https://github.com/Microsoft/azuredatastudio/issues/1744): Volet de résultats perd ses positions de défilement quand vous basculez entre les onglets.
- Corriger [émettre #1748](https://github.com/Microsoft/azuredatastudio/issues/1748): Message d’erreur lors de l’enregistrement d’heure de fichier deuxième (et ultérieures) Excel.
- Corriger [émettre #1782](https://github.com/Microsoft/azuredatastudio/issues/1782): Modifier des données : cellule ne revert à la valeur d’origine sur appuyant sur la touche ÉCHAP.
- Corriger [émettre #1836](https://github.com/Microsoft/azuredatastudio/issues/1836): fichiers .sql non associés à SQL Operations Studio.
- Corriger [émettre #1850](https://github.com/Microsoft/azuredatastudio/issues/1850): Tapez N'' remplissage automatique des N'' '.
- Corriger [émettre #1985](https://github.com/Microsoft/azuredatastudio/issues/1985): Copie à partir de la grille de résultats de requête est désactivée par 1 colonne.
- Corriger [émettre #1998](htpts://github.com/Microsoft/azuredatastudio/pull/1998): Ajouter la version VS Code à sur la boîte de dialogue.
- Corriger [émettre #2042](https://github.com/Microsoft/azuredatastudio/pull/2042): Agent : Activation de bouton Importer des requêtes à partir de fichiers sql.
- Corriger [émettre #2091](https://github.com/Microsoft/azuredatastudio/issues/2091): Impossible d’utiliser les raccourcis Ctrl + C pour copier à partir du volet de résultats.
- Corriger [émettre #2099](https://github.com/Microsoft/azuredatastudio/pull/2099): Ajouté saveAsCsv davantage d’options.
- Corriger [émettre #2107](https://github.com/Microsoft/azuredatastudio/issues/2107): Icône de document pour les documents de tableau de bord et de Profiler de mise à jour.
- Corriger [émettre #2129](https://github.com/Microsoft/azuredatastudio/pull/2129): Enregistrer la position de défilement de données de modification lors de la commutation des onglets.
- Corriger [émettre #2152](https://github.com/Microsoft/azuredatastudio/issues/2152): Indicateur de ligne de la grille de résultats basé sur zéro.

### <a name="known-issues-august-2018"></a>Problèmes connus, août 2018

- [Problème #2371](https://github.com/Microsoft/azuredatastudio/issues/2371) enregistrer comme Excel uniquement enregistre première ligne de données
- [Problème #2150](https://github.com/Microsoft/azuredatastudio/issues/2150): Impossible de se connecter sur Ubuntu 16.04 to SQL dans un conteneur

## <a name="july-2018"></a>Juillet 2018

Le 19 juillet 2018 &nbsp;  /  &nbsp; version : 0.31.4 &nbsp;  /  &nbsp; version préliminaire publique

Le *préliminaire de juillet* se concentre sur les éléments suivants :

- La version initiale des scénarios de configuration de l’Agent SQL Server.
- SQL Server Profiler session et la vue modèle améliorations apportées.
- Permanent de correctifs de bogues pour le client a signalé des problèmes GitHub.

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| [SQL Server Agent pour l’extension de SQL Operations Studio](sql-server-agent-extension.md) améliorations. | Ajout d’affichage des alertes, des opérateurs et des proxys et des icônes sur le volet gauche.<br/><br/>Boîtes de dialogue Ajout pour le nouveau travail nouvelle étape du travail, nouvelle alerte et nouvel opérateur.<br/><br/>Ajout Delete Job, supprimer l’alerte et Delete (opérateur) (clic droit).<br/><br/>Visualisation d’exécutions précédentes ajoutée.<br/><br/>Ajout de filtres pour chaque nom de colonne. |
| [SQL Server Profiler pour l’extension de SQL Operations Studio](sql-server-profiler-extension.md) améliorations. | Ajout 5 modèles par défaut pour afficher les événements étendus.<br/><br/>Nom de connexion de serveur/base de données ajoutée.<br/><br/>Prise en charge pour les instances de base de données SQL Azure.<br/><br/>Ajout de suggestion pour quitter Profiler lors de l’onglet est fermé lorsque Profiler est en cours d’exécution. |
| Version de l’Extension des Scripts de combinaison. | &nbsp; |
| Assistant et l’extensibilité de la boîte de dialogue points ajoutées pour les auteurs de l’Extension. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="bug-fixes-july-2018"></a>Correctifs de bogues, juillet 2018

- Corriger [émettre 728](https://github.com/Microsoft/azuredatastudio/issues/728): Aucune réponse pour ajouter une connexion sur macOS
- Corriger [émettre 1612](https://github.com/Microsoft/azuredatastudio/issues/1612): Affichage de texte de grille de résultats est désordre par des caractères internationaux
- Corriger [émettre 1693](https://github.com/Microsoft/azuredatastudio/issues/1693): Boîte de dialogue sauvegarde : Interface utilisateur du navigateur de fichier est interrompue
- Corriger [émettre 1713](https://github.com/Microsoft/azuredatastudio/issues/1713): Nombre de lignes affectées
- Corriger [émettre 1718](https://github.com/Microsoft/azuredatastudio/issues/1718): Impossible de se connecter à une source de données
- Corriger [émettre 1719](https://github.com/Microsoft/azuredatastudio/issues/1719): TypeError lors de la connexion au serveur
- Corriger [émettre 1724](https://github.com/Microsoft/azuredatastudio/issues/1724): Boîtes de dialogue extension ont cessé de fonctionner
- Corriger [émettre 1749](https://github.com/Microsoft/azuredatastudio/issues/1749): BOGUE : Les données HTML dans une colonne sont ensuite interprétées
- Corriger [émettre 1789](https://github.com/Microsoft/azuredatastudio/issues/1789): Extensibilité : Si vous ajoutez un fournisseur de connexion désinstallation sera jamais supprimer dans la liste
- Corriger [émettre 1791](https://github.com/Microsoft/azuredatastudio/issues/1791): Extensions de Sqlops : queryeditor.connect() se connecte à la base de données cible, mais l’interface utilisateur n’affiche pas que l’éditeur est connecté
- Corriger [émettre 1799](https://github.com/Microsoft/azuredatastudio/issues/1799): Graphique de taille de 10 DB principales ne fonctionne pas sur les instances de la casse
- Corriger [émettre 1814](https://github.com/Microsoft/azuredatastudio/issues/1814): définition de type de faute de frappe sqlops.d.ts à l’origine implicite 'any'
- Corriger [émettre 1817](https://github.com/Microsoft/azuredatastudio/issues/1817): Erreur de Ortografia
- Corriger [émettre 1830](https://github.com/Microsoft/azuredatastudio/issues/1830): Paramètre iconPath dans ButtonComponent après l’appel de component() ne change pas l’icône
- Corriger [émettre 1843](https://github.com/Microsoft/azuredatastudio/issues/1843): Une meilleure organisation de Table

## <a name="june-2018"></a>Juin 2018

Le 20 juin 2018 &nbsp;  /  &nbsp; version : 0.30.6 &nbsp;  /  &nbsp; version préliminaire publique

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| **SQL Server Profiler pour SQL Operations Studio _aperçu_**  version initiale d’extension. | &nbsp; |
| La nouvelle **SQL Data Warehouse** extension inclut des widgets de tableau de bord personnalisable riche en exposant des insights à votre entrepôt de données. | Ceci permet de déverrouiller des scénarios clés de gestion et votre entrepôt de données pour vous assurer qu’il est optimisé pour des performances cohérentes. |
| **Modifier les données de « Filtrage et tri »** prennent en charge. | &nbsp; |
| **L’Agent SQL Server pour SQL Operations Studio _aperçu_**  améliorations d’extension pour les travaux et l’historique des travaux vues. | &nbsp; |
| Amélioration de **Assistant & infrastructure de générateur de l’interface utilisateur de boîte de dialogue** API d’extensibilité. | &nbsp; |
| Mettre à jour de code source de plateforme de Code Visual Studio. | Intégré les versions suivantes :<br/>&bull; &nbsp; [Mars 2018 (1.22)](https://code.visualstudio.com/updates/v1_22)<br/>&bull; &nbsp; [Avril 2018 (1.23)](https://code.visualstudio.com/updates/v1_23) |
| &nbsp; | &nbsp; |

### <a name="github-issues-fixes-june-2018"></a>Résout des problèmes GitHub, juin 2018

- Demande de fonctionnalité ([émettre 1204](https://github.com/Microsoft/azuredatastudio/issues/1204)) : Vérifiez les résultats de la largeur de colonne de l’ajustement automatique de la grille aux données et n’oubliez pas de modifications manuelles si la même requête est exécutée de nouveau.
- Corriger [émettre 1398](https://github.com/Microsoft/azuredatastudio/issues/1398): Show doit ajouter un message et bouton Ajouter un compte lorsque compte lié est vide.
- Corriger [émettre 1399](https://github.com/Microsoft/azuredatastudio/issues/1399): Onglet compte lié est interrompue lorsque la vue est réduite.
- Corriger [émettre 1374](https://github.com/Microsoft/azuredatastudio/issues/1374): Service des outils SQL se bloque lors de l’ouverture du fichier .sql à partir du disque.
- Corriger [émettre 1372](https://github.com/Microsoft/azuredatastudio/issues/1372): Mot clé « BETWEEN » de SQL absent.
- Corriger [émettre 1395](https://github.com/Microsoft/azuredatastudio/issues/1395): Mot clé « Correspondance » bloque de Service des outils SQL.
- Corriger [émettre 1496](https://github.com/Microsoft/azuredatastudio/issues/1496): « Nouvelle Profiler » option de menu contextuel dans l’Explorateur d’objets n’a aucun effet.
- Corriger [émettre 1495](https://github.com/Microsoft/azuredatastudio/issues/1495): Plan de requête de requête éditeur « Explain » est interrompue.

## <a name="may-2018"></a>Mai 2018

Le 7 mai 2018 &nbsp;  /  &nbsp; version : 0.29.3 &nbsp;  /  &nbsp; version préliminaire publique

Le *préliminaire peut* se concentre sur la stabilisation et de correctifs de bogues.

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Annonce l’extension de Redgate SQL Search est disponible dans le Gestionnaire d’extensions. | &nbsp; |
| Localisation de la Communauté disponible dans 10 langues. | Allemand, espagnol, Français, italien, japonais, coréen, portugais, russe, chinois simplifié et chinois traditionnel. |
| Modifications de collection de données de télémétrie. | &bull; &nbsp; Collection de télémétrie réduite.<br/>&bull; &nbsp; Amélioration de l’expérience d’annulations.<br/>&bull; &nbsp; Liens de produit à la déclaration de confidentialité. |
| Gestionnaire d’extensions a amélioré la place de marché d’expérience. | Découvrir plus facilement les extensions de la Communauté. |
| Extension de l’Agent SQL. | &bull; &nbsp; Travaux.<br/>&bull; &nbsp; Amélioration de la vue historique des travaux. |
| Met à jour des extensions pour whoisactive et les rapports de serveur. | &nbsp; |
| Amélioration de défilement de gérer les propriétés de tableau de bord. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fix-github-issues"></a>Résoudre les problèmes de GitHub

- Corriger [émettre 703](https://github.com/Microsoft/azuredatastudio/issues/703): Entrée de texte HTML similaire dans modifier des données entraîne la valeur à afficher incorrectement jusqu'à ce que l’actualisation
- Corriger [émettre 821](https://github.com/Microsoft/azuredatastudio/issues/821): dépendance de package azuredatastudio.deb
- Corriger [émettre 1260](https://github.com/Microsoft/azuredatastudio/issues/1260): Mot clé « distinct » ne pas mis en surbrillance
- Corriger [émettre 1332](https://github.com/Microsoft/azuredatastudio/issues/1332): Modifier des données rétablir ligne ne fonctionne pas
- Corriger [émettre 1215](https://github.com/Microsoft/azuredatastudio/issues/1215): Extension de l’Agent SQL et de la barre d’état
- Corriger [émettre 1316](https://github.com/Microsoft/azuredatastudio/issues/1316): Redimensionnement de SQL Agent n’après modifier la taille de windows

## <a name="april-2018"></a>Avril 2018

Le 25 avril 2018 &nbsp;  /  &nbsp; version : 0.28.6 &nbsp;  /  &nbsp; version préliminaire publique

Le *version préliminaire publique avril* contient des correctifs de bogues et améliorations.

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Améliorations apportées à l’extension de l’aperçu de l’Agent SQL : | &nbsp; |
| &nbsp; &nbsp; &nbsp; Prise en charge améliorée pour les fichiers. | &bull; &nbsp; Fichiers volumineux.<br/>&bull; &nbsp; Les fichiers protégés pour l’enregistrement d’administrateur protégé.<br/>&bull; &nbsp; Stockage \>fichiers 256 M dans SQL Operations Studio. |
| &nbsp; &nbsp; &nbsp; Fractionnement de Terminal intégré. | Travailler avec plusieurs terminaux ouverts simultanément. |
| &nbsp; &nbsp; &nbsp; Installations plus rapides et les temps de démarrage. | Réduction d’installation de fichier sur disque nombre foot impression. |
| &nbsp; | &nbsp; |

### <a name="fix-github-issues-april-2018"></a>Résoudre les problèmes GitHub, avril 2018

- Corriger [émettre 37](https://github.com/Microsoft/azuredatastudio/issues/37): Lorsque la visionneuse de graphique génère une erreur, un comportement inattendu se produit.
- Corriger [émettre 462](https://github.com/Microsoft/azuredatastudio/issues/462): Demande de fonctionnalité : Option pour les groupes de serveurs à être développé par défaut.
- Corriger [émettre 606](https://github.com/Microsoft/azuredatastudio/issues/606): intellisense - suggestion incorrecte pour la commande « update ».
- Corriger [émettre 967](https://github.com/Microsoft/azuredatastudio/issues/967): Attendez le plan de requête lorsque sélectionnez showplan XML dans la grille de résultats.
- Corriger [émettre 1023](https://github.com/Microsoft/azuredatastudio/issues/1023): Ajouter les crochets vides pour l’appel de ms_foreachdb à partir de flyfishingdba.
- Corriger [émettre 1048](https://github.com/Microsoft/azuredatastudio/issues/1048): Erreur lors de la négociation SSL/TLS de préconnexion.
- Corriger [émettre 1050](https://github.com/Microsoft/azuredatastudio/issues/1050): Vue d’insights clair avant d’afficher l’erreur.
- Corriger [émettre 1057](https://github.com/Microsoft/azuredatastudio/issues/1057): Nouvelles actions de requête dans le widget d’explorer et de restauration sont interrompues.
- Corriger [émettre 1068](https://github.com/Microsoft/azuredatastudio/issues/1068): Tableau de bord sortie windows pop-up avec le message d’erreur pour la base de données SQL Azure.
- Corriger [émettre 1069](https://github.com/Microsoft/azuredatastudio/issues/1069): Boîte de dialogue de connexion affiche Erreur de serveur requis lors de l’affichage initial.
- Corriger [émettre 1070](https://github.com/Microsoft/azuredatastudio/issues/1070): À présent, les groupes de serveurs requièrent un double-clic pour développer.
- Corriger [émettre 1072](https://github.com/Microsoft/azuredatastudio/issues/1072): Arrière-plan du contrôle sélectionné est semi-transparent.
- Corriger [émettre 1115](https://github.com/Microsoft/azuredatastudio/issues/1115): Corriger le contraste élevé tous les problèmes d’accessibilité dans SQL Operations Studio.
- Corriger [émettre 1101](https://github.com/Microsoft/azuredatastudio/issues/1101): Échec de l’extension au lien de mise à niveau « télécharger manuellement » va vers un emplacement incorrect.
- Corriger [émettre 1103](https://github.com/Microsoft/azuredatastudio/issues/1103): Défilement V ne fonctionne ne pas dans l’onglet Accueil.
- Corriger [émettre 1104](https://github.com/Microsoft/azuredatastudio/issues/1104): Onglets de l’extension SQL a cessé de fonctionner.

### <a name="visual-studio-code-121-platform"></a>Visual Studio Code 1.21 plateforme

Une mise en surbrillance de la préversion publique avril est l’actualisation du code source pour la plateforme 1.21 de Code Visual Studio. Gagne en plusieurs mises à jour l’éditeur principal et workbench à partir du point de 1.19 synchronisation précédente. Voici quelques exemples :

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| [L’interface utilisateur de nouvelles Notifications](https://code.visualstudio.com/updates/v1_21#_new-notifications-ui). | Gérer et passez en revue les notifications SQL Operations Studio facilement. |
| [Intégré fractionnement Terminal](https://code.visualstudio.com/updates/v1_21#_split-terminals). | Travailler avec plusieurs terminaux ouverts à la fois. |
| [Enregistrer des fichiers volumineux et protégés](https://code.visualstudio.com/updates/v1_20#_save-files-that-need-admin-privileges). | Enregistrer l’administrateur protégé et \>fichiers 256 M dans SQL Operations Studio. |
| [Prise en charge des fichiers volumineux améliorée](https://code.visualstudio.com/updates/v1_21#_text-buffer-improvements). | Optimisations de mémoire tampon de texte pour les fichiers volumineux. |
| [Recherche de paramètres améliorée](https://code.visualstudio.com/updates/v1_20#_settings-search). | Trouvez facilement au paramètre approprié avec la recherche en langage naturel. |
| [Extraits de code globales](https://code.visualstudio.com/updates/v1_20#_global-snippets). | Créer des extraits de code que vous pouvez utiliser pour tous les types de fichier. |
| [Sélection multiple Explorer](https://code.visualstudio.com/updates/v1_20#_multi-select-in-the-explorer). | Effectuer des actions sur plusieurs fichiers à la fois. |
| [Erreurs et avertissements dans l’Explorateur de](https://code.visualstudio.com/updates/v1_20#_error-indicators-in-the-explorer). | Accédez rapidement aux erreurs de votre base de code. |
| [Faites glisser et supprimer, copier et coller entre des fenêtres](https://code.visualstudio.com/updates/v1_21#_better-drag-and-drop-support). | Déplacer des fichiers entre les fenêtres ouvertes de SQL Operations Studio. |
| [Prise en charge du sous-module GIT](https://code.visualstudio.com/updates/v1_20#_git-submodules). | Effectuer des opérations Git sur les référentiels Git imbriquées. |
| [Prise en charge du lecteur de l’écran de terminal](https://code.visualstudio.com/updates/v1_20#_screen-reader-support). | Terminal intégré a maintenant **écran lecteur optimisé** mode. |
| [Mise en page centrée éditeur](https://code.visualstudio.com/updates/v1_21#_centered-editor-layout). | Optimisez votre écran d’affichage du code. |
| [Résultats de la recherche horizontal (version préliminaire)](https://code.visualstudio.com/updates/v1_21#_horizontal-search). | Vous pouvez maintenant l’affichage des résultats dans un volet horizontal. |
| &nbsp; | &nbsp; |

Pour plus d’informations, extraction le [Notes de publication Visual Studio Code février](https://code.visualstudio.com/updates/v1_21)et le [Notes de publication Visual Studio Code janvier](https://code.visualstudio.com/updates/v1_20).

Pour plus d’informations, consultez le [journal des modifications](https://github.com/Microsoft/azuredatastudio/blob/master/CHANGELOG.md).

## <a name="march-2018"></a>Mars 2018

Le 28 mars 2018 &nbsp;  /  &nbsp; version : 0.27.3 &nbsp;  /  &nbsp; version préliminaire publique

Le *version préliminaire publique mars* continue à résoudre les principaux problèmes de GitHub et se concentre sur l’amélioration de notre histoire d’extensibilité. Plus précisément l’activation de gestionnaire d’extensions, amélioration de la gestion du tableau de bord et en fournissant l’Agent SQL et les extensions d’insights. Cette version inclut les améliorations suivantes :

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Améliorer le modèle d’extensibilité de tableau de bord pour prendre en charge des insights à onglets et volets de configuration. | Gestionnaire d’extensions permet simple d’acquisition des extensions.<br/><br/>Extensions de tableau de bord pour sp\_whoisactive de [whoisactive.com](http://www.whoisactive.com).<br/><br/>Pour plus d’informations, consultez [étendre les fonctionnalités de SQL Operations Studio](extensions.md). |
| Ajoutez d’autres [API d’extensibilité pour la connexion et l’objet explorer](https://github.com/Microsoft/azuredatastudio/wiki/Extensibility-API) gestion. | &nbsp; |
| Continuer à résoudre des clients importants ayant un impact sur [problèmes GitHub](https://github.com/Microsoft/azuredatastudio/issues). | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="february-2018"></a>Février 2018

Le 15 février 2018 &nbsp;  /  &nbsp; version : 0.26.7 &nbsp;  /  &nbsp; version préliminaire publique

Le *préliminaire de février* inclut des suggestions de fonctionnalités et les correctifs de bogues de priorité élevée. Cette version inclut les améliorations suivantes :

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Présentation d’Installation de mise à jour automatique, qui fournit une notification lorsqu’une nouvelle version est disponible au téléchargement. | &nbsp; |
| La boîte de dialogue de connexion **base de données** champ est désormais une liste déroulante remplie dynamiquement qui contient une liste de bases de données rempli à partir du serveur spécifié. | &nbsp; |
| Introduire des API d’extensibilité de connexion. | &nbsp; |
| Intégration VS 1.19 d’éditeur de Code. | &nbsp; |
| Mettre à jour les composant JustinPealing/html-plan de requête pour la prise en charge plusieurs améliorations de l’Observateur de Plan de requête. | &nbsp; |
| &nbsp; | &nbsp; |

### <a name="fixed-issues-february-2018"></a>Résolution des problèmes, février 2018

- Corriger [n° 6](https://github.com/Microsoft/azuredatastudio/issues/6): Conserver la connexion et la base de données sélectionnée lors de l’ouverture de nouveaux onglets de requête.
- Corriger [numéro 22](https://github.com/Microsoft/azuredatastudio/issues/22): 'Nom_serveur' et 'Nom de la base de données' - ceux-ci peuvent être des zones de liste déroulante au lieu de zones de texte ?
- Corriger [émettre 549](https://github.com/Microsoft/azuredatastudio/issues/549): Installer sans assistance en mode silencieux/très entraîne l’application qui ouvre après l’installation.
- Corriger [émettre 481](https://github.com/Microsoft/azuredatastudio/issues/481): Ajouter l’option « Vérifier les mises à jour ».
- Colorisation de l’éditeur SQL et les correctifs de la saisie semi-automatique :
  - Corriger [émettre 584](https://github.com/Microsoft/azuredatastudio/issues/584): Mot clé « Complète » ne pas mis en surbrillance par IntelliSense.
  - Corriger [émettre 345](https://github.com/Microsoft/azuredatastudio/issues/345): Colorer les fonctions SQL dans l’éditeur.
  - Corriger [émettre 300](https://github.com/Microsoft/azuredatastudio/issues/300): [#tempData] dernière «] » affichera la couleur verte.
  - Corriger [émettre 225](https://github.com/Microsoft/azuredatastudio/issues/225): Incompatibilité de couleur de mot clé.
  - Corriger [émettre 60](https://github.com/Microsoft/azuredatastudio/issues/60): Sql non valide syntaxe couleur mise en surbrillance lorsque vous utilisez une table temporaire dans la clause from.

## <a name="january-2018"></a>Janvier 2018

Le 17 janvier 2018 &nbsp;  /  &nbsp; version : 0.25.4 &nbsp;  /  &nbsp; version préliminaire publique

Le *préliminaire de janvier* inclut des suggestions de fonctionnalités et les correctifs de bogues de priorité élevée. Cette version inclut les améliorations suivantes :

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Les connexions serveur enregistrées sont disponibles dans la boîte de dialogue de connexion. | &nbsp; |
| Activer la sortie à chaud. Sortie à chaud est désactivée par défaut, pour permettre de voir [paramètre de sortie à chaud](settings.md#hot-exit). | &nbsp; |
| La coloration d’onglet basée sur le groupe de serveurs. La coloration d’onglet est désactivé par défaut, pour permettre de voir [onglet paramètre des couleurs](settings.md#tab-color). | &nbsp; |
| Modification *nom du serveur* à *Server* dans la boîte de dialogue de connexion. | &nbsp; |
| Résoudre interrompu *exécuter la requête actuelle* commande. | &nbsp; |
| Corriger la rupture de glisser-déplacer bogue de script. | &nbsp; |
| Correctif incorrect épinglé icône du Menu Démarrer. | &nbsp; |
| Corriger le compte Azure manquant icône de marque. | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="december-2017"></a>Décembre 2017

Le 19 décembre 2017 &nbsp;  /  &nbsp; version : 0.24.1 &nbsp;  /  &nbsp; version préliminaire publique

Le *préliminaire de décembre* comprend plusieurs correctifs de bogues sur toutes les zones de fonctionnalité, ainsi que les améliorations suivantes :

&nbsp;

| Modifier | Détails |
| :----- | :------ |
| Créer boîte de dialogue règle de pare-feu est désormais disponible pour faciliter la connexion à la base de données SQL Azure et Azure SQL Data Warehouse. | &nbsp; |
| Ajouté le programme d’installation Windows et les packages d’installation Linux DEB et tr/min. | &nbsp; |
| Gérer l’éditeur de disposition visuelle du tableau de bord. | &nbsp; |
| *Script en tant que Alter* et *Script comme exécuter* commandes. | &nbsp; |
| *Exécutez la requête en cours avec le Plan réel* commande. | &nbsp; |
| Intégrer la plateforme d’éditeur Visual Studio Code 1.18.1. | &nbsp; |
| Activer les fichiers de chargement de version test d’une Extension VSIX. | &nbsp; |
| Prend en charge la syntaxe d’itération lot « GO N ». | &nbsp; |
| &nbsp; | &nbsp; |

## <a name="november-2017"></a>Novembre 2017

Le 15 novembre 2017 &nbsp;  /  &nbsp; version : 0.23.6

- Version initiale du [!INCLUDE[name-sos](../includes/name-sos-short.md)].

## <a name="next-steps"></a>Étapes suivantes

Consultez les Démarrages rapides suivants pour commencer :

- [Connexion & interrogation de SQL Server](quickstart-sql-server.md)
- [Connexion & interrogation de base de données SQL Azure](quickstart-sql-database.md)
- [Connexion & interrogation d’entrepôt de données Azure](quickstart-sql-dw.md)

Contribuer à [!INCLUDE[name-sos](../includes/name-sos-short.md)]:

- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio)
