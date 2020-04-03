---
title: Nouveautés en SSMA pour DB2 (DB2ToSQL) Microsoft Docs
authors: HJToland3;nahk-ivanov
ms.prod: sql
ms.custom: ''
ms.date: 4/2/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1cc38f85-3caa-42d0-8c76-a380c1d15c67
ms.author: jtoland;alexiva
ms.openlocfilehash: 53a159627750a5ec66b5aa0b3fd6510c647e26a5
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625522"
---
# <a name="whats-new-in-ssma-for-db2-db2tosql"></a>Nouveautés en SSMA pour DB2 (DB2ToSQL)

Cet article répertorie SQL Server Migration Assistant (SSMA) pour les modifications DB2 dans chaque version.

## <a name="ssma-v88"></a>SSMA v8.8

La version v8.8 de SSMA pour DB2 comprend :

* SQL Server objets améliorations de stabilité de synchronisation
* Amélioration du rendement de l’interface graphique lors de l’évaluation et de la conversion
* Mise à `ROWID` `varbinary(40)` jour de la cartographie de la part pour faciliter la migration des données
* Amélioration de `SELECT ... FROM NEW/OLD TABLE` la conversion des déclarations
* Nouvelle conversion `ALTER` des énoncés pour les procédures et les fonctions
* Nouvelle conversion des missions de déstructuration

## <a name="ssma-v87"></a>SSMA v8.7

La version v8.7 de SSMA pour DB2 comprend tout nouveau parser syntaxe DB2, ainsi que des correctifs mineurs et des améliorations des performances dans l’interface utilisateur graphique.

En outre, SSMA pour DB2 fournit maintenant:

* Un correctif pour la découverte des clés étrangères lors de la migration de DB2 sur LUW.
* Amélioration de `SELECT ... FOR UPDATE` la conversion de l’énoncé.
* Amélioration de `COUNT` la conversion pour la fonction dans les tables MQ.
* Conversion `SAVEPOINT` des déclarations.
* Conversion pour imiter le comportement `NULL` de `ORDER BY` DB2 pour les valeurs en clause.
* Soutien parsing pour LA déclaration ASSOCIATE RESULT SET.

> [!IMPORTANT]
> Avec SSMA v8.5 et plus tard, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v86"></a>SSMA v8.6

En plus d’un ensemble ciblé de correctifs conçus pour améliorer la convivialité et les performances, la version v8.6 de SSMA pour DB2 a été améliorée par l’ajout d’un paramètre qui permet aux utilisateurs d’omettre les propriétés étendues SSMA dans le code converti.

Pour tirer parti de ce paramètre, en SSMA pour DB2, naviguez vers **Tools** > **Project Settings** > **General** > **Conversion**, puis sous **Misc**, mettre à jour la valeur du **paramètre Omit Extended Properties** à **Yes**.

![Omettre le cadre des propriétés étendues](../db2/media/ssma-omit-extended-properties.png)

En outre, SSMA pour DB2 fournit maintenant:

* Un correctif pour la conversion des fonctions qui utilisent des valeurs d’argument par défaut.
* Amélioration de l’analyse de la `PARAMETER` clause pour les fonctions.
* La possibilité de `LEAVE` convertir la déclaration.

> [!IMPORTANT]
> Avec SSMA v8.5 et plus tard, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v85"></a>SSMA v8.5

La version v8.5 de SSMA pour DB2 est renforcée par le support de l’authentification Azure Active Directory et le support de base pour les fonctionnalités JSON dans le serveur SQL, ainsi qu’un ensemble ciblé de correctifs conçus pour améliorer la convivialité et les performances.

En outre, SSMA pour DB2 a été améliorée avec:

* Prise en charge `GET DIAGNOSTICS` pour `ROW_NUMBER`l’ajout de conversion pour l’instruction avec .
* Un correctif pour un bogue lié aux espaces au début du nom de l’objet n’étant pas respecté.

