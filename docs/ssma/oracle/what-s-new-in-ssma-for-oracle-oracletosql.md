---
title: Quelles sont les nouveautés de SSMA pour Oracle (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 03/06/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f305ebb6-7393-4a43-abb3-6332b739d690
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 1d28ddc0ca3338c9f3a5f8e9e912efa90f6cbcfa
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527102"
---
# <a name="whats-new-in-ssma-for-oracle-oracletosql"></a>Quelles sont les nouveautés de SSMA pour Oracle (OracleToSQL)
Cet article répertorie les SQL Server Migration Assistant (SSMA) pour les modifications d’Oracle dans chaque version.

## <a name="ssma-v81"></a>SSMA v8.1
La version v8.1 de SSMA pour Oracle a été améliorée avec des correctifs ciblés visant qui est conçues pour améliorer la qualité et conversion des mesures.

> [!NOTE]
> Un problème connu avec la mise à jour automatique peut entraîner l’échec d’une mise à jour à partir de la version 8.0 SSMA pour v8.1. Si vous rencontrez cette erreur, veuillez télécharger la nouvelle version et l’installer manuellement.

> [!IMPORTANT]
> Avec SSMA v7.4 et versions ultérieures, .net 4.5.2 est un préalable de l’installation.

## <a name="ssma-v80"></a>SSMA v8.0
La version 8.0 de SSMA pour Oracle a été améliorée avec des correctifs ciblés visant conçues pour améliorer la qualité et conversion des mesures. Cette version offre également les nouvelles fonctionnalités suivantes :

* Prise en charge de **Azure SQL Database Managed Instance** en tant que cible. Vous pouvez désormais créer des projets ciblant Azure SQL Database Managed Instance :

  ![Projet de base de données SQL MI](../media/ssma-newproject-sqldbmi.png)

    > [!NOTE]
    > SSMA pour Oracle le Pack d’Extension a été également mis à jour pour autoriser les installations à distance sur Azure SQL Database Managed Instance :
    >
    > ![SSMA pour Oracle le Pack d’Extension](../media/ssma-oracle-ext-pack.png)

    Certaines fonctionnalités, notamment la migration des données testeur et côté serveur, ne sont pas pris en charge lors du ciblage d’Azure SQL Database Managed Instance. En savoir plus sur elle [ici](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/migrate-your-oracle-database-to-azure-sql-database-managed-instance-using-ssma-8-0/).

*   Après la conversion **correctif advisor**. En savoir plus sur elle [ici](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Sélection de la base de données/schémas préliminaire.

    Lors de la connexion à la source, l’utilisateur peut sélectionner maintenant les bases de données/schémas d’intérêt. En sélectionnant uniquement les schémas que vous projetez de migrer pour gagner du temps lors de la connexion initiale et améliorer les performances globales de SSMA.

    ![Filtrer les objets SSMA](../media/ssma-filter-objects.png)

* La possibilité d’utiliser le pilote NET officiel et géré pour vous connecter à Oracle. Le pilote OCI n’est plus une condition préalable à l’aide de l’Assistant Migration de SQL Server pour Oracle.

* La capacité de mapper des ROWID et UROWID à VARCHAR par défaut. Remplacé par 'uniqueidentifier' pour prendre en charge la migration des données pour les colonnes ROWID explicites.

## <a name="ssma-v710"></a>SSMA v7.10
La version v7.10 de SSMA pour Oracle contient les modifications suivantes :
- Les correctifs ciblés visant conçu pour fournir une sécurité supplémentaire et protections de la confidentialité pour répondre aux modifications apportées aux spécifications globales.
- Une amélioration de la conversion concernant les requêtes hiérarchiques.

## <a name="ssma-v79"></a>SSMA v7.9
La version v7.9 de SSMA pour Oracle contient les modifications suivantes :
- Correctifs ciblés visant qui améliorent la qualité et conversion des mesures.
- Prise en charge pour la migration des instructions « Continue » à partir d’Oracle vers SQL Server.
- Prend en charge dans la ligne de commande SSMA pour modifier le mappage de Type de données et les préférences du projet.
- Prise en charge pour la migration de données à l’aide de SQL Server Integration Services (SSIS). Après avoir converti le schéma, il est possible de créer un package SSIS à l’aide d’une option de menu contextuel.
- La boîte de dialogue de connexion de base de données SQL Azure dans SSMA a également été modifié pour spécifier le nom complet du serveur. Dans les versions précédentes de SSMA, le préfixe de la base de données SQL Azure devait être mentionnée explicitement à l’intérieur des paramètres des projets.

## <a name="ssma-v78"></a>SSMA v7.8
La version v7.8 de SSMA pour Oracle contient les modifications suivantes :
-   Prise en charge pour :
    - Expression de la ligne de la clause IN.
    - Casts de type implicite.
    - Conversion de UID pour une base de données SQL Azure.
- Modifier le mappage de type mis en surbrillance dans les paramètres du projet.
- La capacité des utilisateurs à désactiver la télémétrie.

## <a name="ssma-v77"></a>SSMA v7.7
La version v7.7 de SSMA pour Oracle contient les modifications suivantes :
- SSMA pour Oracle a été amélioré avec des correctifs ciblés qui améliorent les métriques de qualité et de conversion.
- Selon l’à la demande générale, la version 32 bits de SSMA pour Oracle est de retour. Par rapport à l’implémentation précédente (avant v7.4), il existe deux packages de programme d’installation, mais ils ne peuvent pas être installés côte à côte. Par conséquent, vous devez choisir la version la plus appropriée en fonction des composants de connectivité que vous disposez. Il est toujours préférable d’utiliser la version 64 bits, si possible.
- Prise en charge de SQL Server 2017 est désormais officiel avec le Pack d’Extension Oracle sur Linux également pris en charge (nouvelle option d’installation à distance). Notez que les fonctionnalités du Pack d’Extension sont limitée lors de l’installation sur Linux, comme le testeur et fonctionnalités de migration de données côté serveur ne sont pas prises en charge.
- SSMA pour Oracle permet d’effectuer une migration des vues matérialisées en tant que tables régulières (configurable via les paramètres au **paramètres du projet** -> **synchronisation**  ->  **Détecter des tables de stockage pour les vues matérialisées**).

## <a name="ssma-v76"></a>SSMA v7.6
La version v7.6 de SSMA pour Oracle a été améliorée avec des correctifs ciblés visant qui améliorent la qualité et conversion des mesures et prise en charge de SQL Server 2017 (version préliminaire publique). Prise en charge de SQL Server 2017 sur Windows et Linux en version préliminaire publique et ne doit pas être utilisé pour les migrations de production.

## <a name="ssma-v75"></a>SSMA v7.5
La version v7.5 de SSMA pour Oracle contient les modifications suivantes :
- Amélioré avec plusieurs améliorations pour garantir une meilleure accessibilité des personnes handicapées.
- Mise à jour pour améliorer les mesures de qualité et de conversion avec correctifs ciblés visant, telles que l’amélioration de la gestion des types de données de date et float pendant la migration de données, en fonction des commentaires des clients.

## <a name="ssma-v74"></a>SSMA v7.4
La version v7.4 de SSMA pour Oracle contient les modifications suivantes :

- SSMA pour Oracle prend désormais en charge Azure SQL Data Warehouse comme plateforme cible pour la migration.

    ![Fenêtre Nouveau projet](../media/new-project.png)
  - Prend en charge les options de stockage de l’entrepôt de données comme indiqué dans l’image suivante :

    ![options de stockage pour l’entrepôt de données](../media/storage-options_red.png)
  - Prend en charge les options de distribution de données comme indiqué dans l’image suivante :

    ![répartition des données d’entrepôt de données](../media/data-distribution_red.png)

- Le **Query timeout** option est désormais disponible au cours de la découverte d’objets de schéma à la source et cible.

    ![option de délai d’attente de requête](../media/query-timeout_red.png)

- Les mesures de qualité et la conversion a été améliorée avec des correctifs ciblés, en fonction des commentaires des clients.

> [!IMPORTANT]
> .NET 4.5.2 est requis pour l’installation de SSMA v7.4. En outre, à compter de v7.4, la version 32 bits de SSMA est en cours de retrait.

## <a name="ssma-v73"></a>SSMA v7.3
La version v7.3 de SSMA pour Oracle contient les modifications suivantes :
- Métrique de qualité et de conversion améliorée avec des correctifs ciblés en fonction des commentaires des clients.
- Infrastructure d’extensibilité SSMA exposé via les éléments suivants :
  - Fonctionnalité d’exportation à un projet SQL Server Data Tools (SSDT).
    -   Vous pouvez désormais exporter des scripts de schéma à partir de SSMA pour un projet SSDT. Vous pouvez utiliser les scripts de schéma pour apporter des modifications de schéma supplémentaires et de déployer votre base de données.

        ![Enregistrer en tant que commande de projet SSDT](../media/export-schema-scripts_red.png)
  - Bibliothèques qui peuvent être consommées par SSMA pour effectuer des conversions personnalisées.
    - Vous pouvez désormais construire le code qui peut gérer les conversions de syntaxe personnalisée et les conversions qui n’ont pas été précédemment gérées par SSMA.
      - Obtenir des instructions sur la construction d’un convertisseur personnalisé sont disponibles dans ce billet de blog, [fonctions de conversion d’extension Assistant Migration SQL Server](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/).
      - Télécharger un exemple de projet pour la conversion à partir de ce [billet de blog](https://blogs.msdn.microsoft.com/datamigration/ssmafororacleconversionsample/).


## <a name="ssma-v72"></a>SSMA v7.2
La version v7.2 de SSMA pour Oracle contient les modifications suivantes :
- Métrique de qualité et de conversion améliorée avec des correctifs ciblés en fonction des commentaires des clients.
- Améliorations de télémétrie pour fournir une meilleure points de données pour résoudre les problèmes des clients et d’améliorer le taux de conversion de SSMA.

## <a name="ssma-v71"></a>SSMA v7.1
La version v7.1 de SSMA pour Oracle contient les modifications suivantes :
- SQL Server 2017 sur Windows et Linux CTP1 est désormais une plateforme cible prise en charge pour la migration. Cette fonctionnalité est dans technical preview et permet le déplacement de schéma et les données aux serveurs de SQL Server cible.
- SSMA prend désormais en charge les mises à jour automatiques pour télécharger la dernière version de SSMA dès qu’il est disponible.
- Fichiers binaires installables SSMA sont maintenant fournies via fichiers de package Windows installer (.msi).

**Ressources**

[Extension des fonctionnalités de SQL Server Migration Assistant conversion](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[Évaluer et migrer des données à partir des plateformes de données non Microsoft pour SQL Server *(avec l’exemple d’Oracle)*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>Mai 2016  
La version de mai 2016 de SSMA pour Oracle contient les modifications suivantes :  

- Prise en charge pour SQL Server 2016.
- Conversion Ajout de tables d’archives Oracle flashback aux tables temporelles de SQL Server.

    **Remarque** -SSMA ne copie pas les données de l’historique à partir de tables d’archives de données Oracle Flashback. Par conséquent, les données d’historique doivent être copiées manuellement pendant le processus de migration. En outre, SSMA n’affiche pas la table d’historique dans l’Explorateur de métadonnées SQL Server, car elle est traitée comme une table système, vous pouvez consulter la table d’historique dans SQL Server Management Studio.
    SQL Server 2016 ne prend pas en charge plusieurs fonctionnalités Oracle Flashback, notamment :
    - Requêtes de Transaction Oracle Flashback
    - Package DBMS_FLASHBACK
    - Transaction de fonction Flashback
    - Archive de données Flashback
    - Flashback Table
    - Flashback Drop
    - Base de données Flashback
- Ajout de conversion d’Oracle VPD stratégie aux objets de stratégie de SQL Server (sécurité de niveau ligne pour Oracle).
- Une diminution des temps de chargement initial pour Oracle.
- Analyseur améliorée et programme de résolution.
- Supprimé la vérification du programme d’installation pour .net 2.0.
- Dépendance Extension Pack mis à jour à partir de .net 3.5 vers .net 4.0.
- Fixe « enregistrer le projet » et « ouvrir le projet » des commandes pour la Console SSMA.
- Commande fixe « securepassword » pour la Console SSMA.
- Correction de comptage des objets pour le chargement initial.
- Correction de la conversion des types de données caractères pour Oracle.
- Résolution de bogue dans les paramètres globaux.
  
## <a name="march-2016"></a>Mars 2016  
La version préliminaire de mars 2016 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge pour la migration vers SQL Server 2016.  
-   Prise en charge pour la migration Oracle la sécurité de ligne (avec certaines restrictions).  
-   Prise en charge pour la migration des tables Oracle dans la mémoire pour SQL Server colonne Store.  
  
## <a name="january-2016"></a>Janvier 2016  
Le janvier 2014 mise à jour de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge les index cluster.  
-   Correction des requêtes de schéma Oracle lentes (RFC 5076207).  
-   Fixe se connecter à Azure à partir de la console.  
-   Élément de Menu ajouté vue journal pour SSMA (RFC 5706203). 
-   Ajout de télémétrie.  
  
## <a name="july-2014"></a>Juillet 2014  
La version de juillet 2014 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge ajoutée pour la base de données SQL Azure.  
-   Fonctionnalité du pack d’extension déplacé au schéma pour prendre en charge de la base de données SQL Azure.  
-   Prise en charge pour les vues matérialisées Oracle.  
-   Tables optimisées en prise en charge pour la mémoire de SQL Server 2014.  
-   Améliorations des performances inclus testé pour les bases de données avec plus de 10k objets.  
-   Améliorations de l’interface utilisateur ajoutées pour traiter avec un grand nombre d’objets.  
-   Ajouté la mise en surbrillance des schémas LOB « connues ».  
-   Améliorations de la vitesse conversion inclus.  
-   Prise en charge ajoutée pour afficher l’objet de compte dans l’interface utilisateur.  
-   Taille de rapport réduit de plus de 25 %.
-   Messages d’erreur améliorés pour les constructions non analysées.  
  
## <a name="april-2014"></a>Avril 2014  
La version d’avril 2014 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge ajoutée de MS SQL Server 2014.  
-   Prise en charge d’optimisation Oracle 12 et de la requête.  
-   Bogues résolus concernant la conversion vers Azure.  
-   Bogues résolus concernant les pages de rapport invisible dans Internet Explorer 10.  
  
## <a name="january-2012"></a>Janvier 2012  
La version de janvier 2012 de SSMA pour Oracle prend en charge RowType et RecordType des paramètres d’entrée par défaut NULL.  
  
## <a name="july-2011"></a>Juillet 2011  
La version de juillet 2011 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge pour la conversion de la séquence Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Générateur de séquence « Denali ».  
-   Amélioration signalement d’erreurs pendant la migration des données.  
-   Conversion améliorée d’instruction à l’aide de mots réservés.  
-   Amélioration de la conversion implicite de la valeur de date dans une fonction.  
  
## <a name="april-2011"></a>Avril 2011  
La version d’avril 2011 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Produit consolidé « SSMA pour Oracle », qui prend en charge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] « Denali ».  
-   Prise en charge pour la connexion et la migration vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] « Denali ».  
-   Moteur de migration améliorée des données côté client, prise en charge de la migration parallèle des données.  
-   Performances de migration de données améliorées avec Simple et en bloc connecté les modes de récupération.  
-   Prise en charge pour la compatibilité descendante des projets créés par les versions antérieures de SSMA (version 4.0 et v4.2).  
-   Ajouté la possibilité d’installer SSMA pour Oracle v5.0 produit côte à côte (SxS) avec les versions antérieures de SSMA (version 4.0 et v4.2).  
-   Prise en charge les Types définis par l’utilisateur (inclut le sous-type VARRAY, la TABLE imbriquée, table des objets et affichage de l’objet) et leurs utilisations dans des blocs de PL/SQL avec des messages d’erreur spéciale de création de rapports.  

## <a name="july-2010"></a>Juillet 2010  
La version de juillet 2010 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge pour la migration vers SQL Server 2008 R2.  
-   Ajouter une nouvelle application de Console SSMA pour l’exécution de ligne de commande.  
-   Prise en charge la Migration des données à l’aide côté serveur et côté Client des moteurs de Migration de données.  
-   Prise en charge ajoutée pour l’instruction de « SELECT personnalisé » dans la migration des données.  
-   Prise en charge pour la migration à partir d’Oracle 11g R2.  
  
## <a name="june-2008"></a>Juin 2008  
La version de juin 2008 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Ajout d’améliorations au rapport d’évaluation, y compris des informations supplémentaires pour les synonymes, source brute d’objets à analyser, panneaux et la suppression de logo de SQL Server et persistance de disposition.  
-   Ajout d’améliorations dans la conversion de l’objet :  
    -   Packages DBMS_LOB, conversion DBMS_SQL ajouté.  
    -   Joint conversion révisée.  
    -   Modification des collections et des enregistrements de conversion, désormais une conversion d’enregistrements dans les cas simples, publiées par le biais des variables distinctes pour chaque champ.  
    -   Améliorations de mise en œuvre des enregistrements et des collections.  
    -   Fonctions d’agrégation de fenêtrage ajoutées.  
    -   Clause ROLLUP/CUBE ajoutée.  
    -   Amélioration du produit pour NEXTVAL/CURVAL.  
    -   Colonnes de regroupement dans la clause SET, jeux de regroupement et de regroupement d’ID ont été ajoutées.  
    -   Ajouté des instructions de fusion.  
    -   Prise en charge des nouveaux types date/heure et de conversion des enregistrements et les collections en tant que types de données CLR ajoutés.  
-   Ajout de nouvelles fonctionnalités de testeur. Tables peuvent maintenant être testées en tant qu’objets à l’aide du testeur, un ordre d’appel de plusieurs objets testables dans les cas de test peut être modifié, utilisateur permettre tester les procédures et des fonctions avec des enregistrements et les collections comme paramètres et valeurs de retour, et un analyseur de dépendances a été ajouté pour vérifier seulement les tables utilisées.  
  
## <a name="august-2007"></a>Août 2007  
La version d’août 2007 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Ajouter qu'un nouveau composant de testeur vous permet de créer, gérer et exécuter des cas de test pour vérifier le code SQL converti.  
-   Prise en charge pour la conversion des sous-types Oracle, les collections et les modules locaux ont été ajoutées au convertisseur de SQL.  
-   Ajouter qu'une nouvelle fonctionnalité de synchronisation vous permet de synchroniser des objets spécifiques avec la base de données SQL Server.  
-   Nouvelles options de conversion ajouté.  
  
## <a name="april-2007"></a>Avril 2007  
La version d’avril 2007 de SSMA pour Oracle était la version initiale.
