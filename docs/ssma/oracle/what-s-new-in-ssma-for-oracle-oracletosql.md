---
title: Quel &#39; s de SSMA pour Oracle (OracleToSQL) | Documents Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f305ebb6-7393-4a43-abb3-6332b739d690
caps.latest.revision: 24
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 191fe2e11c43f4c190a87ee52df9ff87c259ea7d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="what39s-new-in-ssma--for-oracle-oracletosql"></a>Quel &#39; s de SSMA pour Oracle (OracleToSQL)
Cette rubrique répertorie SSMA pour les modifications d’Oracle dans chaque version.  

## <a name="may-2016"></a>Mai 2016  
La version de mai 2016 de SSMA pour Oracle contient les modifications suivantes :  

1.  Prise en charge pour SQL Server 2016
2.  Ajout de conversion de tables d’archive restauration Oracle aux tables temporelles de SQL Server
3.  Ajout de conversion de la stratégie de VPD Oracle convertir des objets de stratégie de SQL Server (sécurité de niveau ligne pour Oracle)
4.  Réduction du temps de chargement initial pour Oracle
5.  Programme de résolution et de l’analyseur améliorée
6.  Supprimer la vérification du programme d’installation pour .net 2.0
7.  Dépendance Extension Pack mis à jour à partir de .net 3.5 pour .net 4.0
8.  Fixe « enregistrer le projet » et « ouvrir le projet » des commandes pour la Console de SSMA
9.  Commande securepassword « fixe » pour la Console de SSMA
10. Fixe le comptage des objets pour le chargement initial
11. Fixe la conversion des types de données pour Oracle
12. Résolution du bogue dans les paramètres globaux
  
## <a name="march-2016"></a>Mars 2016  
La version préliminaire de mars 2016 de SSMA pour Oracle contient les modifications suivantes :  
  
1.  Prend en charge la migration vers SQL Server 2016  
  
2.  Prise en charge pour la migration sécurité au niveau des lignes Oracle (avec certaines limitations)  
  
3.  Prend en charge pour la migration des tables Oracle dans la mémoire à la banque des colonnes SQL Server  
  
## <a name="january-2016"></a>Janvier 2016  
Le janvier 2014 mise à jour de SSMA pour Oracle contient les modifications suivantes :  
  
1.  Prise en charge pour les index cluster  
  
2.  Les requêtes de schéma Oracle lentes (RFC 5076207)  
  
3.  Fixe se connecter à Azure à partir de la console  
  
4.  Élément de Menu journal View ajouté SSMA (RFC 5706203)  
  
5.  Ajout de télémétrie  
  
## <a name="july-2014"></a>Juillet 2014  
La version de juillet 2014 de SSMA pour Oracle contient les modifications suivantes :  
  
1.  Prise en charge de la base de données SQL Azure  
  
2.  Fonctionnalités du Pack d’extension est déplacé vers le schéma pour prendre en charge de la base de données SQL Azure  
  
3.  Prise en charge des vues matérialisées d’Oracle  
  
4.  Les tables optimisées en la prise en charge de la mémoire de SQL Server 2014  
  
5.  Améliorations des performances testées pour les bases de données avec plus de 10k objets  
  
6.  Améliorations de l’interface utilisateur pour le traitement d’un grand nombre d’objets  
  
7.  Mise en surbrillance des schémas « connues » de LOB  
  
8.  Améliorations de la vitesse de conversion  
  
9. Afficher les nombres de l’objet dans l’interface utilisateur  
  
10. Réduction de plus de 25 % de la taille de rapport  
  
11. Messages d’erreur améliorés pour les constructions non analysées.  
  
## <a name="april-2014"></a>Avril 2014  
La version d’avril 2014 de SSMA pour Oracle contient les modifications suivantes :  
  
1.  Prise en charge de Microsoft SQL Server 2014.  
  
2.  Prise en charge supplémentaire d’optimisation Oracle 12 et la requête.  
  
3.  Bogues résolus concernant la conversion vers Azure.  
  
4.  Bogues résolus en ce qui concerne les pages du rapport invisible dans Internet Explorer 10.  
  
## <a name="january-2012"></a>Janvier 2012  
La version de janvier 2012 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge RowType et RecordType des paramètres d’entrée NULL comme valeur par défaut.  
  
