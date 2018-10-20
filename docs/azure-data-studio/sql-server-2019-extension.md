---
title: Extension de données Studio SQL Server 2019 Azure (version préliminaire) | Microsoft Docs
description: Extension de la version préliminaire de SQL Server 2019 pour Azure Data Studio
ms.custom: tools|sos
ms.date: 10/11/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6624f2efb14f5d056ee0ac052fa9396535ebb239
ms.sourcegitcommit: ef115025e57ec342c14ed3151ce006f484d1fadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49411166"
---
# <a name="sql-server-2019-extension-preview"></a>Extension de SQL Server 2019 (version préliminaire)

L’extension de SQL Server 2019 (version préliminaire) fournit la prise en charge de la version préliminaire pour les nouvelles fonctionnalités et outils de livraison à l’appui de [!INCLUDE [sql-server-2019](..\includes\sssqlv15-md.md)]. Cela inclut la prise en charge de la version préliminaire de [clusters de données volumineuses de SQL Server 2019](../big-data-cluster/big-data-cluster-overview.md), intégré [expérience de bloc-notes](../big-data-cluster/notebooks-guidance.md), un PolyBase [Assistant de Create External Table](../relational-databases/polybase/data-virtualization.md?toc=%2fsql%2fbig-data-cluster%2ftoc.json)et [Azure Resource Explorer](azure-resource-explorer.md).

## <a name="install-the-sql-server-2019-extension-preview"></a>Installer l’extension de SQL Server 2019 (version préliminaire)

Pour installer l’extension de SQL Server 2019 (version préliminaire), télécharger et installer le fichier .vsix associé.

1. Télécharger le fichier .vsix d’extension (version préliminaire) SQL Server 2019 dans un répertoire local :

   |Plateforme|Télécharger|Date de publication|Version
   |:---|:---|:---|:---|
   |Windows|[.VSIX](https://go.microsoft.com/fwlink/?LinkId=2031539)|18 octobre 2018|0.7.2
   |macOS|[.VSIX](https://go.microsoft.com/fwlink/?LinkId=2031717)|18 octobre 2018 |0.7.2
   |Linux|[.VSIX](https://go.microsoft.com/fwlink/?LinkId=2031538)|18 octobre 2018 |0.7.2

1. Dans Azure Data Studio choisissez **installer l’Extension à partir du Package VSIX** à partir de la **fichier** menu et sélectionnez le fichier .vsix téléchargé.

1. Choisissez **Oui** lorsque vous êtes invité à confirmer l’installation et attendre la notification de l’installation a réussi.

1. Sélectionnez **recharger** pour activer l’extension (uniquement obligatoire la première fois que vous installez une extension).

1. Après le rechargement, l’extension installera les dépendances. Vous pouvez voir la progression dans la fenêtre Sortie, et il peut prendre plusieurs minutes.

## <a name="release-notes-v072"></a>Notes de publication (v0.7.2)
* Explorateur de ressources Azure est désormais intégré à Azure Data Studio et a été supprimé de cette extension. Nous vous remercions pour vos commentaires sur ce !
* Amélioration des performances des ordinateurs portables avec beaucoup de cellules Markdown.
* Cellules de code de redimensionnement automatique dans le bloc-notes. Cela a toujours une taille minimale basée sur la barre d’outils de la cellule.
* Informez l’utilisateur lors de l’installation des dépendances de bloc-notes. Sur Windows cela peut en particulier prendre beaucoup de temps, afin de notifications sont maintenant affichées dans la vue tâches.
* Prise en charge la réinstallation des dépendances de bloc-notes. Cela est utile si l’utilisateur précédemment fermés Azure Data Studio en cours via l’installation.
* Prise en charge l’annulation de l’exécution de cellule dans le bloc-notes.
* Fiabilité améliorée lorsque vous utilisez l’Assistant de création de données externe, en particulier lorsque les erreurs de connexion se produisent.
* Bloquer l’utilisation de l’Assistant de création de données externe si Polybase n’est pas activé ni en cours d’exécution sur le serveur cible.
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

## <a name="polybase-create-external-table-wizard"></a>Table externe Assistant de création de Polybase

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
