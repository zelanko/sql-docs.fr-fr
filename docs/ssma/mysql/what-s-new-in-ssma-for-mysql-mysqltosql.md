---
title: Nouveautés dans la SSMA pour MySQL (MySQLToSql) Microsoft Docs
authors: HJToland3;nahk-ivanov
ms.prod: sql
ms.custom: ''
ms.date: 4/2/2020
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1451a0b0-6713-4d0c-954f-ea3d8fce1d31
ms.author: jtoland;alexiva
ms.openlocfilehash: 9d5c33bbb9e09a5a833c928547a5ec659fe43c96
ms.sourcegitcommit: d818a307725983c921987749915fe1a381233d98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80625550"
---
# <a name="whats-new-in-ssma-for-mysql-mysqltosql"></a>Nouveautés de SSMA pour MySQL (MySQLToSql)

Cet article répertorie SQL Server Migration Assistant (SSMA) pour les modifications mySQL dans chaque version.

## <a name="ssma-v88"></a>SSMA v8.8

La version v8.8 de SSMA pour MySQL comprend :

* SQL Server objets améliorations de stabilité de synchronisation
* Amélioration du rendement de l’interface graphique lors de l’évaluation et de la conversion

## <a name="ssma-v87"></a>SSMA v8.7

La version v8.7 de SSMA pour MySQL a des correctifs mineurs et des améliorations de performances dans l’interface utilisateur graphique.

De plus, SSMA pour MySQL `LIMIT` fournit maintenant la conversion de clause lors du ciblage d’Azure SQL.

> [!IMPORTANT]
> Avec SSMA v8.5 et plus tard, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v86"></a>SSMA v8.6

En plus d’un ensemble ciblé de correctifs conçus pour améliorer la convivialité et les performances, la version v8.6 de SSMA pour MySQL a été améliorée en ajoutant un paramètre qui permet aux utilisateurs d’omettre les propriétés étendues SSMA dans le code converti.

Pour tirer parti de ce paramètre, dans SSMA pour MySQL, naviguez vers **Tools** > **Project Settings** > **General** > **Conversion**, puis sous **Misc**, mettre à jour la valeur du **paramètre Omit Extended Properties** à **Yes**.

![Omettre le cadre des propriétés étendues](../mysql/media/ssma-omit-extended-properties.png)

> [!IMPORTANT]
> Avec SSMA v8.5 et plus tard, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v85"></a>SSMA v8.5

La version v8.5 de SSMA pour MySQL est renforcée par le support de l’authentification Azure Active Directory et le support de base pour les fonctionnalités JSON dans le serveur SQL, ainsi qu’un ensemble ciblé de correctifs conçus pour améliorer la convivialité et les performances.