## <a name="july-2011"></a>Juillet 2011  
La version de juillet 2011 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge pour la conversion de séquence Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Générateur de séquence « Denali ».  
  
-   Amélioration signalement d’erreurs pendant la migration des données.  
  
-   Conversion amélioré d’instruction à l’aide des mots réservés.  
  
-   Amélioration de la conversion implicite de la valeur de date dans une fonction.  
  
## <a name="april-2011"></a>Avril 2011  
La version d’avril 2011 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Produit consolidé « SSMA pour Oracle », qui prend en charge [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008 et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] « Denali ».  
  
-   Prise en charge pour la connexion et la migration vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] « Denali ».  
  
-   Amélioré le moteur de migration de données côté client, prise en charge parallèle migration des données.  
  
-   Performances de migration de données améliorées avec Simple et en bloc connecté des modes de récupération.  
  
-   Compatibilité descendante des projets créés dans les versions antérieures de SSMA (version 4.0 et v4.2).  
  
-   SSMA pour Oracle v5.0 produit peut être installé côte à côte (SxS) avec les versions antérieures de SSMA (version 4.0 et v4.2).  
  
-   Prise en charge des Types de définis par l’utilisateur (y compris sous-type, VARRAY, la TABLE imbriquée, table des objets et affichage d’objets) et leur utilisation dans les blocs de PL/SQL avec des messages d’erreur spéciale de création de rapports.  
  
## <a name="july-2010"></a>Juillet 2010  
La version de juillet 2010 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Prise en charge pour la migration vers SQL Server 2008 R2  
  
-   Nouvelle application de Console de SSMA pour l’exécution de la ligne de commande  
  
-   Prise en charge la Migration des données à l’aide de côté serveur et les moteurs de Migration de données côté Client  
  
-   Prise en charge de l’instruction de « SELECT personnalisée » dans la migration des données  
  
-   Prise en charge pour la migration à partir d’Oracle 11g R2  
  
## <a name="june-2008"></a>Juin 2008  
La version de juin 2008 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Améliorations dans le rapport d’évaluation ont été effectuées. Il inclut des informations supplémentaires pour les synonymes, de source brute d’objets à analyser, panneaux et la suppression de logo de SQL Server et persistance de disposition.  
  
-   Améliorations de la conversion de l’objet :  
  
    -   Packages DBMS_LOB, conversion DBMS_SQL ajouté.  
  
    -   Joint la conversion révisée.  
  
    -   Modification des enregistrements et des collections de conversion, maintenant la conversion d’enregistrements dans les cas simples libérés via des variables distinctes pour chaque champ.  
  
    -   Améliorations de mise en oeuvre des enregistrements et des regroupements.  
  
    -   Fonctions d’agrégation de fenêtrage ajoutées.  
  
    -   Clause ROLLUP/CUBE ajoutée.  
  
    -   Amélioration de NEXTVAL/CURVAL.  
  
    -   Colonnes de regroupement dans la clause SET, les jeux de regroupement et l’ID de regroupement ont été ajoutés.  
  
    -   Ajouté des instructions de fusion.  
  
    -   Prise en charge de nouveaux types date/heure et la conversion des enregistrements et des collections en tant que types de données CLR ajoutés.  
  
-   Nouvelles fonctionnalités de testeur ont été ajoutées. Tables peuvent maintenant être testées en tant qu’objets à l’aide de Tester un ordre d’appel de plusieurs objets testables dans les cas de test peut être modifié, utilisateur peut tester les procédures et fonctions des enregistrements et des collections en tant que paramètres et retourner des valeurs et un analyseur a été ajouté pour vérifier les dépendances seulement les tables utilisées.  
  
## <a name="august-2007"></a>Août 2007  
La version d’août 2007 de SSMA pour Oracle contient les modifications suivantes :  
  
-   Un nouveau composant testeur vous permet de créer, gérer et exécuter des cas de test pour vérifier le code SQL converti.  
  
-   Conversion de sous-types Oracle, les collections et les modules locaux ont été ajoutés au convertisseur de SQL.  
  
-   Une nouvelle fonctionnalité de synchronisation vous permet de synchroniser des objets spécifiques à la base de données SQL Server.  
  
-   Nouvelles options de conversion ajoutées.  
  
## <a name="april-2007"></a>Avril 2007  
La version d’avril 2007 de SSMA pour Oracle était la version initiale.  
  

