---
title: Extension de données Studio SQL Server 2019 Azure (version préliminaire) | Microsoft Docs
description: Extension de la version préliminaire de SQL Server 2019 pour Azure Data Studio
ms.custom: tools|sos
ms.date: 10/11/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d73f4a0d55cbe3fe3bacc0b2bb68f191046fe01b
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49168789"
---
# <a name="sql-server-2019-extension-preview"></a>Extension de SQL Server 2019 (version préliminaire)

L’extension de SQL Server 2019 (version préliminaire) fournit la prise en charge de la version préliminaire pour les nouvelles fonctionnalités et outils de livraison à l’appui de [!INCLUDE [sql-server-2019](..\includes\sssqlv15-md.md)]. Cela inclut la prise en charge de la version préliminaire de [clusters de données volumineuses de SQL Server 2019](../big-data-cluster/big-data-cluster-overview.md), intégré [expérience de bloc-notes](../big-data-cluster/notebooks-guidance.md), un PolyBase [Assistant de Create External Table](../relational-databases/polybase/data-virtualization.md?toc=%2fsql%2fbig-data-cluster%2ftoc.json)et [Azure Resource Explorer](azure-resource-explorer.md).

## <a name="install-the-sql-server-2019-extension-preview"></a>Installer l’extension de SQL Server 2019 (version préliminaire)

Pour installer l’extension de SQL Server 2019 (version préliminaire), télécharger et installer le fichier .vsix associé.

1. Télécharger le fichier .vsix d’extension (version préliminaire) SQL Server 2019 dans un répertoire local :

   |Plateforme|Télécharger|Date de publication|
   |:---|:---|:---|
   |Windows|[.VSIX](https://go.microsoft.com/fwlink/?linkid=2024911)|24 septembre 2018|
   |macOS|[.VSIX](https://go.microsoft.com/fwlink/?linkid=2024587)|24 septembre 2018 |
   |Linux|[.VSIX](https://go.microsoft.com/fwlink/?linkid=2024841)|24 septembre 2018 |

1. Dans Azure Data Studio choisissez **installer l’Extension à partir du Package VSIX** à partir de la **fichier** menu et sélectionnez le fichier .vsix téléchargé.

1. Choisissez **Oui** lorsque vous êtes invité à confirmer l’installation et attendre la notification de l’installation a réussi.

1. Sélectionnez **recharger** pour activer l’extension (uniquement obligatoire la première fois que vous installez une extension).

1. Après le rechargement, l’extension installera les dépendances. Vous pouvez voir la progression dans la fenêtre Sortie, et il peut prendre plusieurs minutes.

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


## <a name="azure-resource-explorer"></a>Explorateur de ressources Azure

* Pour vous connecter à Azure, cliquez sur l’icône de personne dans la partie inférieure gauche de Studio de données Azure et suivez les boîtes de dialogue se connecter à Azure.
* Une fois connecté, cliquez sur l’icône Azure triangulaire dans le gauche barre d’Azure Data Studio et développez l’arborescence pour afficher les ressources SQL associées à vos abonnements.
* Avec le bouton droit ou cliquez sur l’icône de connexion sur la base de données SQL ou SQL Server pour ouvrir la boîte de dialogue de connexion. Entrez votre mot de passe pour vous connecter et d’ajouter la ressource à l’Explorateur d’objets Azure Data Studio.

Pour plus d’informations, consultez [Azure Resource Explorer](azure-resource-explorer.md).


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
