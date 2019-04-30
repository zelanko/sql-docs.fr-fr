---
title: Quelles sont les nouveautés de SSMA pour Access(AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 03/06/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: a24d3fc0-6911-4bfa-828a-197abf222e02
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7557a34698f90054806aeafe9b7285970af092c3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63299069"
---
# <a name="whats-new-in-ssma-for-access-accesstosql"></a>Nouveautés de SSMA pour Access (AccessToSQL)
Cet article répertorie les SQL Server Migration Assistant (SSMA) pour les modifications d’accès dans chaque version.  

## <a name="ssma-v81"></a>SSMA v8.1
La version v8.1 de SSMA pour Access a été améliorée avec des correctifs ciblés visant qui est conçues pour améliorer la qualité et conversion des mesures.

> [!NOTE]
> Un problème connu avec la mise à jour automatique peut entraîner l’échec d’une mise à jour à partir de la version 8.0 SSMA pour v8.1. Si vous rencontrez cette erreur, veuillez télécharger la nouvelle version et l’installer manuellement.

> [!IMPORTANT]
> Avec SSMA v7.4 et versions ultérieures, .net 4.5.2 est un préalable de l’installation.

## <a name="ssma-v80"></a>SSMA v8.0
La version de la version 8.0 de SSMA pour Access a été améliorée avec des correctifs ciblés visant conçues pour améliorer la qualité et conversion des mesures. Cette version offre également les nouvelles fonctionnalités suivantes :

* Prise en charge de **Azure SQL Database Managed Instance** en tant que cible. Vous pouvez désormais créer des projets ciblant Azure SQL Database Managed Instance :

  ![Projet de base de données SQL MI](../media/ssma-newproject-sqldbmi.png)

*   Après la conversion **correctif advisor**. En savoir plus sur elle [ici](https://blogs.msdn.microsoft.com/datamigration/2019/02/17/%20accelerate-your-oracle-migrations-with-new-machine-learning-capabilities-in-ssma/).

* Sélection de la base de données/schémas préliminaire.

    Lors de la connexion à la source, l’utilisateur peut sélectionner maintenant les bases de données/schémas d’intérêt. En sélectionnant uniquement les schémas que vous projetez de migrer pour gagner du temps lors de la connexion initiale et améliorer les performances globales de SSMA.

    ![Filtrer les objets SSMA](../media/ssma-filter-objects.png)

## <a name="ssma-v710"></a>SSMA v7.10
La version v7.10 de SSMA pour Access a été améliorée avec des correctifs ciblés visant conçu pour fournir une sécurité supplémentaire et protections de la confidentialité pour répondre aux modifications apportées aux spécifications globales.

## <a name="ssma-v79"></a>SSMA v7.9
La version v7.9 de SSMA pour Access contient les modifications suivantes :
- Correctifs ciblés visant qui améliorent la qualité et conversion des mesures.
- Prend en charge dans la ligne de commande SSMA pour modifier le mappage de Type de données et les préférences du projet.
- La boîte de dialogue de connexion de base de données SQL Azure dans SSMA a également été modifié pour spécifier le nom complet du serveur. Dans les versions précédentes de SSMA, le préfixe de la base de données SQL Azure devait être mentionnée explicitement à l’intérieur des paramètres des projets.

## <a name="ssma-v78"></a>SSMA v7.8
La version v7.8 de SSMA pour Access contient les modifications suivantes :
- Modifier le mappage de type mis en surbrillance dans les paramètres du projet.
- La capacité des utilisateurs à désactiver la télémétrie.

## <a name="ssma-v77"></a>SSMA v7.7
La version v7.7 de SSMA pour Access contient les modifications suivantes :
- Correctifs ciblés visant qui améliorent la qualité et conversion des mesures.
- Selon l’à la demande générale, la version 32 bits de SSMA pour Access est de retour. Par rapport à l’implémentation précédente (avant v7.4), il existe deux packages de programme d’installation, mais ils ne peuvent pas être installé côte à côte. Par conséquent, vous devez choisir la version la plus appropriée en fonction des composants de connectivité que vous disposez. Il est toujours préférable d’utiliser la version 64 bits, si possible.

## <a name="ssma-v76"></a>SSMA v7.6
La version v7.6 de SSMA pour Access a été améliorée avec des correctifs ciblés visant qui améliorent la qualité et conversion des mesures et prise en charge de SQL Server 2017 (version préliminaire publique). Prise en charge de SQL Server 2017 sur Windows et Linux en version préliminaire publique et ne doit pas être utilisé pour les migrations de production.

## <a name="ssma-v75"></a>SSMA v7.5
La version v7.5 de SSMA pour Access a été améliorée avec plusieurs améliorations pour garantir une meilleure accessibilité des personnes handicapées.

## <a name="ssma-v74"></a>SSMA v7.4
La version v7.4 de SSMA pour Access contient les modifications suivantes :
- Le **Query timeout** option est désormais disponible au cours de la découverte d’objets de schéma à la source et cible.
 
    ![option de délai d’attente de requête](../media/query-timeout_red.png)

- Les mesures de qualité et la conversion a été améliorée avec des correctifs ciblés, en fonction des commentaires des clients.

> [!IMPORTANT]
> .NET 4.5.2 est requis pour l’installation de SSMA v7.4. En outre, à compter de v7.4, la version 32 bits de SSMA a disparu.

## <a name="ssma-v73"></a>SSMA v7.3
La version v7.3 de SSMA pour Access contient les modifications suivantes :
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
La version v7.2 de SSMA pour Access contient les modifications suivantes :
- Métrique de qualité et de conversion améliorée avec des correctifs ciblés en fonction des commentaires des clients.
- Améliorations de télémétrie pour fournir une meilleure points de données pour résoudre les problèmes des clients et d’améliorer le taux de conversion de SSMA.

## <a name="ssma-v71"></a>SSMA v7.1
La version v7.1 de SSMA pour Access contient les modifications suivantes :
- SQL Server 2017 sur Windows et Linux CTP1 est désormais une plateforme cible prise en charge pour la migration. Cette fonctionnalité est dans technical preview et prend en charge le déplacement de schéma et les données aux serveurs de SQL Server cible.
- SSMA prend désormais en charge les mises à jour automatiques pour télécharger la dernière version de SSMA dès qu’il est disponible.
- Fichiers binaires installables SSMA sont maintenant fournies via fichiers de package Windows installer (.msi).

**Ressources**

[Extension des fonctionnalités de SQL Server Migration Assistant conversion](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)
  
## <a name="may-2016"></a>Mai 2016  
La version de mai 2016 de SSMA pour Access contient les modifications suivantes :  
  
-  Prise en charge officielle pour SQL Server 2016
-  Supprimé la vérification du programme d’installation pour .net 2.0.
-  Fixe « enregistrer le projet » et « ouvrir le projet » des commandes pour la Console SSMA.
-  Commande fixe « securepassword » pour la Console SSMA.
-  Correction de comptage des objets pour le chargement initial.
-  Chargement des données des tables fixe pour les onglets de l’interface utilisateur pour l’accès.
-  Résolution de bogue dans les paramètres globaux. 
   
## <a name="march-2016"></a>Mars 2016  
La version préliminaire de mars 2016 de SSMA pour Access ajoute la prise en charge pour la migration vers SQL Server 2016.  
   
## <a name="january-2016"></a>Janvier 2016  
La version de maintenance de janvier 2016 de SSMA pour Access contient les modifications suivantes :  
  
-  Fixe de fonction non valide pour la valeur par défaut d’un champ GUID (RFC 3894811).  
-  Blocage fixe sur l’importation d’enregistrements à la base de données SQL (Azure) (RFC 4919573).  
-  Élément de Menu ajouté vue journal pour SSMA (RFC 5706203).  
-  Ajout de télémétrie.  
  
## <a name="july-2014"></a>Juillet 2014  
La version de juillet 2014 de SSMA pour Access contient les modifications suivantes :  
  
-   Conversion de code de base de données SQL Azure améliorée.  
-   Déplacer la fonctionnalité du pack d’extension au schéma pour prendre en charge de la base de données SQL Azure.  
-   Améliorations des performances testés pour les bases de données avec plus de 10 objets k.  
-   Améliorations de l’interface utilisateur ajoutées pour traiter avec un grand nombre d’objets.  
-   Prise en charge pour la mise en surbrillance des schémas LOB « connues » (afin qu’ils peuvent être ignorés dans la conversion).  
-   Ajouté des améliorations de la vitesse de conversion.
-   Prise en charge ajoutée pour afficher l’objet de compte dans l’interface utilisateur.
-   Taille de rapport réduit de plus de 25 %.
-   Messages d’erreur améliorés pour les constructions non analysées.  
  
## <a name="april-2014"></a>Avril 2014  
La version d’avril 2014 de SSMA pour Access contient les modifications suivantes :  
  
-   Prise en charge MS SQL Server 2014.  
-   Bogues résolus concernant la conversion vers Azure.  
-   Bogues résolus concernant les pages de rapport invisible dans Internet Explorer 10.  
  
## <a name="january-2012"></a>Janvier 2012  
La version de janvier 2012 de SSMA pour Access contient les modifications suivantes :  
  
-   Fourni l’option n’est ne pas conservée nom d’utilisateur et mot de passe pour MS Access lié tables après la migration.  
-   Définir des actions en cascade les références circulaires No Action.  
-   Condition des messages appropriés indiquant les actions en cascade pour les références circulaires ont été définis pour No Action.  
  
## <a name="july-2011"></a>Juillet 2011  
La version de juillet 2011 de SSMA pour Access ajoute améliorée signalement d’erreurs pendant la migration des données.  
  
## <a name="april-2011"></a>Avril 2011  
La version d’avril 2011 de SSMA pour Access contient les modifications suivantes :  
  
-   Ajouter un seul installable de « SSMA pour Access », qui prend en charge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] « Denali » et SQL Azure.  
-   Ajouté la possibilité de connecter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] « Denali ».  
-   Ajout de SSMA pour la version de la Console d’accès prend en charge pour la compatibilité descendante. Vous pouvez ouvrir les projets créés par les versions antérieures à SSMA v5.0.
-   Ajouté la possibilité d’installer le produit SSMA v5.0 côte à côte (SxS) avec les versions antérieures du produit de SSMA.  
  
