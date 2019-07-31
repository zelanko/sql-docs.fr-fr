---
title: Nouveautés de SSMA pour Oracle (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 07/31/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f305ebb6-7393-4a43-abb3-6332b739d690
author: HJToland3
ms.author: Shamikg
ms.openlocfilehash: 27e1e0ee06f343c63240c1155601b2eab5e8c6cc
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631995"
---
# <a name="whats-new-in-ssma-for-oracle-oracletosql"></a>Nouveautés de SSMA pour Oracle (OracleToSQL)
Cet article répertorie les Assistant Migration SQL Server (SSMA) pour les modifications Oracle dans chaque version.

## <a name="ssma-v83"></a>SSMA v 8.3

La version 8.3 de SSMA pour Oracle a été améliorée avec des correctifs ciblés conçus pour améliorer les mesures de qualité et de conversion. En outre, cette version de SSMA pour Oracle fournit des correctifs qui:

* Résoudre les problèmes d’accessibilité
* Ajouter la prise en charge de base pour le type «hierarchyid» dans SQL Server
* Résoudre un problème avec un type de retour inconnu pour une fonction appelée par le synonyme
* Mettre à jour ODP.NET vers v 19.3

> [!IMPORTANT]
> Avec SSMA v 7.4 et versions ultérieures, .net 4.5.2 est une condition préalable à l’installation.

## <a name="ssma-v82"></a>SSMA v8.2

La version 8.2 de SSMA pour Oracle a été améliorée pour:

* Ajoutez la prise en charge de DBMS_OUTPUT. ACTIVATION/DÉSACTIVATION.
* Supprimer la conversion en tant que valeur FLOAT pour les colonnes BINARY_FLOAT et BINARY_DOUBLE dans la requête de migration de données par défaut.
* Corriger les séquences actualiser si la valeur actuelle a changé.
* Corrigez les bogues liés à une mauvaise interprétation des pseudo-colonnes (ROWNUM, etc.) si une colonne portant le même nom existe.
* Corriger un incident qui se produit lors de la conversion de boucles avec un identificateur non résolu ambigu.

En outre, cette version comprend un ensemble ciblé de correctifs conçus pour améliorer les mesures de qualité et de conversion, ainsi que des correctifs pour:

* Un problème avec les index non cluster désactivés après la migration des données.
* Détection des .NET Framework pendant l’installation sans assistance.
* Incident intermittent qui se produit lorsqu’une nouvelle version est téléchargée.

> [!NOTE]
> Un problème connu avec la mise à jour automatique peut entraîner l’échec d’une mise à jour de SSMA v 8.1 à v 8.2. Si vous rencontrez cette erreur, téléchargez la nouvelle version et installez-la manuellement.

> [!IMPORTANT]
> Avec SSMA v 7.4 et versions ultérieures, .net 4.5.2 est une condition préalable à l’installation.

## <a name="ssma-v81"></a>SSMA v 8.1

La version 8.1 de SSMA pour Oracle a été améliorée avec des correctifs ciblés conçus pour améliorer les mesures de qualité et de conversion.

> [!NOTE]
> Un problème connu avec la mise à jour automatique peut entraîner l’échec d’une mise à jour de SSMA v 8.0 à v 8.1. Si vous rencontrez cette erreur, téléchargez la nouvelle version et installez-la manuellement.

## <a name="ssma-v80"></a>SSMA v8.0

La version 8.0 de SSMA pour Oracle a été améliorée avec des correctifs ciblés conçus pour améliorer les mesures de qualité et de conversion. Cette version offre également les nouvelles fonctionnalités suivantes:

* Prise en charge de **Azure SQL Database Managed instance** en tant que cible. Vous pouvez maintenant créer des projets ciblant Azure SQL Database Managed Instance:

  ![Projet SQL DB MI](../media/ssma-newproject-sqldbmi.png)

  > [!NOTE]
  > Le pack d’extension SSMA pour Oracle a également été mis à jour pour permettre les installations à distance sur Azure SQL Database Managed Instance:
  >
  > ![SSMA pour le pack d’extension Oracle](../media/ssma-oracle-ext-pack.png)

  Certaines fonctionnalités, y compris le testeur et la migration des données côté serveur, ne sont pas prises en charge lors du ciblage Azure SQL Database Managed Instance. En savoir plus à ce sujet [ici](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/migrate-your-oracle-database-to-azure-sql-database-managed-instance-using-ssma-8-0/).

* **Conseiller de réparation**après conversion. En savoir plus à ce sujet [ici](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Sélection préliminaire de base de données/schéma.

  Lors de la connexion à la source, l’utilisateur peut désormais sélectionner les bases de données/schémas intéressants. La sélection de seuls les schémas que vous envisagez de migrer permet de gagner du temps lors de la connexion initiale et d’améliorer les performances globales de SSMA.

  ![Objets de filtre SSMA](../media/ssma-filter-objects.png)

* La possibilité d’utiliser le pilote NET géré par l’agent pour se connecter à Oracle. Le pilote OCI n’est plus un composant requis pour l’utilisation de Assistant Migration SQL Server pour Oracle.

* Possibilité de mapper par défaut ROWID et UROWID sur VARCHAR. Modifié de «uniqueidentifier» pour tenir compte de la migration des données pour les colonnes ROWID explicites.

## <a name="ssma-v710"></a>SSMA v 7.10

La version v 7.10 de SSMA pour Oracle contient les modifications suivantes:

* Des correctifs ciblés conçus pour fournir des protections de sécurité et de confidentialité supplémentaires pour répondre aux modifications des exigences globales.
* Amélioration de la conversion liée aux requêtes hiérarchiques.

## <a name="ssma-v79"></a>SSMA v 7.9

La version v 7.9 de SSMA pour Oracle contient les modifications suivantes:

* Correctifs ciblés qui améliorent les mesures de qualité et de conversion.
* Prise en charge de la migration des instructions «continue» d’Oracle vers SQL Server.
* Prise en charge dans la ligne de commande SSMA pour modifier le mappage du type de données et les préférences du projet.
* Prise en charge de la migration de données à l’aide de SQL Server Integration Services (SSIS). Après la conversion du schéma, il est possible de créer un package SSIS à l’aide d’un clic droit de la bouton du menu contextuel.
* La boîte de dialogue de connexion Azure SQL Database dans SSMA a également été modifiée pour spécifier le nom de serveur complet. Dans les versions précédentes de SSMA, le préfixe Azure SQL Database devait être mentionné explicitement dans les paramètres des projets.

## <a name="ssma-v78"></a>SSMA v 7.8

La version 7.8 de SSMA pour Oracle contient les modifications suivantes:

* Prise en charge de:
  * Expression de ligne pour la clause IN.
  * Casts de type implicite.
  * Conversion d’UID pour Azure SQL Database.
* Modifiez le mappage de type mis en surbrillance dans les paramètres du projet.
* La possibilité pour les utilisateurs de désactiver la télémétrie.

## <a name="ssma-v77"></a>SSMA v 7.7

La version de SSMA pour Oracle du v 7.7 contient les modifications suivantes:

* SSMA pour Oracle a été amélioré avec des correctifs ciblés qui améliorent la qualité et les mesures de conversion.
* En fonction de la demande populaire, la version 32 bits de SSMA pour Oracle est de retour. Par rapport à l’implémentation précédente (avant la version 7.4), il existe deux packages d’installation, mais ils ne peuvent pas être installés côte à côte. Par conséquent, vous devez choisir la version la plus appropriée en fonction des composants de connectivité dont vous disposez. Il est toujours préférable d’utiliser la version 64 bits, si possible.
* La prise en charge de SQL Server 2017 est désormais officielle avec le pack d’extension Oracle pris en charge sur Linux également (nouvelle option d’installation à distance). Notez que les fonctionnalités du pack d’extension sont limitées lorsqu’elles sont installées sur Linux, car les fonctionnalités d’essai et de migration des données côté serveur ne sont pas prises en charge.
* SSMA pour Oracle vous permet de migrer des vues matérialisées en tant que tables standard (configurables via les paramètres dans les **paramètres** -> du projet**synchronisation** -> **découvrir les tables de stockage pour les vues matérialisées**).

## <a name="ssma-v76"></a>SSMA v 7.6

La version v 7.6 de SSMA pour Oracle a été améliorée avec des correctifs ciblés qui améliorent les mesures de qualité et de conversion et prennent en charge SQL Server 2017 (version préliminaire publique). La prise en charge de SQL Server 2017 sur Windows et Linux est en version préliminaire publique et ne doit pas être utilisée pour les migrations de production.

## <a name="ssma-v75"></a>SSMA v 7.5

La version 7.5 de SSMA pour Oracle contient les modifications suivantes:

* Amélioration de plusieurs améliorations pour garantir une meilleure accessibilité aux personnes handicapées.
* Mise à jour pour améliorer la mesure de qualité et de conversion avec des correctifs ciblés, tels que la gestion améliorée des types de données date et float pendant la migration des données, en fonction des commentaires des clients.

## <a name="ssma-v74"></a>SSMA v 7.4

La version 7.4 de SSMA pour Oracle contient les modifications suivantes:

* SSMA pour Oracle prend désormais en charge Azure SQL Data Warehouse comme plateforme cible pour la migration.

  ![Fenêtre nouveau projet](../media/new-project.png)
  * Prend en charge les options de stockage Data Warehouse, comme indiqué dans l’image suivante:

  ![options de stockage pour l’entrepôt de données](../media/storage-options_red.png)
  * Prend en charge les options de distribution de données comme indiqué dans l’image suivante:

  ![distribution des données pour l’entrepôt de données](../media/data-distribution_red.png)

* L’option **délai de requête** est désormais disponible pendant la découverte d’objets de schéma à la source et à la cible.

  ![option délai d’expiration de la requête](../media/query-timeout_red.png)

* La mesure de qualité et de conversion a été améliorée avec les correctifs ciblés, en fonction des commentaires des clients.

> [!IMPORTANT]
> .Net 4.5.2 est une condition préalable à l’installation de SSMA v 7.4. En outre, à compter de la version 7.4, la version 32 bits de SSMA n’est plus disponible.

## <a name="ssma-v73"></a>SSMA v 7.3

La version 7.3 de SSMA pour Oracle contient les modifications suivantes:

* Amélioration de la qualité et de la mesure de conversion avec des correctifs ciblés basés sur les commentaires des clients.
* Infrastructure d’extensibilité SSMA exposée via les éléments suivants:
  * Exportez les fonctionnalités vers un projet SQL Server Data Tools (SSDT).
    * Vous pouvez maintenant exporter des scripts de schéma de SSMA vers un projet SSDT. Vous pouvez utiliser les scripts de schéma pour apporter des modifications de schéma supplémentaires et déployer votre base de données.

      ![Enregistrer en tant que projet SSDT, commande](../media/export-schema-scripts_red.png)
  * Bibliothèques pouvant être consommées par SSMA pour effectuer des conversions personnalisées.
    * Vous pouvez désormais construire du code capable de gérer les conversions de syntaxe personnalisées et les conversions qui n’ont pas été traitées précédemment par SSMA.
      * Des instructions sur la construction d’un convertisseur personnalisé sont disponibles dans ce billet de blog, qui [étend les fonctionnalités de conversion de Assistant Migration SQL Server](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      * Téléchargez un exemple de projet pour la conversion à partir de ce billet de [blog](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).

## <a name="ssma-v72"></a>SSMA v7.2

La version 7.2 de SSMA pour Oracle contient les modifications suivantes:

* Amélioration de la qualité et de la mesure de conversion avec des correctifs ciblés basés sur les commentaires des clients.
* Améliorations de la télémétrie pour fournir de meilleurs points de données afin de résoudre les problèmes des clients et d’améliorer les taux de conversion de SSMA.

## <a name="ssma-v71"></a>SSMA v 7.1

La version 7.1 de SSMA pour Oracle contient les modifications suivantes:

* SQL Server 2017 sur Windows et Linux CTP1 est désormais une plateforme cible prise en charge pour la migration. Cette fonctionnalité est en version d’évaluation technique et permet le déplacement des schémas et des données vers les serveurs SQL Server.
* SSMA prend désormais en charge les mises à jour automatiques pour télécharger la dernière version de SSMA dès qu’elle est disponible.
* Les fichiers binaires de SSMA installables sont désormais fournis via des fichiers de package Windows Installer (. msi).

## <a name="may-2016"></a>Mai 2016

La version 2016 de SSMA pour Oracle contient les modifications suivantes:  

* Ajout de la prise en charge de SQL Server 2016.
* Ajout de la conversion des tables d’archive Oracle Flashback en SQL Server tables temporelles.

  > [!NOTE]
  > SSMA ne copie pas les données d’historique des tables d’archive de données Oracle Flashback. Par conséquent, les données d’historique doivent être copiées manuellement pendant le processus de migration. En outre, alors que SSMA n’affiche pas la table d’historique dans le SQL Server l’Explorateur de métadonnées, car il est traité comme une table système, vous pouvez afficher la table d’historique dans SQL Server Management Studio.
  >
  > SQL Server 2016 ne prend pas en charge plusieurs fonctionnalités d’Oracle Flashback, notamment:
  >
  > * Requête de transaction Oracle Flashback
  > * Package DBMS_FLASHBACK
  > * Transaction Flashback
  > * Archive de données Flashback
  > * Table Flashback
  > * Insertion de flashback
  > * Base de données Flashback
* Ajout de la conversion de la stratégie Oracle VPD en objets de stratégie SQL Server (Sécurité au niveau des lignes pour Oracle).
* Réduction du temps de chargement initial pour Oracle.
* Analyseur et résolveur améliorés.
* Vérification de l’installation de .NET 2,0 supprimée.
* Dépendance de Pack d’extension mise à jour entre .net 3,5 et .net 4,0.
* Correction des commandes «enregistrer le projet» et «ouvrir le projet» pour la console SSMA.
* Correction de la commande «SecurePassword» pour la console SSMA.
* Correction du décompte des objets pour le chargement initial.
* Correction de la conversion des types de données caractères pour Oracle.
* Correction du bogue dans les paramètres globaux.
  
## <a name="march-2016"></a>Mars 2016

La version préliminaire de SSMA de mars 2016 de SSMA pour Oracle a ajouté la prise en charge de:  
  
* Migration vers SQL Server 2016.  
* Migration d’Sécurité au niveau des lignes Oracle (avec certaines limitations).  
* Migration d’Oracle dans des tables de mémoire vers SQL Server magasin de colonnes.  
  
## <a name="january-2016"></a>2016 janvier

La version de maintenance de SSMA pour Oracle de janvier 2014 contient les modifications suivantes:  
  
* Ajout de la prise en charge des index cluster.  
* Résolution des requêtes de schéma Oracle lentes (RFC 5076207).  
* Correction de la connexion à Azure à partir de la console.  
* Ajout de l’élément de menu de l’affichage du journal à SSMA (RFC 5706203). 
* Ajout de données de télémétrie.
  
## <a name="july-2014"></a>2014 juillet

La version 2014 de SSMA pour Oracle de juillet contient les modifications suivantes:  
  
* Ajout de la prise en charge d’Azure SQL DB.
* Fonctionnalités du pack d’extension déplacées vers le schéma pour la prise en charge d’Azure SQL DB.
* Ajout de la prise en charge des vues matérialisées Oracle.  
* Ajout de la prise en charge de SQL Server de tables optimisées en mémoire 2014.  
* Améliorations des performances incluses testées pour les bases de données avec plus de 10 000 objets.  
* Ajout d’améliorations de l’interface utilisateur pour le traitement d’un grand nombre d’objets.  
* Ajout de la mise en surbrillance des schémas LOB «bien connus».  
* Améliorations de la vitesse de conversion incluses.  
* Ajout de la prise en charge de l’indication du nombre d’objets dans l’interface utilisateur.  
* Réduction de la taille du rapport de plus de 25%.
* Amélioration des messages d’erreur pour les constructions non analysées.  
  
## <a name="april-2014"></a>2014 avril

La version d’avril 2014 de SSMA pour Oracle contient les modifications suivantes:  
  
* Ajout de la prise en charge de MS SQL Server 2014.  
* Ajout de la prise en charge d’Oracle 12 et de l’optimisation des requêtes.  
* Correction des bogues concernant la conversion vers Azure.  
* Correction des bogues concernant les pages de rapport invisibles dans IE 10.  
  
## <a name="january-2012"></a>2012 janvier

La version de 2012 janvier de SSMA pour Oracle ajoute la prise en charge des paramètres d’entrée RowType et RecordType par défaut avec la valeur NULL.  
  
## <a name="july-2011"></a>2011 juillet

La version 2011 de SSMA pour Oracle de juillet contient les modifications suivantes:  
  
* Ajout de la prise en charge de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conversion de la séquence Oracle en générateur de séquence «Denali».
* Amélioration des rapports d’erreurs lors de la migration des données.  
* Conversion améliorée de l’instruction à l’aide de mots réservés.  
* Amélioration de la conversion implicite de la valeur de date dans une fonction.  
  
## <a name="april-2011"></a>2011 avril

La version d’avril 2011 de SSMA pour Oracle contient les modifications suivantes:  
  
* Le produit «SSMA pour Oracle» consolidé, qui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] charge 2005 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , 2008 et «Denali».
* Ajout de la prise en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la connexion et de la migration vers «Denali».  
* Moteur de migration de données côté client amélioré, prenant en charge la migration parallèle des données.  
* Amélioration des performances de migration des données avec des modes de récupération simple et journalisée en bloc.  
* Ajout de la prise en charge de la compatibilité descendante des projets créés par des versions antérieures de SSMA (v 4.0 et v 4.2).  
* Ajout de la possibilité d’installer SSMA pour le produit Oracle v 5.0 côte à côte (SxS) avec les versions antérieures de SSMA (v 4.0 et v 4.2).
* Ajout de la prise en charge de la création de rapports pour les types définis par l’utilisateur (notamment SubType, VARRAY, TABLE IMBRIQUÉe, table objet et vue objet) et leur utilisation dans les blocs PL/SQL avec des messages d’erreur spéciaux.  

## <a name="july-2010"></a>2010 juillet

La version de 2010 de SSMA pour Oracle a été ajoutée:

* Prise en charge de la migration vers SQL Server 2008 R2.  
* Nouvelle application console SSMA pour l’exécution à partir de la ligne de commande.  
* Prise en charge de la migration des données à l’aide des moteurs de migration de données côté serveur et côté client.  
* Prise en charge de l’instruction «Custom SELECT» dans la migration de données.  
* Prise en charge de la migration à partir d’Oracle 11g R2.  
  
## <a name="june-2008"></a>2008 juin

La version de 2008 de SSMA pour Oracle contient les modifications suivantes:  
  
* Améliorations apportées au rapport d’évaluation, y compris des informations supplémentaires pour les synonymes, la source brute pour les objets analysables, les panneaux et la SQL Server la suppression du logo et la persistance de la disposition.  
* Améliorations ajoutées à la conversion d’objets:  
  * Packages DBMS_LOB, conversion DBMS_SQL ajoutée.  
  * Conversion de jointures révisée.  
  * Modification des regroupements et de la conversion des enregistrements, conversion des enregistrements dans des cas simples libérés par des variables distinctes pour chaque champ.  
  * Améliorations de l’implémentation des enregistrements et des collections.  
  * Fonctions d’agrégation de fenêtrage ajoutées.  
  * Clause ROLLUP/CUBE ajoutée.  
  * Amélioration de NEXTVAL/courbure.  
  * Le regroupement de colonnes dans la clause SET, les groupes de regroupement et l’ID de regroupement ont été ajoutés.  
  * Instruction MERGE ajoutée.  
  * Prise en charge des nouveaux types DateTime et de la conversion des enregistrements et des collections en tant que types de données CLR ajoutés.  
* Ajout de nouvelles fonctionnalités du testeur. Les tables peuvent désormais être testées en tant qu’objets à l’aide du testeur. un ordre d’appel de plusieurs objets testables dans un cas de test peut être modifié, l’utilisateur peut tester des procédures et des fonctions avec des enregistrements et des collections comme paramètres et valeurs de retour, et un analyseur de dépendances a été ajouté à la vérification tables utilisées uniquement.  
  
## <a name="august-2007"></a>2007 août

La version d’août 2007 de SSMA pour Oracle a été ajoutée:

* Un nouveau composant testeur vous permet de créer, gérer et exécuter des cas de test pour vérifier le code SQL converti.  
* La prise en charge de la conversion des sous-types Oracle, des collections et des modules locaux a été ajoutée au convertisseur SQL.  
* Une nouvelle fonctionnalité de synchronisation vous permet de synchroniser des objets spécifiques avec SQL Server base de données.  
* Nouvelles options de conversion.  
  
## <a name="april-2007"></a>2007 avril

La version d’avril 2007 de SSMA pour Oracle était la version initiale.
