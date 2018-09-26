---
title: Quelles sont les nouveautés de SSMA pour SAP ASE (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/22/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2be0cf8d-6dbe-443a-abbd-036249922205
caps.latest.revision: 21
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 3ade0baa7e970639769cf5bdba522e54d3843771
ms.sourcegitcommit: 7076fcb854c033a5dbeac7fcb22c5e15cf8528fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46362033"
---
# <a name="whats-new-in-ssma-for-sap-ase-sybasetosql"></a>Quelles sont les nouveautés de SSMA pour SAP ASE (SybaseToSQL)
Cet article répertorie SSMA pour SAP ASE (anciennement SSMA pour Sybase) les modifications dans chaque version. 

## <a name="ssma-v710"></a>SSMA v7.10
La version v7.10 de SSMA pour SAP ASE a été améliorée avec des correctifs ciblés visant conçu pour fournir une sécurité supplémentaire et protections de la confidentialité pour répondre aux modifications apportées aux spécifications globales.

> [!IMPORTANT]
> Avec SSMA v7.4 et versions ultérieures, .net 4.5.2 est un préalable de l’installation.

## <a name="ssma-v79"></a>SSMA v7.9
La version v7.9 de SSMA pour SAP ASE contient les modifications suivantes :
- Correctifs ciblés visant qui améliorent la qualité et conversion des mesures.
- Prend en charge dans la ligne de commande SSMA pour modifier le mappage de Type de données et les préférences du projet.
- Prise en charge pour la migration de données à l’aide de SQL Server Integration Services (SSIS). Après avoir converti le schéma, il est possible de créer un package SSIS à l’aide d’une option de menu contextuel.
- La boîte de dialogue de connexion de base de données SQL Azure dans SSMA a également été modifié pour spécifier le nom complet du serveur. Dans les versions précédentes de SSMA, le préfixe de la base de données SQL Azure devait être mentionnée explicitement à l’intérieur des paramètres des projets.

> [!IMPORTANT]
> Avec SSMA v7.4 et versions ultérieures, .net 4.5.2 est un préalable de l’installation.

## <a name="ssma-v78"></a>SSMA v7.8
La version v7.8 de SSMA pour SAP ASE contient les modifications suivantes :
- Mappage du type de modifications mises en évidence dans les paramètres du projet.
- Fourni à la capacité des utilisateurs à désactiver la télémétrie.

> [!IMPORTANT]
> Avec SSMA v7.4 et versions ultérieures, .net 4.5.2 est un préalable de l’installation.

## <a name="ssma-v77"></a>SSMA v7.7
La version v7.7 de SSMA pour SAP ASE contient les modifications suivantes :
- SSMA pour SAP ASE a été amélioré avec des correctifs ciblés qui améliorent les métriques de qualité et de conversion.
- Selon l’à la demande générale, la version 32 bits de SSMA pour SAP ASE est de retour. Par rapport à l’implémentation précédente (avant v7.4), il existe deux packages de programme d’installation, mais ils ne peuvent pas être installés côte à côte. Par conséquent, vous devez choisir la version la plus appropriée en fonction des composants de connectivité que vous disposez. Il est toujours préférable d’utiliser la version 64 bits, si possible.

> [!IMPORTANT]
> Avec SSMA v7.4 et versions ultérieures, .net 4.5.2 est un préalable de l’installation.

## <a name="ssma-v76"></a>SSMA v7.6
La version v7.6 de SSMA pour SAP ASE contient les modifications suivantes :
- SSMA pour SAP ASE a été amélioré avec des correctifs ciblés visant qui améliorent la qualité et conversion des mesures et prise en charge de SQL Server 2017 (version préliminaire publique). Prise en charge de SQL Server 2017 sur Windows et Linux en version préliminaire publique et ne doit pas être utilisé pour les migrations de production.
- SSMA pour SAP ASE a été mis à jour pour prendre en charge pour la conversion des fonctions de Sybase.

> [!IMPORTANT]
> Avec SSMA v7.4 et versions ultérieures, .net 4.5.2 est un préalable de l’installation et la version 32 bits de l’outil a été abandonnée.

## <a name="ssma-v75"></a>SSMA v7.5
La version v7.5 de SSMA pour SAP ASE contient les modifications suivantes :
-   Amélioré avec plusieurs améliorations pour garantir une meilleure accessibilité des personnes handicapées.
-   Mise à jour pour prendre en charge pour créer ou remplacer la syntaxe.

> [!IMPORTANT]
> .NET 4.5.2 est requis pour l’installation de SSMA v7.5. En outre, à compter de v7.4, la version 32 bits de SSMA est en cours de retrait.  

## <a name="ssma-v74"></a>SSMA v7.4
La version v7.4 de SSMA pour Sybase contient les modifications suivantes :
- Le **Query timeout** option est désormais disponible au cours de la découverte d’objets de schéma à la source et cible.
![option de délai d’attente de requête](../media/query-timeout_red.png)
- Les mesures de qualité et la conversion a été améliorée avec des correctifs ciblés, en fonction des commentaires des clients.

> [!IMPORTANT]
> .NET 4.5.2 est requis pour l’installation de SSMA v7.4. En outre, à compter de v7.4, la version 32 bits de SSMA est en cours de retrait.  

## <a name="ssma-v73"></a>SSMA v7.3
La version v7.3 de SSMA pour Sybase contient les modifications suivantes :
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
La version v7.2 de SSMA pour Sybase contient les modifications suivantes :
- Métrique de qualité et de conversion améliorée avec des correctifs ciblés en fonction des commentaires des clients.
- Améliorations de télémétrie pour fournir une meilleure points de données pour résoudre les problèmes des clients et d’améliorer le taux de conversion de SSMA.

## <a name="ssma-v71"></a>SSMA v7.1
La version v7.1 de SSMA pour Access contient les modifications suivantes :
- SQL Server 2017 sur Windows et Linux CTP1 est désormais une plateforme cible prise en charge pour la migration. Cette fonctionnalité est dans technical preview et prend en charge le déplacement de schéma et les données aux serveurs de SQL Server cible.
- SSMA prend désormais en charge les mises à jour automatiques pour télécharger la dernière version de SSMA dès qu’il est disponible.
- Fichiers binaires installables SSMA sont maintenant fournies via fichiers de package Windows installer (.msi).

**Ressources**

[Extension des fonctionnalités de SQL Server Migration Assistant conversion](https://blogs.msdn.microsoft.com/datamigration/2017/02/21/2185/)

[Évaluer et migrer des données à partir des plateformes de données non Microsoft pour SQL Server *(avec l’exemple d’Oracle)*](https://blogs.msdn.microsoft.com/datamigration/2016/11/16/sql-server-migration-assistant-how-to-assess-and-migrate-databases-from-non-microsoft-data-platforms-to-sql-server/) 

## <a name="may-2016"></a>Mai 2016  
La version de mai 2016 de SSMA pour Sybase contient les modifications suivantes :  

-  Prise en charge pour SQL Server 2016.
-  Supprimé la vérification du programme d’installation pour .net 2.0.
-  Dépendance Extension Pack mis à jour à partir de .net 3.5 vers .net 4.0.
-  Fixe « enregistrer le projet » et « ouvrir le projet » des commandes pour la Console SSMA.
-  Commande fixe « securepassword » pour la Console SSMA.
-  Correction de comptage des objets pour le chargement initial.
-  Résolution de bogue dans les paramètres globaux.

## <a name="march-2016"></a>Mars 2016  
La version préliminaire de mars 2016 de SSMA pour Sybase contient les modifications suivantes :  
  
-  Prise en charge pour la migration vers SQL Server 2016.  
  
## <a name="january-2016"></a>Janvier 2016  
La version de maintenance de janvier 2016 de SSMA pour Sybase contient les modifications suivantes :  
  
-  Élément de Menu ajouté vue journal pour SSMA (RFC 5706203).  
-  Ajout de télémétrie. 
  
## <a name="july-2014"></a>Juillet 2014  
La version de juillet 2014 de SSMA pour Sybase contient les modifications suivantes :  
  
-  Conversion de code de base de données SQL Azure améliorée.  
-  Déplacer la fonctionnalité du pack d’extension au schéma pour prendre en charge de la base de données SQL Azure.  
-  Améliorations de performances ajoutés testé pour les bases de données avec plus de 10k objets.  
-  Améliorations de l’interface utilisateur ajoutées pour traiter avec un grand nombre d’objets.  
-  Ajouté la possibilité de mettre en surbrillance les schémas LOB « connues » (afin qu’ils peuvent être ignorés dans la conversion).  
-  Ajouté des améliorations de la vitesse de conversion.  
-  Ajouté la possibilité d’afficher le nombre d’objets dans l’interface utilisateur. 
-  Taille de rapport réduit de plus de 25 %.  
-  Messages d’erreur améliorés pour les constructions non analysées.  
  
## <a name="april-2014"></a>Avril 2014  
La version d’avril 2014 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Prise en charge ajoutée de MS SQL Server 2014.  
-   Bogues résolus concernant la conversion vers Azure.  
-   Bogues résolus concernant les pages de rapport invisible dans Internet Explorer 10.  
  
## <a name="january-2012"></a>Janvier 2012  
La version de janvier 2012 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Prise en charge pour la conversion de déclencheur de restauration.  
-   Fourni un correctif pour la conversion@ROWCOUNT et @@ERROR dans la même instruction SET.  
  
## <a name="july-2011"></a>Juillet 2011  
La version de juillet 2011 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Amélioration signalement d’erreurs pendant la migration des données.  
  
## <a name="april-2011"></a>Avril 2011  
La version d’avril 2011 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Produit consolidé « De SSMA pour Sybase », qui prend en charge [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] « Denali » et SQL Azure.  
-   Prise en charge pour la connexion et la migration vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] « Denali ».  
-   Ajouté une nouvelle fonctionnalité pour convertir et migrer des bases de données Sybase vers SQL Azure.  
-   Moteur de migration améliorée des données côté client, prise en charge de la migration parallèle des données.  
-   Performances de migration de données améliorées avec Simple et en bloc connecté les modes de récupération.  
-   Ajouté la possibilité de convertir correctement et de migrer des bases de données Sybase respect de la casse à la casse de SQL Server.  
-   Prise en charge pour la conversion des instructions de jointure Non ANSI Sybase ASE aux instructions de jointure ANSI du serveur SQL a été étendue pour les instructions DELETE et UPDATE.  
-   Fourni des options de connectivité supplémentaire pour se connecter aux serveurs Sybase ASE à l’aide du fournisseur Sybase ASE ODBC et les fournisseurs de Sybase ASE ADO.Net.  
-   Supprimé la dépendance sur une base de données distinct appelé **SysDB**, qui contient les fonctions d’émulation Sybase (installées en tant que partie du Pack d’Extension).  
-   Ajouté la possibilité d’installer SSMA pour Sybase le Pack d’Extension sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] clusters.  
-   Ajouté la compatibilité descendante des projets créés par les versions antérieures de SSMA (version 4.0 et v4.2).  
-   Ajouté la possibilité d’installer SSMA pour Sybase v5.0 produit côte-à-côte (à côte SxS) avec les versions antérieures de SSMA (version 4.0 et v4.2).  
  
## <a name="july-2010"></a>Juillet 2010  
La version de juillet 2010 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Prise en charge pour la migration vers SQL Server 2008 R2.  
-   Ajouter une nouvelle application de Console SSMA pour l’exécution de ligne de commande.  
-   Prise en charge la Migration des données à l’aide côté serveur et côté Client des moteurs de Migration de données.  
-   Prise en charge ajoutée pour l’instruction de « SELECT personnalisé » dans la migration des données.  
-   Prise en charge pour la migration à partir de Sybase ASE 15.0.3 et 15.5.  
  
## <a name="june-2008"></a>Juin 2008  
La version de juin 2008 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Ajout SSMA testeur, qui teste automatiquement la conversion des objets de base de données et la migration des données effectuées par SSMA. Une fois que toutes les étapes de migration de SSMA sont terminées, utilisez SSMA testeur pour vérifier que les objets convertis fonctionnent de manière identique et que toutes les données a été correctement transféré.  
-   Conversion de versions antérieures à SQL ajoutée. Utilisateur peut maintenant spécifier une table temporaire (et un autre objet) déclarations pour chaque procédure de la source à utiliser dans la conversion.  
-   Ajout d’améliorations dans la conversion de l’objet :  
    -   Joint conversion révisée.  
    -   Agrégats et des non-agrégats sans avaient/groupe par clauses.  
    -   La fonction IDENTITY avec une instruction SELECT INTO.  
    -   Contraintes en cluster et les index sur les données uniquement verrouillées.  
    -   Tables temporaires créées par SELECT INTO.  
    -   Contraintes / index pour les tables temporaires.  
    -   Nouvelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 des types de date/heure sont pris en charge.  
    -   Sybase 15.0 connectivité et les types de données prise en charge.  
  
## <a name="may-2007"></a>Mai 2007  
La version de mai 2007 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Ajouté la possibilité de charger le contenu de la base de données plus rapide lors de l’enregistrement d’un projet.  
-   Prise en charge pour les commentaires d’entré par l’utilisateur dans SQL Server mise en forme en mode SQL.  
-   Ajout d’améliorations dans la conversion de l’objet.  
  
Le fichier d’aide n’a pas été mis à jour pour cette version. Pour plus d’informations, consultez la section Notes concernant la Documentation plus loin dans cet article.  
  
## <a name="november-2006"></a>Novembre 2006  
La version de novembre 2006 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Ajouté de nouveaux paramètres globaux :  
    -   Vous pouvez choisir d’afficher les numéros de ligne dans les fenêtres de l’éditeur.  
    -   Vous pouvez configurer SSMA pour demander à remplacer les objets en double, ou toujours ou jamais remplacer des objets en double lors de la conversion de schéma.  
-   Ajout d’une nouvelle option de conversion qui vous permet de configurer comment SSMA gère les situations suivantes :  
    -   Une instruction CAST ou CONVERT qui contient une chaîne binaire.  
    -   Vérifie les valeurs null dans des expressions d’égalité.  
    -   Tables de proxy.  
    -   Utilisateur message numéros d’erreur de RAISERROR.  
    -   Instructions de mise à jour qui contiennent des identificateurs non résolues.  
-   Ajouté une nouvelle option de migration qui vous permet de spécifier comment SSMA doit gérer les dates qui sont en dehors de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] plage de dates.  
-   Ajouté une **SQL au format** définition sur le **SQL** onglet, qui met en forme le code pour une meilleure lisibilité.  
-   Correctifs de bogues, notamment :  
    -   SSMA convertit maintenant le verrou de TABLE *table* IN {partagé | Instructions de MODE exclusif} en ajoutant un indicateur TABLOCK ou TABLOCKX à la requête SELECT suivante sur la table.  
    -   Les conversions nécessaires sont maintenant ajoutées quand des types binaires sont utilisés dans les expressions de caractères.  
    -   Améliorations des performances et de mémoire.  
  
## <a name="july-2006"></a>Juillet 2006  
La version de juillet 2006 de SSMA pour Sybase était la version initiale.  
  
## <a name="see-also"></a>Voir aussi  
[Bien démarrer avec SSMA pour Sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)
