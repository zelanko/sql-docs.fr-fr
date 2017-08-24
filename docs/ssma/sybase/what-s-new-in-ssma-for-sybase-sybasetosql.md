---
title: Quel &#39; s de SSMA pour Sybase (SybaseToSQL) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 2be0cf8d-6dbe-443a-abbd-036249922205
caps.latest.revision: 21
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9d97e03212e6985ce9d506774bfff0aa2f4ec8d1
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="what39s-new-in-ssma--for-sybase-sybasetosql"></a>Quel &#39; s de SSMA pour Sybase (SybaseToSQL)
Cette rubrique répertorie SSMA pour Sybase les modifications dans chaque version.  

## <a name="may-2016"></a>Mai 2016  
La version de mai 2016 de SSMA pour Sybase contient les modifications suivantes :  

1.  Prise en charge pour SQL Server 2016
2.  Supprimer la vérification du programme d’installation pour .net 2.0
3.  Dépendance Extension Pack mis à jour à partir de .net 3.5 pour .net 4.0
4.  Fixe « enregistrer le projet » et « ouvrir le projet » des commandes pour la Console de SSMA
5.  Commande securepassword « fixe » pour la Console de SSMA
6.  Fixe le comptage des objets pour le chargement initial
7.  Résolution du bogue dans les paramètres globaux

## <a name="march-2016"></a>Mars 2016  
La version préliminaire de mars 2016 de SSMA pour Sybase contient les modifications suivantes :  
  
1.  Prend en charge la migration vers SQL Server 2016  
  
## <a name="january-2016"></a>Janvier 2016  
La version de maintenance de janvier 2016 de SSMA pour Sybase contient les modifications suivantes :  
  
1.  Élément de Menu journal View ajouté SSMA (RFC 5706203)  
  
2.  Ajout de télémétrie  
  
## <a name="july-2014"></a>Juillet 2014  
La version de juillet 2014 de SSMA pour Sybase contient les modifications suivantes :  
  
1.  Conversion de code de base de données SQL Azure amélioré  
  
2.  Fonctionnalités du Pack d’extension est déplacé vers le schéma pour prendre en charge de la base de données SQL Azure  
  
3.  Améliorations des performances testées pour les bases de données avec plus de 10k objets  
  
4.  Améliorations de l’interface utilisateur pour le traitement d’un grand nombre d’objets  
  
5.  Mise en surbrillance des schémas LOB « connues » (afin qu’ils peuvent être ignorés lors de la conversion)  
  
6.  Améliorations de la vitesse de conversion  
  
7.  Afficher les nombres de l’objet dans l’interface utilisateur  
  
8.  Réduction de plus de 25 % de la taille de rapport  
  
9. Messages d’erreur améliorés pour les constructions non analysées.  
  
## <a name="april-2014"></a>Avril 2014  
La version d’avril 2014 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Prise en charge de Microsoft SQL Server 2014.  
  
-   Bogues résolus concernant la conversion vers Azure  
  
-   Bogues résolus en ce qui concerne les pages du rapport invisible dans Internet Explorer 10.  
  
## <a name="january-2012"></a>Janvier 2012  
La version de janvier 2012 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Prise en charge pour la conversion de déclencheur de restauration.  
  
-   Fourni un correctif pour la conversion@ROWCOUNT et @@ERROR dans la même instruction SET.  
  
## <a name="july-2011"></a>Juillet 2011  
La version de juillet 2011 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Amélioration signalement d’erreurs pendant la migration des données.  
  
## <a name="april-2011"></a>Avril 2011  
La version d’avril 2011 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Produit consolidé « De SSMA pour Sybase », qui prend en charge [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] « Denali » et SQL Azure.  
  
-   Prise en charge pour la connexion et la migration vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] « Denali ».  
  
-   Nouvelle fonction pour convertir et migrer des bases de données Sybase vers SQL Azure.  
  
-   Amélioré le moteur de migration de données côté client, prise en charge parallèle migration des données.  
  
-   Performances de migration de données améliorées avec Simple et en bloc connecté des modes de récupération.  
  
-   Des bases de données Sybase peuvent être converties correctement et migrés vers respecte la casse de SQL Server.  
  
-   Prise en charge pour la conversion des instructions de jointure Non ANSI Sybase ASE aux instructions de jointure ANSI du serveur SQL a été étendue pour les instructions DELETE et UPDATE.  
  
-   Options de connectivité supplémentaire pour se connecter aux serveurs de Sybase ASE à l’aide du fournisseur de Sybase ASE ODBC et les fournisseurs de Sybase ASE ADO.Net.  
  
-   La suppression de la dépendance sur une base de données distinct appelé **SysDB** qui contient les fonctions d’émulation de Sybase (installées en tant que partie du Pack d’Extension).  
  