> [!IMPORTANT]
> Avec SSMA v8.5, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v84"></a>SSMA v8.4

La version v8.4 de SSMA pour DB2 est enrichie de correctifs ciblés qui sont conçus pour résoudre les problèmes d’accessibilité et corriger un bogue lié aux colonnes d’index max (pour permettre 32 au lieu de 16) pour SQL Server 2016 et les versions ultérieures.

> [!IMPORTANT]
> Avec les versions SSMA 7.4 bien que 8.4, .NET 4.5.2 est une installation pré-requis.

## <a name="ssma-v83"></a>SSMA v8.3

La version v8.3 de SSMA pour DB2 est améliorée avec des correctifs ciblés qui sont conçus pour améliorer la qualité et les mesures de conversion. En outre, cette version de SSMA pour DB2 fournit des correctifs qui:

* Aborder les questions d’accessibilité.
* Ajoutez une `hierarchyid` prise en charge de base pour le type dans SQL Server.
* Remplacez l’utilisation de la fonction `RTRIM` / `LTRIM`TRIM dans les requêtes de découverte z/OS par .
* Permettre à l’utilisateur de spécifier la collection `NULLID`de paquets lors de la connexion en mode Standard (par défaut à ).
* Ajouter la `CREATE TABLE AS SELECT`conversion pour .
* Améliorer les conversions pour les tables d’intérim globales.
* Résoudre un problème avec l’ordre de vérification de l’unicité des objets pour prioriser les tableaux plutôt que les contraintes, si les noms entrent en collision.
* Résoudre un problème avec le `DATE` chargement des valeurs de colonne par défaut pour et `TIMESTAMP` pour z/ OS.
* Prendre en charge le caractère `NEL`d’alimentation en ligne Unicode (également connu sous le nom de ).
* Résoudre un problème avec la `RETURN TO` conversion des curseurs avec clause manquante.
* Ajouter un support `GOTO`pour les étiquettes et .

## <a name="ssma-v82"></a>SSMA v8.2

La version v8.2 de SSMA pour DB2 est améliorée avec pour répondre aux problèmes avec les connexions à Azure SQL Base de données de l’outil de console SSMA et manquant COUNT_BIG colonne dans la déclaration de vues lors de la conversion. En outre, cette version comprend un ensemble ciblé de correctifs conçus pour améliorer la qualité et les mesures de conversion, ainsi que des correctifs pour:

* Un problème avec les indices non groupés désactivés après la migration des données.
* Détection du cadre .NET lors de l’installation silencieuse.
* Un plantage intermittent qui se produit lorsqu’une nouvelle version est téléchargée.

> [!NOTE]
> Un problème connu avec l’auto-mise à jour peut causer l’échec d’une mise à jour de SSMA v8.1 à v8.2. Si vous rencontrez cette erreur, veuillez télécharger la nouvelle version et l’installer manuellement.

## <a name="ssma-v81"></a>SSMA v8.1

La version v8.1 de SSMA pour DB2 est améliorée pour fournir des correctifs ciblés qui sont conçus pour améliorer la qualité et les mesures de conversion.

> [!NOTE]
> Un problème connu avec l’auto-mise à jour peut causer l’échec d’une mise à jour de SSMA v8.0 à v8.1. Si vous rencontrez cette erreur, veuillez télécharger la nouvelle version et l’installer manuellement.

## <a name="ssma-v80"></a>SSMA v8.0

La version v8.0 de SSMA pour DB2 est améliorée pour fournir des correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion. Cette version offre également les nouvelles fonctionnalités suivantes :

* Prise en charge de **l’instance gérée par la base de données Azure SQL** comme cible. Vous pouvez désormais créer de nouveaux projets ciblant Azure SQL Database Managed Instance :

  ![Projet SQL DB MI](../media/ssma-newproject-sqldbmi.png)