## <a name="july-2010"></a>Juillet 2010  
La version de juillet 2010 de SSMA pour Access contient les modifications suivantes :  
  
-   Prise en charge pour la migration vers SQL Server 2008 R2 et SQL Azure.
-   Ajouter une connexion sécurisée à SQL Server et SQL Azure.  
-   Prise en charge pour les bases de données Access 2010.
-   Ajouter une nouvelle application de Console SSMA pour l’exécution de ligne de commande.
-   Prise en charge pour le type de données DateTime2 SQL Server.
  
## <a name="june-2008"></a>Juin 2008  
La version de juin 2008 de SSMA pour Access ajoute la prise en charge des bases de données Access 2007.  
  
## <a name="may-2007"></a>Mai 2007  
La version de mai 2007 de SSMA pour Access contient les modifications suivantes :  
  
-   Prise en charge pour les bases de données Access qui utilisent des stratégies de groupe de travail.  
-   Fourni la possibilité de supprimer les objets convertis à partir de l’Explorateur de métadonnées SQL Server.  
-   Prise en charge pour les commentaires d’entré par l’utilisateur dans SQL Server mise en forme en mode SQL.  
-   Ajout d’améliorations dans la conversion de l’objet.  
  
## <a name="november-2006"></a>Novembre 2006  
La version de novembre 2006 de SSMA pour Access contient les modifications suivantes :  
  
-   Ajouter un nouvel Assistant de Migration de base de données qui vous guide à travers de la migration d’une base de données à partir de l’accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
-   Ajouté une nouvelle conversion, charge, et la commande Migrate qui convertit les bases de données Access, charge les objets convertis dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], et migre les données dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tout en une seule étape.  
-   Migration a amélioré les requêtes. Interroger la migration maintenant convertit les requêtes à des vues plus SELECT. Pour plus d’informations, consultez [conversion des objets de base de données Access](converting-access-database-objects-accesstosql.md).  
-   Ajouté la possibilité de modifier des propriétés de table et d’index sur la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Table** onglet.  
-   Ajouté de nouveaux paramètres globaux :  
    -   Vous pouvez choisir d’afficher les numéros de ligne dans les fenêtres de l’éditeur.  
    -   Vous pouvez configurer SSMA pour demander à remplacer les objets en double, ou toujours ou jamais remplacer des objets en double lors de la conversion de schéma.  
-   Ajout d’une nouvelle option de conversion qui vous permet de spécifier si SSMA affiche un avertissement lorsqu’une requête complexe contient un caractère générique.  
  
## <a name="july-2006"></a>Juillet 2006  
La version de juillet 2006 de SSMA pour Access était la version initiale.