-   SSMA pour Sybase Extension Pack peut désormais être installée sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] clusters.  
  
-   Compatibilité descendante des projets créés dans les versions antérieures de SSMA (version 4.0 et v4.2).  
  
-   SSMA pour Sybase v5.0 produit peut être installé côte à côte (SxS) avec les versions antérieures de SSMA (version 4.0 et v4.2).  
  
## <a name="july-2010"></a>Juillet 2010  
La version de juillet 2010 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Prise en charge pour la migration vers SQL Server 2008 R2  
  
-   Nouvelle application de Console de SSMA pour l’exécution de la ligne de commande  
  
-   Prise en charge la Migration des données à l’aide de côté serveur et les moteurs de Migration de données côté Client  
  
-   Prise en charge de l’instruction de « SELECT personnalisée » dans la migration des données  
  
-   Prise en charge pour la migration à partir de Sybase ASE 15.0.3 et 15.5  
  
## <a name="june-2008"></a>Juin 2008  
La version de juin 2008 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Testeur de SSMA est ajouté, il teste automatiquement la conversion des objets de base de données et la migration des données effectuées par SSMA. Une fois que toutes les étapes de migration de SSMA sont terminées, utilisez SSMA testeur pour vérifier que les objets convertis fonctionnent de manière identique et que toutes les données a été transféré correctement.  
  
-   Conversion de versions antérieures à SQL ajoutée. Utilisateur peut désormais spécifier des tables temporaires (et autres objets) déclarations pour chaque procédure source à utiliser lors de la conversion.  
  
-   Améliorations de la conversion de l’objet :  
  
    -   Joint la conversion révisée.  
  
    -   Agrégats et des non-agrégats sans avaient/groupe par clauses.  
  
    -   La fonction IDENTITY avec une instruction SELECT INTO.  
  
    -   Contraintes en cluster et des index sur les données uniquement verrouillé.  
  
    -   Tables temporaires créées par SELECT INTO.  
  
    -   Contraintes / d’index pour les tables temporaires.  
  
    -   Nouvelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 datetime pris en charge.  
  
    -   Sybase 15.0 connectivité et des types de données prise en charge.  
  
## <a name="may-2007"></a>Mai 2007  
La version de mai 2007 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Lorsque vous enregistrez un projet, du chargement du contenu de la base de données est plus rapide.  
  
-   Prise en charge pour les commentaires entré par l’utilisateur que SQL Server au format mode SQL.  
  
-   Améliorations de la conversion de l’objet.  
  
Notez que le fichier d’aide n’a pas mis à jour pour cette version. Pour plus d’informations, consultez la section Notes de la Documentation plus loin dans cette rubrique.  
  
## <a name="november-2006"></a>Novembre 2006  
La version de novembre 2006 de SSMA pour Sybase contient les modifications suivantes :  
  
-   Nouveaux paramètres globaux :  
  
    -   Vous pouvez choisir d’afficher les numéros de ligne dans les fenêtres de l’éditeur.  
  
    -   Vous pouvez configurer SSMA pour inviter à remplacer les objets en double ou jamais, ou toujours remplacer les objets en double lors de la conversion de schéma.  
  
-   Nouvelles options de conversion vous permettent de configurer la façon dont SSMA gère les situations suivantes :  
  
    -   Une instruction CAST ou CONVERT qui contient une chaîne binaire  
  
    -   Vérifications de valeurs null dans des expressions d’égalité  
  
    -   Tables de proxy  
  
    -   Numéros d’erreur de message utilisateur pour RAISERROR  
  
    -   Instructions de mise à jour qui contiennent des identificateurs non résolues  
  
-   Une nouvelle option de migration vous permet de spécifier comment SSMA doit gérer les dates qui sont en dehors de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] plage de dates.  
  
-   A **SQL de mise en forme** définition sur le **SQL** onglet, qui met en forme le code pour une meilleure lisibilité.  
  
-   Correctifs de bogues qui incluent les éléments suivants :  
  
    -   SSMA convertit maintenant le verrou de TABLE *table* IN {SHARED | Instructions en MODE exclusif} en ajoutant un indicateur TABLOCK ou TABLOCKX à la requête SELECT suivante sur la table.  
  
    -   Les conversions nécessaires sont maintenant ajoutées quand des types binaires sont utilisés dans les expressions de caractères.  
  
    -   Améliorations des performances et de mémoire.  
  
## <a name="july-2006"></a>Juillet 2006  
La version de juillet 2006 de SSMA pour Sybase était la version initiale.  
  
## <a name="see-also"></a>Voir aussi  
[Prise en main de SSMA pour Sybase &#40; SybaseToSQL &#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  

