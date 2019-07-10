---
title: Extension de SQL Server 2019 (version préliminaire)
titleSuffix: Azure Data Studio
description: Extension de la version préliminaire de SQL Server 2019 pour Azure Data Studio
ms.custom: seodec18
ms.date: 06/25/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: jroth
ms.openlocfilehash: bc865b36dc8b8036fa9a6a1a9c58c6890acadf47
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67681606"
---
# <a name="sql-server-2019-extension-preview"></a>Extension de SQL Server 2019 (version préliminaire)

L’extension de SQL Server 2019 (version préliminaire) fournit la prise en charge de la version préliminaire pour les nouvelles fonctionnalités et outils de livraison à l’appui de [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. Cela inclut la prise en charge de la version préliminaire de [clusters de données volumineuses de SQL Server 2019](../big-data-cluster/big-data-cluster-overview.md), intégré [expérience de bloc-notes](../big-data-cluster/notebooks-guidance.md)et un PolyBase [Assistant de Create External Table](../relational-databases/polybase/data-virtualization.md?toc=/sql/toc/toc.json).

## <a name="install-the-sql-server-2019-extension-preview"></a>Installer l’extension de SQL Server 2019 (version préliminaire)

Pour installer l’extension de SQL Server 2019 (version préliminaire), télécharger et installer le fichier .vsix associé.

1. Télécharger le fichier .vsix d’extension (version préliminaire) SQL Server 2019 dans un répertoire local :

   |Plateforme|Télécharger|Date de publication|Version
   |:---|:---|:---|:---|
   |Windows|[.vsix](https://go.microsoft.com/fwlink/?linkid=2097803)|25 juin 2019 |0.14.1
   |macOS|[.vsix](https://go.microsoft.com/fwlink/?linkid=2097802)|25 juin 2019 |0.14.1
   |Linux|[.vsix](https://go.microsoft.com/fwlink/?linkid=2097801)|25 juin 2019 |0.14.1

1. Dans Azure Data Studio choisissez **installer l’Extension à partir du Package VSIX** à partir de la **fichier** menu et sélectionnez le fichier .vsix téléchargé.

1. Choisissez **Oui** lorsque vous êtes invité à confirmer l’installation et attendre la notification de l’installation a réussi.

1. Sélectionnez **recharger** pour activer l’extension (uniquement obligatoire la première fois que vous installez une extension).

1. Après le rechargement, l’extension installera les dépendances. Vous pouvez voir la progression dans la fenêtre Sortie, et il peut prendre plusieurs minutes.

1. Une fois les dépendances de terminer l’installation, fermez et rouvrez Studio de données Azure. Le **cluster de données volumineux de SQL Server** type de connexion n’est pas disponible tant que vous ne redémarrez Azure Data Studio.

## <a name="changes-in-release-0141"></a>Modifications apportées à la version 0.14.1
* Prise en charge pour la prise en charge de source de données CTP 3.1

## <a name="changes-in-release-0121"></a>Modifications apportées à la version 0.12.1 de version

* Le **cluster de données volumineux de SQL Server** type de connexion a été supprimé dans cette version. Toutes les fonctionnalités précédemment disponibles à partir de la connexion au cluster volumineuses de données SQL Server sont maintenant disponible dans la connexion SQL Server.
* HDFS de navigation se trouve sous le **Data Services** dossier
* Pour les blocs-notes le noyaux PySpark et autres données volumineuses fonctionne lorsque connecté à l’instance principale de SQL Server dans votre cluster de données volumineux de SQL Server.
* Créer un Assistant de Table externe :
  * Prise en charge pour la création d’une Table externe à l’aide de la Source de données externe existante.
  * Améliorations des performances dans l’Assistant.
  * Amélioration de la gestion des noms d’objet avec des caractères spéciaux. Dans certains cas, ces a provoqué l’Assistant Échec
  * Améliorations de la fiabilité de la page mappage de l’objet.
  * Supprimé bases de données système - 'DWConfiguration', 'DWDiagnostics', « DWQueue - » dans la liste déroulante de bases de données.
  * Prise en charge pour la définition du nom de l’objet de Format de fichier externe dans le **Create External Table à partir de fichiers CSV** Assistant.
  * Ajouter un bouton d’actualisation pour la première page de la **Create External Table à partir de fichiers CSV** Assistant.

## <a name="release-notes-v0110"></a>Notes de publication (v0.11.0)

* Prise en charge de bloc-notes Jupyter, spécifiquement prennent en charge pour les noyaux Python3 et Spark a été déplacée dans Azure Data Studio. Cette extension n’est plus requise pour pouvoir utiliser des blocs-notes.
* Plusieurs correctifs de bogues dans les Assistants de données externes :
  * Mappages de type Oracle ont été mis à jour pour refléter les modifications fournies dans SQL Server 2019 CTP 2.3.
  * Correction d’un problème où de nouveaux schémas tapés dans les contrôles de mappage de table ont été perdus.
  * Correction d’un problème où la vérification d’un nœud de base de données dans les mappages de table n’ont pas généré dans toutes les tables et vues en cours de vérification.


## <a name="release-notes-v0102"></a>Notes de publication (v0.10.2)
### <a name="sql-server-2019-support"></a>Prise en charge de SQL Server 2019
Prise en charge de SQL Server 2019 a été mis à jour. Sur la connexion à un Cluster de données volumineuses de SQL Server instance un nouveau _Data Services_ dossier s’affiche dans l’arborescence de l’Explorateur. Cela a des points de lancement pour les actions telles que l’ouverture d’un nouveau bloc-notes par rapport à la connexion, envoi de travaux Spark et l’utilisation de HDFS. Notez que, pour certaines actions comme _créer des données externes_ sur un fichier/dossier HDFS, le _SQL Server 2019 Preview_ extension doit être installée.

### <a name="notebook-support"></a>Prise en charge du bloc-notes
Nous avons apporté des mises à jour importantes à l’interface utilisateur de bloc-notes dans cette version. Notre objectif était de rend facile à lire des ordinateurs portables qui sont partagés avec vous. Cela signifiait suppression tous décrivent des zones autour des cellules, sauf si sélectionné ou Survolé, ajout de prise en charge de pointage pour les actions au niveau des cellules simples sans nécessiter sélectionner une cellule et à clarifier l’état d’exécution en ajoutant le nombre d’exécutions, animée _arrêt en cours d’exécution_ bouton et bien plus encore. Nous avons également ajouté des raccourcis clavier pour _nouveau bloc-notes_ (`Ctrl+Shift+N`), _cellule exécuter_ (`F5`), _nouvelle cellule de Code_ (`Ctrl+Shift+C`),  _Nouvelle cellule de texte_ (`Ctrl+Shift+T`). À l’avenir que nous cherchera à avoir toutes les actions clées accessible par raccourci faites-nous donc savoir ce que vous ratez !

Autres correctifs et améliorations sont les suivantes :
* Le _SQL Server 2019 Preview_ extension maintenant invites utilise pour choisir un répertoire d’installation pour les dépendances de Python. Il n’est plus inclut également Python dans le `.vsix file`, ce qui réduit la taille globale de l’extension. Les dépendances de Python sont nécessaires pour prendre en charge les noyaux Spark et Python3, installez cette extension n’est requis pour utiliser ces.
* Prise en charge pour le lancement d’un nouveau bloc-notes à partir de la ligne de commande a été ajoutée. Avec les arguments de lancement `--command=notebook.command.new --server=myservername` doit s’ouvrir un nouveau bloc-notes et se connecter à ce serveur.
* Correctifs des performances pour les blocs-notes avec une longueur de code volumineux dans les cellules. Si les cellules de code sont plus de 250 lignes qu'ont ajouté une barre de défilement.
* Prise en charge des fichiers .ipynb améliorée. Version 3 ou version ultérieure est désormais prise en charge. Veuillez noter que lors de l’enregistrement de fichiers sera être mis à jour vers la version 4 ou version ultérieure.
* Le `notebook.enabled` paramètre utilisateur a été supprimé maintenant intégrée dans le bloc-notes visionneuse est stable
* Thème à contraste élevé est désormais pris en charge un nombre de correctifs à la disposition des objets dans ce cas.
* Correction 3680 # où sorties présentait parfois un nombre de `,,,` caractères de manière incorrecte
* Correction #3602 que disparaît de l’éditeur pour les cellules après avoir quitté studio de données azure
* Prise en charge a été ajoutée à utiliser les vues de la grille pour la `application/vnd.dataresource+json` type MIME de la sortie. Cela signifie que de nombreux ordinateurs portables qui utilisent ce (par exemple en définissant `pd.options.display.html.table_schema` dans une instance Python notebook) aura mieux sorties sous forme de tableau fixe #3959 Azure Data Studio essaie d’arrêter le serveur de bloc-notes à deux reprises après la fermeture de bloc-notes

#### <a name="known-issues"></a>Problèmes connus
* Lors de l’ouverture d’un ordinateur portable, la boîte de dialogue Installation python s’affiche. L’annulation de cette installation entraîne les noyaux et joindre aux listes déroulantes s’affichent ne pas les valeurs attendues. La solution de contournement consiste à terminer l’installation de Python.
* Lorsqu’un ordinateur portable est ouvert avec un noyau n’est pas pris en charge, les noyaux et _attacher à_ listes déroulantes provoque un Studio de données Azure ne répond plus. Vous devrez fermer Azure Data Studio et vérifiez que vous utilisez un noyau est prise en charge (Python3, Spark | R, Spark | Scala, PySpark, PySpark3)
* Échec de la liaison de l’interface utilisateur Spark lorsque vous utilisez PySpark3 ou autres noyaux Spark sur le point de terminaison de SQL Server. Pour résoudre ce problème, veuillez cliquer sur l’interface utilisateur Spark à partir du tableau de bord, ou connectez-vous en utilisant le type de connexion de cluster SQL Server données volumineuses comme cela aura le lien hypertexte de l’interface utilisateur Spark correct

### <a name="extensibility-improvements"></a>Améliorations de l’extensibilité
Un certain nombre d’améliorations qui aident les extendeurs ont été ajouté dans cette version
* Un nouveau `ObjectExplorerNodeProvider` API permet aux extensions de contribuer dossiers sous SQL Server ou d’autres nœuds de la connexion. Voici comment la `Data Services` nœud est ajouté sous les instances de SQL Server 2019 mais pouvait être utilisé pour ajouter facilement des dossiers de surveillance ou d’autres à l’interface utilisateur.
* Deux nouvelles valeurs clés de contexte sont disponibles pour aider à afficher/masquer les contributions au tableau de bord.
  * `mssql:iscluster` Indique s’il s’agit d’un Cluster SQL Server 2019 Big Data
  * `mssql:servermajorversion` a la version du serveur (15 pour SQL Server 2019, 14 pour SQL Server 2017 et ainsi de suite). Cela peut être utile si les fonctionnalités doivent uniquement être affichées pour SQL Server 2017 ou supérieur, par exemple.


## <a name="release-notes-v080"></a>Notes de publication (v0.8.0)
*Blocs-notes*:
* Ajout de cellules avant / après existant cellules est maintenant possible en cliquant sur le bouton de la cellule « Plus d’Actions »
* **Ajouter une nouvelle connexion** option a été ajoutée pour les connexions dans la liste déroulante « Attacher à »
* Un **réinstaller les dépendances de bloc-notes** commande a été ajoutée pour faciliter les mises à jour du package Python et résoudre les cas où installer a été interrompue en cours via en fermant l’application. Cela peut être exécuté à partir de la palette de commandes (utilisez `Ctrl/Cmd+Shift+P` et type `Reinstall Notebook Dependencies`)
* Le package python PROSE a été mis à jour vers la version 1.1.0, et inclut un certain nombre de correctifs de bogues. Utilisez le **réinstaller les dépendances de bloc-notes** commande pour mettre à jour de ce package
* Un **effacer la sortie** commande est désormais prise en charge en cliquant sur le **autres Actions** bouton de la cellule
* Correction de ce qui suit client signalé des problèmes :
  * Session de bloc-notes pas pu démarrer sur Windows en raison de problèmes de chemin d’accès
  * Ordinateur portable n’a pas pu être démarré à partir du dossier racine d’un lecteur, tel que C:\ ou D:\
  * [#2820](https://github.com/Microsoft/azuredatastudio/issues/2820) Impossible de modifier les blocs-notes créés à partir de publicités dans VS Code
  * Lien de l’interface utilisateur Spark fonctionne désormais lors de l’exécution d’un noyau Spark
  * Renommé « Géré par les Packages » à « Installer les Packages »

*Créer des données externes*:

* Messages d’erreur peuvent être copiés et ont été séparées dans une vue de synthèse ou détaillée pour facilement
* Disposition de l’interface utilisateur améliorée et considérablement amélioré et une gestion des erreurs
* Correction de ce qui suit client signalé des problèmes :
  * Tables avec les mappages de colonnes non valides sont affichés comme étant désactivés et un avertissement décrit l’erreur

## <a name="release-notes-v072"></a>Notes de publication (v0.7.2)
* Explorateur de ressources Azure est désormais intégré à Azure Data Studio et a été supprimé de cette extension. Nous vous remercions pour vos commentaires sur ce !
* Amélioration des performances des ordinateurs portables avec beaucoup de cellules Markdown.
* Cellules de code de redimensionnement automatique dans le bloc-notes. Cela a toujours une taille minimale basée sur la barre d’outils de la cellule.
* Informez l’utilisateur lors de l’installation des dépendances de bloc-notes. Sur Windows cela peut en particulier prendre beaucoup de temps, afin de notifications sont maintenant affichées dans la vue tâches.
* Prise en charge la réinstallation des dépendances de bloc-notes. Cela est utile si l’utilisateur précédemment fermés Azure Data Studio en cours via l’installation.
* Prise en charge l’annulation de l’exécution de cellule dans le bloc-notes.
* Fiabilité améliorée lorsque vous utilisez l’Assistant de création de données externe, en particulier lorsque les erreurs de connexion se produisent.
* Bloquer l’utilisation de l’Assistant de création de données externe si PolyBase n’est pas activé ni en cours d’exécution sur le serveur cible.
* Vérificateur d’orthographe et d’affectation de noms correctifs liés à SQL Server 2019 et créer des données externes.
* Supprimé un grand nombre d’erreurs à partir de la console de débogage Azure Data Studio.

##  <a name="sql-server-2019-big-data-cluster-support"></a>Prise en charge du Cluster de données volumineuses de SQL Server 2019

* Cliquez sur **ajouter une connexion** dans *Explorateur d’objets* et choisissez **cluster de données volumineux de SQL Server** comme type de connexion.

   > [!TIP]
   > Si vous ne voyez pas le **cluster de données volumineux de SQL Server** type de connexion, redémarrez Studio de données Azure.

* Entrez le nom d’hôte ou l’adresse IP du point de terminaison de cluster plus le nom d’utilisateur et le mot de passe utilisé pour se connecter.
* Si vous le souhaitez, inclure un nom d’affichage convivial dans le **nom** champ.
* Cliquez sur **Connect** , vous pouvez ensuite lancer des tâches courantes du tableau de bord, parcourir **HDFS** dans l’Explorateur d’objets et d’exécution des tâches en contexte à partir de là.
* Pour soumettre un travail Spark sur le cluster, cliquez sur le nœud du serveur dans *Explorateur d’objets* et choisissez **soumettre un travail Spark** pour afficher la boîte de dialogue de soumission.
* Pour ouvrir un bloc-notes, consultez la section suivante.

Pour plus d’informations, consultez [Big Data Clusters](../big-data-cluster/big-data-cluster-overview.md).


## <a name="azure-data-studio-notebooks"></a>Azure Data Studio blocs-notes

* Ouvrez un bloc-notes dans une des manières suivantes :
  * Ouvrez un nouveau bloc-notes à partir de la *Palette de commandes*.
  * Ouvrez l’arborescence de l’Explorateur d’objets HDFS pour un cluster de données volumineux de SQL Server 2019 et soit :
    * Cliquez avec le bouton droit sur le nœud du serveur et choisissez **nouveau bloc-notes Jupyter**.
    * Cliquez avec le bouton droit sur un fichier CSV, puis choisissez **analyser dans le bloc-notes**.
  * Ouvrez un fichier .ipynb existant à partir de la **fichier** explorer de menu ou le fichier *(fichiers .ipynb doivent être mis à niveau vers la version 4 ou ultérieure pour pouvoir se charger correctement)*
* Choisissez un noyau. Pour l’exécution de bloc-notes local, choisissez Python 3. Pour l’exécution à distance, choisissez PySpark ou Spark | Scala.
* Choisissez un point de terminaison du cluster de données volumineuses de SQL Server pour se connecter à si l’exécution à distance (cela n’est pas nécessaire pour le développement local avec Python 3).
* Ajouter des cellules de code ou markdown via les boutons dans l’en-tête du bloc-notes. Supprimer les cellules avec l’icône Corbeille à gauche de chaque cellule.
* Exécution des cellules avec le bouton de lecture pour les cellules de code et d’activer/désactiver l’édition avec markdown et d’aperçu avec l’icône représentant un œil

## <a name="polybase-create-external-table-wizard"></a>Table externe Assistant de création de PolyBase

* À partir d’une instance de SQL Server 2019 le *Assistant Création de Table externe* peuvent être ouverts dans trois façons :
  * Cliquez avec le bouton droit sur un serveur, choisissez **gérer**, cliquez sur l’onglet pour SQL Server 2019 (version préliminaire) et choisissez **Create External Table**.
  * Avec une instance de SQL Server 2019 sélectionnée dans *Explorateur d’objets*, faire apparaître *Assistant Création d’un externe* via la *Palette de commandes*.
  * Cliquez avec le bouton droit sur une base de données SQL Server 2019 *Explorateur d’objets* et choisissez **Create External Table**.
* Dans cette version de l’extension, les tables externes peuvent être créés pour accéder à des tables distantes de SQL Server et Oracle.

  > [!NOTE]
  > Alors que la fonctionnalité de Table externe est une fonctionnalité SQL 2019, une version antérieure de SQL Server peut être en cours d’exécution sur le serveur SQL distant.

* Choisissez si vous accédez à SQL Server ou Oracle sur la première page de l’Assistant et continuez.
* Vous devrez créer une clé principale de base de données si aucune n’a pas déjà été créée (les mots de passe de complexité insuffisante seront bloqués).
* Créer une connexion de source de données et nommé d’informations d’identification pour le serveur distant.
* Choisissez les objets à mapper à votre nouvelle table externe.
* Choisissez **générer un Script** ou **créer** pour terminer l’Assistant.
* Après la création de la table externe, il s’affiche immédiatement dans l’arborescence d’objets de la base de données où il a été créé.


## <a name="known-issues"></a>Problèmes connus

* Si le mot de passe n’est pas enregistré lors de la création d’une connexion, certaines actions telles que l’envoi du travail Spark ne peuvent pas réussir.
* Blocs-notes .ipynb existants doivent être mis à niveau vers la version 4 ou une version ultérieure pour charger le contenu dans la visionneuse.
* En cours d’exécution le **réinstaller les dépendances de bloc-notes** commande peut afficher les 2 tâches dans la vue tâches, un d'entre eux échoue. Cela ne provoque pas l’installation échoue
* En choisissant **ajouter une nouvelle connexion** dans un bloc-notes et en cliquant sur Annuler entraîne **sélectionner une connexion** à afficher, même si vous étiez déjà connecté.