> [!IMPORTANT]
> Avec SSMA v8.5, .NET 4.7.2 est une installation pré-requise. Si vous avez besoin d’installer cette version, vous pouvez télécharger le fichier runtime à partir [d’ici](https://dotnet.microsoft.com/download/dotnet-framework/net472).

## <a name="ssma-v84"></a>SSMA v8.4

La version v8.4 de SSMA pour MySQL est enrichie de correctifs ciblés qui sont conçus pour résoudre les problèmes d’accessibilité et corriger un bogue lié aux colonnes d’index max (pour permettre 32 au lieu de 16) pour SQL Server 2016 et les versions ultérieures.

> [!IMPORTANT]
> Avec les versions SSMA 7.4 bien que 8.4, .NET 4.5.2 est une installation pré-requis.

## <a name="ssma-v83"></a>SSMA v8.3

La version v8.3 de SSMA pour MySQL est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion. De plus, cette version de SSMA pour MySQL fournit des correctifs qui :

* Aborder les questions d’accessibilité.
* Ajoutez une `hierarchyid` prise en charge de base pour le type dans SQL Server.

## <a name="ssma-v82"></a>SSMA v8.2

La version v8.2 de SSMA pour MySQL est enrichie d’un ensemble ciblé de correctifs conçus pour améliorer les mesures de qualité et de conversion, ainsi que des correctifs pour :

* Un problème avec les indices non groupés désactivés après la migration des données.
* Détection du cadre .NET lors de l’installation silencieuse.
* Un plantage intermittent qui se produit lorsqu’une nouvelle version est téléchargée.

> [!NOTE]
> Un problème connu avec l’auto-mise à jour peut causer l’échec d’une mise à jour de SSMA v8.1 à v8.2. Si vous rencontrez cette erreur, veuillez télécharger la nouvelle version et l’installer manuellement.

## <a name="ssma-v81"></a>SSMA v8.1

La version v8.1 de SSMA pour MySQL est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion.

> [!NOTE]
> Un problème connu avec l’auto-mise à jour peut causer l’échec d’une mise à jour de SSMA v8.0 à v8.1. Si vous rencontrez cette erreur, veuillez télécharger la nouvelle version et l’installer manuellement.

## <a name="ssma-v80"></a>SSMA v8.0

La version v8.0 de SSMA pour MySQL est enrichie de correctifs ciblés conçus pour améliorer la qualité et les mesures de conversion. Cette version offre également les nouvelles fonctionnalités suivantes :

* Prise en charge de **l’instance gérée par la base de données Azure SQL** comme cible. Vous pouvez désormais créer de nouveaux projets ciblant Azure SQL Database Managed Instance :

  ![Projet SQL DB MI](../media/ssma-newproject-sqldbmi.png)

* Conseiller **Fix**post-conversion . En savoir plus à ce sujet [ici](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Sélection préliminaire de base de données/schémas.

  Lors de la connexion à la source, l’utilisateur peut désormais sélectionner des bases de données/schémas d’intérêt. Sélectionner uniquement les schémas que vous prévoyez de migrer permettra de gagner du temps pendant la connexion initiale et d’améliorer les performances globales de la SSMA.

  ![Objets filtreS SSMA](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10

La version v7.10 de SSMA pour MySQL contient les modifications suivantes :

* Des correctifs ciblés conçus pour fournir des protections supplémentaires en matière de sécurité et de protection de la vie privée afin de répondre aux changements apportés aux exigences mondiales.
* Un correctif pour la conversion des espaces entre le nom de fonction et la liste d’arguments.

## <a name="ssma-v79"></a>SSMA v7.9

La version v7.9 de SSMA pour MySQL contient les modifications suivantes :

* Des correctifs ciblés qui améliorent la qualité et les mesures de conversion.
* Prise en charge partielle des types de données spatiales migrents de MySQL à Azure SQL Database.
* Soutien à la ligne de commande SSMA pour modifier la cartographie de type de données et les préférences de projet.
* Prise en charge des données de migration à l’aide des Services d’intégration des serveurs SQL (SSIS). Après avoir converti le schéma, il est possible de créer un package SSIS en utilisant une option de menu contextuelle à clic droit.
* Le dialogue de connexion de base de données Azure SQL dans SSMA a également été modifié pour spécifier le nom du serveur entièrement qualifié. Dans les versions précédentes de la SSMA, le préfixe azure SQL Database devait être explicitement mentionné à l’intérieur des paramètres des projets.

## <a name="ssma-v78"></a>SSMA v7.8

La version v7.8 de SSMA pour MySQL contient les modifications suivantes :

* Modifier la cartographie de type mise en évidence dans les paramètres du projet.
* La possibilité pour les utilisateurs de désactiver la télémétrie.

## <a name="ssma-v77"></a>SSMA v7.7

La version v7.7 de SSMA pour MySQL contient les modifications suivantes :

* SSMA pour MySQL a été amélioré avec des correctifs ciblés qui améliorent la qualité et les mesures de conversion.
* Sur la base de la demande populaire, la version 32 bits de la SSMA pour MySQL est de retour. Par rapport à la mise en œuvre précédente (avant v7.4), il ya deux paquets d’installateur, mais ils ne peuvent pas être installés côte à côte. Par conséquent, vous devez choisir la version la plus appropriée en fonction des composants de connectivité que vous avez. Il est toujours préférable d’utiliser la version 64 bits, si possible.
* SSMA pour MySQL dispose désormais d’un mode de connexion ODBC Connection String, qui vous permet d’utiliser tous les pilotes ODBC tiers compatibles avec MySQL.

## <a name="ssma-v76"></a>SSMA v7.6

La version v7.6 de SSMA pour MySQL a été améliorée avec des correctifs ciblés qui améliorent la qualité et les mesures de conversion et avec la prise en charge de SQL Server 2017 (aperçu public). Le support pour SQL Server 2017 sur Windows et Linux est en avant-première publique et ne devrait pas être utilisé pour les migrations de production.

## <a name="ssma-v75"></a>SSMA v7.5

La version v7.5 de la SSMA pour MySQL a été améliorée avec plusieurs améliorations afin d’assurer une plus grande accessibilité pour les personnes handicapées.

## <a name="ssma-v74"></a>SSMA v7.4

La version v7.4 de SSMA pour MySQL contient les modifications suivantes :

* **L’option de temps d’arrêt De requête** est maintenant disponible lors de la découverte d’objets schématiques à la source et à la cible.

    ![option de délai d’attente de requête](../media/query-timeout_red.png)
* La mesure de qualité et de conversion a été améliorée grâce à des correctifs ciblés, basés sur la rétroaction des clients.

> [!IMPORTANT]
> .NET 4.5.2 est un pré-requis pour l’installation de SSMA v7.4. En outre, à partir de v7.4, la version 32 bits de SSMA est en cours d’arrêt.

## <a name="ssma-v73"></a>SSMA v7.3

La version v7.3 de SSMA pour MySQL contient les modifications suivantes :

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

La version v7.2 de SSMA pour MySQL contient les modifications suivantes :

* Amélioration de la qualité et de la mesure de conversion grâce à des correctifs ciblés basés sur la rétroaction des clients.
* Améliorations de la télémétrie pour fournir de meilleurs points de données pour résoudre les problèmes des clients et améliorer les taux de conversion de SSMA.

## <a name="ssma-v71"></a>SSMA v7.1

La version v7.1 de SSMA pour MySQL contient les modifications suivantes :

* SQL Server 2017 sur Windows et Linux CTP1 est maintenant une plate-forme cible prise en charge pour la migration. Cette fonctionnalité est en aperçu technique et permet au schéma et au mouvement des données de cibler les serveurs SQL.
* SSMA prend désormais en charge les mises à jour automatiques pour télécharger la dernière version de SSMA dès qu’elle est disponible.
* Les binaires installables SSMA sont maintenant livrés via les fichiers de paquets Windows Installer (.msi).

## <a name="may-2016"></a>Mai 2016

La sortie en mai 2016 de SSMA pour MySQL contient les changements suivants :

* Ajout d’un support pour SQL Server 2016.
* Analyse et résolveur améliorés.
* Vérification de l’installateur supprimé pour .NET 2.0.
* Mise à jour Extension Pack dépendance de .NET 3.5 à .NET 4.0.
* Cartographie de type BigInt par défaut fixe pour MySql.
* Fixe `save-project` `open-project` et commandes pour console SSMA.
* Commande `securepassword` fixe pour console SSMA.
* Comptage fixe des objets pour le chargement initial.
* Chargement fixe d’objets MsSql.
* Bug fixe dans les paramètres globaux.

## <a name="march-2016"></a>Mars 2016

La sortie en avant-première de mars 2016 de SSMA pour MySQL ajoute un soutien à la migration vers SQL Server 2016.
  
## <a name="january-2016"></a>Janvier 2016

La version de maintenance de janvier 2016 de la SSMA pour MySQL contient les changements suivants :

* Ajout de l’élément de menu de journal de vue à SSMA (RFC 5706203).
* Ajout de la télémétrie.
  
## <a name="july-2014"></a>Juillet 2014

La sortie en juillet 2014 de SSMA pour MySQL contient les changements suivants :
  
* Amélioration de la conversion du code Azure SQL DB.
* La fonctionnalité du pack d’extension s’est déplacée au schéma pour prendre en charge Azure SQL DB.
* Améliorations de performance testées pour les bases de données avec plus de 10k objets.
* Améliorations de l’interface utilisateur pour traiter un grand nombre d’objets.
* Mise en évidence des schémas LOB bien connus (afin qu’ils puissent être ignorés dans la conversion).
* Amélioration de la vitesse de conversion.
* Afficher le nombre d’objets dans l’interface utilisateur.
* Réduction de la taille du rapport de plus de 25 %.
* Messages d’erreur améliorés pour les constructions non apprables.
  
## <a name="april-2014"></a>Avril 2014

La sortie en avril 2014 de SSMA pour MySQL contient les changements suivants :
  
* Ajout d’un support pour SQL Server 2014.
* Bugs fixes concernant la conversion à Azure.
* Bugs fixes concernant les pages de rapport invisibles dans IE 10.
  
## <a name="july-2011"></a>juillet 2011

La sortie en juillet 2011 de SSMA pour MySQL contient les changements suivants :
  
* Soutien à `LIMIT` la [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)] `OFFSET`conversion en .
* Amélioration de la déclaration d’erreurs pendant la migration des données.
  
## <a name="april-2011"></a>Avril 2011

La sortie en avril 2011 de SSMA pour MySQL contient les changements suivants :
  
* Installation unique de "SSMA pour MySQL", qui prend en charge [!INCLUDE [ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE [ssSQL10](../../includes/sssql10-md.md)], [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)] et Azure SQL.
* La capacité [!INCLUDE [ssSQL11](../../includes/sssql11-md.md)]de se connecter .
* Amélioration du moteur de migration des données côté client, à l’appui de la migration parallèle des données.
* Amélioration des performances de migration des données grâce à des modèles de récupération connectés Simple et Bulk.
* SSMA pour la version Console MySQL prend en charge la compatibilité vers l’arrière. Vous pouvez ouvrir les projets créés par des versions antérieures à SSMA v5.0.
* SSMA pour mySQL v5.0 produit peut être installé côte à côte (SxS) avec des versions plus anciennes de SSMA Product.
  
## <a name="july-2010"></a>Juillet 2010

La sortie en juillet 2010 de SSMA pour MySQL contient les caractéristiques suivantes :
  
**1. Améliorations à l’interface utilisateur :**

* Onglet 'SQL Modes' pour les objets de base de données MySQL
* Onglet 'Paramètres' pour les objets de base de données MySQL
* Onglet 'Data' pour les tables MySQL
* Mise à jour des paramètres de projet dans les pages de conversion et de migration
* « Paramètres de migration des données » au niveau de la table
  
**2. Améliorations pour se connecter à MySQL et SQL Server:**
  
* Connectivité SSL dans MySQL
* Connectivité cryptée dans SQL Server
  
**3. Améliorations à MySQL Metabase Explorer:**
  
* Chargement de tous les objets de base de données MySQL et leurs onglets respectifs.
  
**4. Améliorations à la conversion d’objets :**
  
* Conversion d’objets MySQL Metabase - Procédures, fonctions, vues, déclencheurs et déclarations.
* Soutien limité pour les types de données spatiales dans les tableaux.
* Option pour convertir les fonctions MySQL en procédures stockées sqL Server
* Option d’appliquer SQL Modes et Charset mapping pendant la conversion d’objets
  
**5. Améliorations apportées à la migration des données :**  
  
* Prise en charge de la migration des données à l’aide de moteurs de migration de données côté serveur et côté client
* Soutien à la migration des données spatiales
* SQL personnalisé pour la migration de données pour les tables
  
**6. SSMA pour console MySQL:**  
  
* Caractéristiques de console de support pour SSMA pour MySQL  
* Prise en charge de Script-Level Interfacing  
  
## <a name="january-2010"></a>Janvier 2010

La sortie en janvier 2010 de SSMA pour MySQL a été la version initiale. Il contenait les caractéristiques suivantes :
  
* Ajout d’un soutien pour la migration vers les deux sur place SQL Server et Azure SQL.  
  
* **Instantané de la fonctionnalité :** Migration de schémas et de données des tables/indices/contraintes MySQL.
