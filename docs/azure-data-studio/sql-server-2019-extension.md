---
title: Extension SQL Server 2019 (préversion)
titleSuffix: Azure Data Studio
description: Extension SQL Server 2019 en préversion pour Azure Data Studio
ms.custom: seodec18
ms.date: 06/25/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 9b25fd044b94e21151b687d428c469a12d8c8a5d
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959217"
---
# <a name="sql-server-2019-extension-preview"></a>Extension SQL Server 2019 (préversion)

L’extension SQL Server 2019 (préversion) fournit une prise en charge préliminaire des nouvelles fonctionnalités et des nouveaux outils fournis pour [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. Cela comprend la prise en charge de l’aperçu pour les [clusters Big Data SQL Server 2019](../big-data-cluster/big-data-cluster-overview.md), une [expérience de notebook](../big-data-cluster/notebooks-guidance.md) intégrée et un [assistant PolyBase Créer une table externe](../relational-databases/polybase/data-virtualization.md?toc=/sql/toc/toc.json).

## <a name="install-the-sql-server-2019-extension-preview"></a>Installation de l’extension SQL Server 2019 en préversion

Pour installer l’extension SQL Server 2019 (préversion), téléchargez et installez le fichier .vsix associé.

1. Téléchargez le fichier .vsix de l’extension SQL Server 2019 (préversion) dans un répertoire local :

   |Plateforme|Télécharger|Date de publication|Options de version
   |:---|:---|:---|:---|
   |Windows|[.vsix](https://go.microsoft.com/fwlink/?linkid=2097803)|25 juin 2019 |0.14.1
   |macOS|[.vsix](https://go.microsoft.com/fwlink/?linkid=2097802)|25 juin 2019 |0.14.1
   |Linux|[.vsix](https://go.microsoft.com/fwlink/?linkid=2097801)|25 juin 2019 |0.14.1

1. Dans Azure Data Studio choisissez **Installer l’extension à partir du package VSIX** dans le menu **Fichier**, puis sélectionnez le fichier. vsix téléchargé.

1. Choisissez **Oui** lorsque vous êtes invité à confirmer l’installation, puis attendez la notification indiquant que l’installation a réussi.

1. Sélectionnez **Recharger** pour activer l’extension (nécessaire uniquement la première fois que vous installez une extension).

1. Après le rechargement, l’extension installe les dépendances. Vous pouvez voir la progression dans la fenêtre de sortie, ce qui peut prendre plusieurs minutes.

1. Une fois l’installation des dépendances terminée, fermez et rouvrez Azure Data Studio. Le type de connexion **Cluster Big Data SQL Server** n’est pas disponible tant que vous n’avez pas redémarré Azure Data Studio.

## <a name="changes-in-release-0141"></a>Modifications dans la version 0.14.1
* Prise en charge de la prise en charge de la source de données CTP 3.1

## <a name="changes-in-release-0121"></a>Modifications dans la version 0.12.1

* Le type de connexion **Cluster Big Data SQL Server** a été supprimé dans cette version. Toutes les fonctionnalités précédemment disponibles à partir de la connexion Big Data SQL Server sont désormais disponibles dans la connexion SQL Server.
* La navigation HDFS se trouve dans le dossier **Data Services**
* Pour les notebooks, le PySpark et les autres noyaux de Big Data fonctionnent lorsqu’ils sont connectés à l’instance SQL Server maître dans votre cluster Big Data SQL Server.
* Assistant Créer une table externe :
  * Prise en charge de la création d’une table externe à l’aide d’une source de données externe existante.
  * Améliorations des performances à travers l’assistant.
  * Amélioration de la gestion des noms d’objets avec des caractères spéciaux. Dans certains cas, ces derniers provoquaient l’échec de l’assistant
  * Améliorations de la fiabilité de la page Mappage d’objets.
  * Suppression des bases de données système « DWConfiguration », « DWDiagnostics », « DWQueue » dans la liste déroulante des bases de données.
  * Prise en charge de la définition du nom de l’objet de format de fichier externe dans l'assistant **Création d’une table externe à partir de fichiers CSV**.
  * Ajout d’un bouton Actualiser à la première page de l’assistant **Créer une table externe à partir de fichiers CSV**.

## <a name="release-notes-v0110"></a>Notes de publication (v0.11.0)

* La prise en charge de Jupyter Notebook, en particulier la prise en charge des noyaux Python3 et Spark, a été déplacée dans Azure Data Studio. Cette extension n’est plus nécessaire pour pouvoir utiliser des notebooks.
* Plusieurs correctifs de bogues dans les assistants de données externes :
  * Les mappages de types Oracle ont été mis à jour pour correspondre aux modifications fournies dans SQL Server 2019 CTP 2.3.
  * Correction d’un problème où les nouveaux schémas saisis dans les contrôles de mappage de table étaient perdus.
  * Résolution d’un problème où la vérification d’un nœud de base de données dans les mappages de tables n’aboutissait pas à la vérification de toutes les tables et vues.


## <a name="release-notes-v0102"></a>Notes de publication (v0.10.2)
### <a name="sql-server-2019-support"></a>Prise en charge de SQL Server 2019
La prise en charge de SQL Server 2019 a été mise à jour. Lors de la connexion à une instance de cluster Big Data SQL Server Big Data, un nouveau dossier _Data Services_ s’affiche dans l’arborescence de l’explorateur. Il possède des points de lancement pour des actions telles que l’ouverture d’un nouveau notebook sur la connexion, l’envoi de travaux Spark et l’utilisation de HDFS. Notez que pour certaines actions, telles que la _Création de données externes_ à partir d’un fichier/dossier HDFS , l’extension _SQL Server 2019 (préversion)_ doit être installée.

### <a name="notebook-support"></a>Prise en charge des notebooks
Nous avons apporté des mises à jour significatives à l’interface utilisateur du notebook dans cette version. Notre objectif était de faciliter la lecture des notebooks partagés avec vous. Cela signifiait la suppression de toutes les zones de contour autour des cellules, sauf si elles sont sélectionnées ou survolées, l’ajout de la prise en charge du pointage pour les actions sur des cellules uniques sans avoir besoin de sélectionner une cellule, la clarification de l’état d’exécution en ajoutant le nombre d’exécutions, un bouton _arrêter l’exécution_ animé et bien plus encore. Nous avons également ajouté des raccourcis clavier pour _Nouveau notebook_ (`Ctrl+Shift+N`), _Exécuter la cellule_ (`F5`),_Nouvelle cellule de code_ (`Ctrl+Shift+C`), _Nouvelle cellule de texte_ (`Ctrl+Shift+T`). Par la suite, nous allons faire en sorte que toutes les actions clés puissent être lancées par raccourci.

Parmi les autres améliorations et correctifs figurent les suivants :
* L’extension _SQL Server 2019 (préversion)_ vous invite désormais à choisir un répertoire d’installation pour les dépendances Python. En outre, Python n’est plus inclus dans le `.vsix file`, ce qui réduit la taille globale de l’extension. Les dépendances Python sont nécessaires pour prendre en charge les noyaux Spark et Python3. L’installation de cette extension est donc nécessaire pour les utiliser.
* La prise en charge du lancement d’un nouveau notebook à partir de la ligne de commande a été ajoutée. Le lancement avec les arguments `--command=notebook.command.new --server=myservername` doit ouvrir un nouveau notebook et se connecter à ce serveur.
* Correctifs de performances pour les notebooks avec une longueur de code conséquente dans les cellules. Si les cellules de code se trouvent sur 250 lignes, une barre de défilement est ajoutée.
* Prise en charge améliorée des fichiers .ipynb. Les versions 3 et ultérieures sont désormais prises en charge. Notez que, lors de l’enregistrement des fichiers, ces derniers sont mis à jour vers la version 4 ou ultérieure.
* Le paramètre utilisateur `notebook.enabled` a été supprimé maintenant que la visionneuse de notebooks intégrée est stable
* Un thème à contraste élevé est désormais pris en charge avec un certain nombre de correctifs pour la disposition des objets dans ce cas.
* Correction du problème #3680 où les sorties affichaient parfois certains caractères `,,,` de manière incorrecte
* Correction du problème #3602, quand l’éditeur disparaissait pour les cellules après avoir quitté Azure Data Studio
* La prise en charge a été ajoutée pour utiliser des vues de grille pour le type MIME de sortie `application/vnd.dataresource+json`. Cela signifie que de nombreux notebooks qui l’utilisent (par exemple en définissant `pd.options.display.html.table_schema` dans un notebook Python) présentent des sorties tabulaires plus attrayantes. Correction du problème #3959, où Azure Data Studio tentait d’arrêter le serveur de notebook deux fois après la fermeture du notebook

#### <a name="known-issues"></a>Problèmes connus
* La boîte de dialogue d’installation de Python s’affiche à l’ouverture d’un notebook. Si vous annulez cette installation, les listes déroulantes Noyaux et Attacher à n’affichent pas les valeurs attendues. Une solution de contournement consiste à effectuer l’installation de Python.
* Lorsqu’un notebook est ouvert avec un noyau qui n’est pas pris en charge, les listes déroulantes Noyaux et _Attacher à_ provoquent le blocage d’Azure Data Studio. Vous devez fermer Azure Data Studio et vous assurer que vous utilisez un noyau pris en charge (Python3, Spark | R, Spark | Scala, PySpark, PySpark3)
* La liaison à l’interface utilisateur Spark échoue lors de l’utilisation de PySpark3 ou d’autres noyaux Spark sur le point de terminaison SQL Server. Pour résoudre ce problème, cliquez sur interface utilisateur Spark dans le tableau de bord ou connectez-vous à l’aide du type de connexion cluster Big Data SQL Server, car le lien hypertexte de l’interface utilisateur Spark est correct

### <a name="extensibility-improvements"></a>Améliorations de l’extensibilité
Un certain nombre d’améliorations ont été apportées à cette version pour aider les extendeurs
* Une nouvelle API `ObjectExplorerNodeProvider` permet aux extensions de contribuer aux dossiers sous SQL Server ou d’autres nœuds de connexion. C’est ainsi que le nœud `Data Services` est ajouté sous les instances SQL Server 2019, mais il peut être utilisé pour ajouter facilement la surveillance ou d’autres dossiers à l’interface utilisateur.
* Deux nouvelles valeurs de clé de contexte sont disponibles pour vous aider à afficher/masquer les contributions au tableau de bord.
  * `mssql:iscluster` indique s’il s’agit d’un cluster Big Data SQL Server 2019
  * `mssql:servermajorversion` possède la version serveur (15 pour SQL Server 2019, 14 pour SQL Server 2017, etc.). Cela peut s’avérer utile si les fonctionnalités ne doivent être affichées que pour SQL Server 2017 ou une version ultérieure, par exemple.


## <a name="release-notes-v080"></a>Notes de publication (v0.8.0)
*Notebooks* :
* L’ajout de cellules avant/après les cellules existantes est désormais pris en charge en cliquant sur le bouton de cellule « Autres actions »
* L’option **Ajouter une nouvelle connexion** a été ajoutée aux connexions dans la liste déroulante « Attacher à »
* Une commande **Réinstaller les dépendances du notebook** a été ajoutée pour faciliter les mises à jour des packages Python et résoudre les cas où l’installation a été interrompue par la fermeture de l’application. Elle peut être exécutée à partir de la palette de commandes (utilisez `Ctrl/Cmd+Shift+P` et saisissez `Reinstall Notebook Dependencies`)
* Le package Python PROSE a été mis à jour vers la version 1.1.0 et inclut un certain nombre de correctifs de bogues. Utilisez la commande **Réinstaller les dépendances du notebook** pour mettre à jour ce package
* Une commande **Effacer la sortie** est maintenant prise en charge en cliquant sur le bouton de cellule **Autres actions**
* Correction des problèmes signalés par les clients suivants :
  * La session du notebook ne peut pas démarrer sur Windows en raison de problèmes de chemin
  * Impossible de démarrer le notebook à partir du dossier racine d’un lecteur, par exemple C:\ ou D:\
  * [#2820](https://github.com/Microsoft/azuredatastudio/issues/2820) impossible de modifier les notebooks créés à partir d’ADS dans VS Code
  * La liaison de l’interface utilisateur Spark fonctionne maintenant lors de l’exécution d’un noyau Spark
  * « Packages gérés » renommés en « Packages d’installation »

*Créer des données externes* :

* Les messages d’erreur peuvent être copiés et ont été séparés entre un affichage résumé et une vue détaillée
* Amélioration de la disposition de l’interface utilisateur et amélioration significative de la fiabilité et de la gestion des erreurs
* Correction des problèmes signalés par les clients suivants :
  * Les tables avec des mappages de colonnes non valides sont indiquées comme étant désactivées et un avertissement explique l’erreur

## <a name="release-notes-v072"></a>Notes de publication (v0.7.2)
* Azure Resource Explorer est maintenant intégré à Azure Data Studio et a été supprimé de cette extension. Merci pour vos commentaires à ce sujet !
* Amélioration des performances des notebooks avec de nombreuses cellules Markdown.
* Dimensionnement automatiquement des cellules de code dans le notebook. Elles ont toujours une taille minimale basée sur la barre d’outils de la cellule.
* Notification à l’utilisateur lors de l’installation des dépendances du notebook. Sur Windows, en particulier, cela peut prendre beaucoup de temps, aussi les notifications s’affichent maintenant dans la vue Tâches.
* Prise en charge de la réinstallation des dépendances de notebook. Cela est utile si l’utilisateur a précédemment fermé Azure Data Studio lors de l’installation.
* Prise en charge de l’annulation de l’exécution des cellules dans le notebook.
* Amélioration de la fiabilité lors de l’utilisation de l’assistant Création de données externes, en particulier lorsque des erreurs de connexion se produisent.
* Blocage de l’utilisation de l’assistant Création de données externes si PolyBase n’est pas activé ou est en cours d’exécution sur le serveur cible.
* Correction de l’orthographe et de l’attribution des noms pour SQL Server 2019 et la création des données externes.
* Suppression d’un grand nombre d’erreurs dans la console de débogage d’Azure Data Studio.

##  <a name="sql-server-2019-big-data-cluster-support"></a>Prise en charge des clusters de Big Data SQL Server 2019

* Cliquez sur **Ajouter une connexion** dans l’*Explorateur d’objets*, puis choisissez **Cluster Big Data SQL Server** comme type de connexion.

   > [!TIP]
   > Si vous ne voyez pas le type de connexion **Cluster Big Data SQL Server**, redémarrez Azure Data Studio.

* Entrez le nom d’hôte ou l’adresse IP du point de terminaison du cluster, ainsi que le nom d’utilisateur & mot de passe utilisés pour vous connecter.
* Si vous le souhaitez, incluez un nom d'affichage convivial dans le champ **Nom**.
* Cliquez sur **Connexion**. Vous pouvez ensuite lancer des tâches courantes à partir du tableau de bord, parcourir **HDFS** dans l’Explorateur d’objets et exécuter des tâches en contexte à partir de là.
* Pour envoyer un travail Spark au cluster, cliquez avec le bouton droit sur le nœud du serveur dans l’*Explorateur d’objets*, puis choisissez **Envoyer un travail Spark** pour afficher la boîte de dialogue d’envoi.
* Pour ouvrir un notebook, consultez la section suivante.

Pour plus d’informations, consultez [Clusters Big Data](../big-data-cluster/big-data-cluster-overview.md).


## <a name="azure-data-studio-notebooks"></a>Notebooks Azure Data Studio

* Ouvrez un notebook de l’une des manières suivantes :
  * Ouvrez un nouveau notebook à partir dans la *Palette de commandes*.
  * Ouvrez l’arborescence de l’explorateur d’objets HDFS pour un cluster Big Data SQL Server 2019 et :
    * Cliquez avec le bouton droit sur le nœud du serveur, puis choisissez **Nouveau Jupyter Notebook**.
    * Cliquez avec le bouton droit sur un fichier CSV, puis choisissez **Analyser dans le notebook**.
  * Ouvrez un fichier .ipynb existant à partir du menu **Fichier** ou de l’Explorateur de fichiers *(les fichiers .ipynb doivent être mis à niveau vers la version 4 ou ultérieure pour pouvoir être chargés correctement)*
* Choisissez un noyau. Pour l’exécution locale du notebook, choisissez Python 3. Pour l’exécution à distance, choisissez PySpark ou Spark | Scala.
* Choisissez un point de terminaison de cluster Big Data SQL Server auquel se connecter en cas d’exécution à distance (cela n’est pas nécessaire pour le développement local avec Python 3).
* Ajoutez des cellules de code ou Markdown à l’aide des boutons de l’en-tête du notebook. Supprimez les cellules avec l’icône Corbeille à gauche de chaque cellule.
* Exécutez des cellules avec le bouton de lecture pour les cellules de code et activez/désactivez l’édition et l’aperçu de Markdown avec l’icône d’œil

## <a name="polybase-create-external-table-wizard"></a>Assistant Créer une table externe PolyBase

* À partir d’une instance SQL Server 2019, *l’assistant Créer une table externe* peut être ouvert de trois manières :
  * Cliquez avec le bouton droit sur un serveur, choisissez **Gérer**, cliquez sur l’onglet correspondant pour SQL Server 2019 (version préliminaire), puis choisissez **Créer une table externe**.
  * Avec une instance SQL Server 2019 sélectionnée dans *l’Explorateur d’objets*, affichez *Créer un assistant externe* via la *Palette de commandes*.
  * Cliquez avec le bouton droit sur une base de données SQL Server 2019 dans *l’Explorateur d’objets* et choisissez **Créer une table externe**.
* Dans cette version de l’extension, il est possible de créer des tables externes pour accéder aux tables SQL Server et Oracle à distance.

  > [!NOTE]
  > Bien que la fonctionnalité de table externe soit une fonctionnalité de SQL 2019, l’instance SQL Server distante peut exécuter une version antérieure de SQL Server.

* Indiquez si vous accédez à SQL Server ou Oracle sur la première page de l’assistant et continuez.
* Vous serez invité à créer une clé principale de base de données si celle-ci n’a pas encore été créée (les mots de passe de complexité insuffisante sont bloqués).
* Créez une connexion à la source de données et les informations d’identification nommées pour le serveur distant.
* Choisissez les objets à mapper à votre nouvelle table externe.
* Choisissez **Générer un script** ou **Créer** pour terminer l’assistant.
* Après la création de la table externe, elle apparaît immédiatement dans l’arborescence d’objets de la base de données où elle a été créée.


## <a name="known-issues"></a>Problèmes connus

* Si le mot de passe n’est pas enregistré lors de la création d’une connexion, certaines actions, telles que l’envoi du travail Spark, peuvent échouer.
* Les notebooks .ipynb existants doivent être mis à niveau vers la version 4 ou une version ultérieure pour charger le contenu dans la visionneuse.
* L’exécution de la commande **Réinstaller les dépendances du notebook** peut afficher 2 tâches dans la vue des tâches, dont une échoue. Cela n’entraîne pas l’échec de l’installation
* Si vous choisissez **Ajouter une nouvelle connexion** dans un notebook et cliquez sur Annuler, l’option **Sélectionner la connexion** s’affiche, même si vous êtes déjà connecté.