* Conseiller **Fix**post-conversion . En savoir plus à ce sujet [ici](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Sélection préliminaire de base de données/schémas.

  Lors de la connexion à la source, l’utilisateur peut désormais sélectionner des bases de données/schémas d’intérêt. Sélectionner uniquement les schémas que vous prévoyez de migrer permettra de gagner du temps pendant la connexion initiale et d’améliorer les performances globales de la SSMA.

  ![Objets filtreS SSMA](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10

La version v7.10 de SSMA pour DB2 contient les modifications suivantes :

* Des correctifs ciblés conçus pour fournir des protections supplémentaires en matière de sécurité et de protection de la vie privée afin de répondre aux changements apportés aux exigences mondiales.
* Un correctif pour `BEGIN-END` la conversion des blocs.

## <a name="ssma-v79"></a>SSMA v7.9

La version v7.9 de SSMA pour DB2 contient les modifications suivantes :

* Des correctifs ciblés qui améliorent la qualité et les mesures de conversion.
* Soutien à la ligne de commande SSMA pour modifier la cartographie de type de données et les préférences de projet.
* Prise en charge des données de migration à l’aide des Services d’intégration des serveurs SQL (SSIS). Après avoir converti le schéma, il est possible de créer un package SSIS en utilisant une option de menu contextuelle à clic droit.
* Le dialogue de connexion de base de données Azure SQL dans SSMA a également été modifié pour spécifier le nom du serveur entièrement qualifié. Dans les versions précédentes de la SSMA, le préfixe azure SQL Database devait être explicitement mentionné à l’intérieur des paramètres des projets.

## <a name="ssma-v78"></a>SSMA v7.8

La version v7.8 de SSMA pour DB2 contient les modifications suivantes :

* Modifier la cartographie de type mise en évidence dans *les paramètres du projet*.
* La possibilité pour les utilisateurs de désactiver la télémétrie.

## <a name="ssma-v77"></a>SSMA v7.7

La version v7.7 de SSMA pour DB2 contient les modifications suivantes :

* Des correctifs ciblés qui améliorent la qualité et les mesures de conversion.
* Sur la base de la demande populaire, la version 32 bits de SSMA pour DB2 est de retour. Par rapport à la mise en œuvre précédente (avant v7.4), il ya deux paquets d’installateur, mais ils ne peuvent pas être installés côte à côte. Par conséquent, vous devez choisir la version la plus appropriée en fonction des composants de connectivité que vous avez. Il est toujours préférable d’utiliser la version 64 bits, si possible.

## <a name="ssma-v76"></a>SSMA v7.6

La version v7.6 de SSMA pour DB2 est enrichie de correctifs ciblés qui améliorent la qualité et les mesures de conversion et avec prise en charge de SQL Server 2017 (aperçu public). Le support pour SQL Server 2017 sur Windows et Linux est en avant-première publique et ne devrait pas être utilisé pour les migrations de production.

## <a name="ssma-v75"></a>SSMA v7.5

La version v7.5 de la SSMA pour DB2 est améliorée avec plusieurs améliorations afin d’assurer une plus grande accessibilité pour les personnes handicapées.

## <a name="ssma-v74"></a>SSMA v7.4

La version v7.4 de SSMA pour DB2 contient les modifications suivantes :

* **L’option de temps d’arrêt De requête** est maintenant disponible lors de la découverte d’objets schématiques à la source et à la cible.

  ![option de délai d’attente de requête](../media/query-timeout_red.png)

* La mesure de qualité et de conversion a été améliorée grâce à des correctifs ciblés, basés sur la rétroaction des clients.

  > [!IMPORTANT]
  > .NET 4.5.2 est un pré-requis pour l’installation de SSMA v7.4. En outre, à partir de v7.4, la version 32 bits de SSMA a été abandonnée.

## <a name="ssma-v73"></a>SSMA v7.3

La version v7.3 de SSMA pour DB2 contient les modifications suivantes :

* Amélioration de la qualité et de la mesure de conversion grâce à des correctifs ciblés basés sur la rétroaction des clients.
* Cadre d’extéabilité SSMA exposé via les éléments suivants :
  * Fonctionnalité d’exportation vers un projet SQL Server Data Tools (SSDT).
    * Vous pouvez maintenant exporter des scripts de schémas de SSMA vers un projet SSDT. Vous pouvez utiliser les scripts schéma pour apporter d’autres modifications de schéma et déployer votre base de données.

      ![Enregistrer comme commande de projet SSDT](../media/export-schema-scripts_red.png)
  * Bibliothèques qui peuvent être consommées par SSMA pour effectuer des conversions personnalisées.
    * Vous pouvez maintenant construire du code qui peut gérer les conversions et conversions syntaxes personnalisées qui n’ont pas été précédemment traitées par SSMA.
      * Des instructions sur la façon de construire un convertisseur personnalisé sont disponibles dans ce billet de blog, [Extension des capacités de conversion de SQL Server Migration Assistant](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      * Téléchargez un exemple de projet de conversion à partir de ce billet de [blog](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).

## <a name="ssma-v72"></a>SSMA v7.2

La version v7.2 de SSMA pour DB2 contient les modifications suivantes :

* Amélioration de la qualité et de la mesure de conversion grâce à des correctifs ciblés basés sur la rétroaction des clients.
* Améliorations de la télémétrie pour fournir de meilleurs points de données pour résoudre les problèmes des clients et améliorer les taux de conversion de SSMA.

## <a name="ssma-v71"></a>SSMA v7.1

La version v7.1 de SSMA pour DB2 contient les modifications suivantes :

* SQL Server 2017 sur Windows et Linux CTP1 est maintenant une plate-forme cible prise en charge pour la migration. Cette fonctionnalité est en aperçu technique et permet au schéma et au mouvement des données de cibler les serveurs SQL.
* Prendre en charge les mises à jour automatiques pour télécharger la dernière version de SSMA dès qu’elle est disponible.
* Les binaires installables SSMA sont maintenant livrés via les fichiers de paquets Windows Installer (.msi).

## <a name="may-2016"></a>Mai 2016

La sortie en mai 2016 de SSMA pour DB2 contient les changements suivants :

* Ajout d’un support pour SQL Server 2016.
* Ajout de la conversion de DB2 en mémoire et de tables régulières aux fonctionnalités SQL Server en mémoire et hekaton.
* Conversion supplémentaire des contrôles d’accès DB2 aux objets SQL Server Policy (Sécurité au niveau de la ligne pour DB2).
* Ajout de la conversion des tables DB2 en version système en tables temporelles SQL Server.
* Analyse et résolveur DB2 améliorés.
* Vérification de l’installateur supprimé pour .NET 2.0.
* Retiré inutile \*.dll de l’installateur Db2.
* Fixe `save-project` `open-project` et commandes pour console SSMA.
* Commande `securepassword` fixe pour console SSMA.
* Comptage fixe des objets pour le chargement initial.
* Bug fixe dans les paramètres globaux.
  
## <a name="march-2016"></a>Mars 2016

La sortie en avant-première de la SSMA pour DB2 en mars 2016 ajoute un soutien à la migration vers SQL Server 2016.

## <a name="january-2016"></a>Janvier 2016

La version de maintenance de janvier 2016 de SSMA pour DB2 contient les modifications suivantes :
  
* Ajout d’un support pour un certain nombre de fonctions standard.
* Erreurs fixes de parser DB2.
* Support fixe DB2 v9 zOS (RFC 5690920).
* Correction des erreurs d’identification non résolues DB2 lors de la conversion.
* Ajout de l’élément de menu de journal de vue à SSMA (RFC 5706203).
* Ajout de la télémétrie.
  
## <a name="november-2014"></a>novembre 2014

La sortie en novembre 2014 de SSMA pour DB2 a été la version initiale.
