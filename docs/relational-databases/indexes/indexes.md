---
title: Index | Microsoft Docs
ms.custom: 
ms.date: 11/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-indexes
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- index types [SQL Server]
ms.assetid: 00863b10-e77c-44c5-8ac2-bb4ac454eec6
caps.latest.revision: 45
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2f4ac3c815fec2e6add64257dd2ae12e7b659f84
ms.lasthandoff: 04/11/2017

---
# <a name="indexes"></a>Index
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  La table suivante répertorie les types d'index disponibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et propose des liens correspondants pour plus d'informations.  
  
|Type d'index|Description|Autres informations|  
|----------------|-----------------|----------------------------|  
|Hachage|Avec un index de hachage, les données sont accédées via une table de hachage en mémoire. Les index de hachage consomment une quantité fixe de mémoire, en fonction du nombre de compartiments.|[Instructions pour utiliser les index sur les tables optimisées en mémoire](http://msdn.microsoft.com/library/16ef63a4-367a-46ac-917d-9eebc81ab29b)|  
|index non cluster optimisés en mémoire|Pour les index non cluster optimisés en mémoire, la consommation de mémoire est une fonction du nombre de lignes et de la taille des colonnes de clés d'index|[Instructions pour utiliser les index sur les tables optimisées en mémoire](http://msdn.microsoft.com/library/16ef63a4-367a-46ac-917d-9eebc81ab29b)|  
|Cluster|Un index cluster trie et stocke les lignes de données de la table ou de la vue en fonction de la clé d'index cluster. L'index cluster est mis en œuvre sous la forme d'une structure d'index arborescente binaire permettant la récupération rapide des lignes d'après leurs valeurs clés de l'index cluster.|[Description des index cluster et non-cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)<br /><br /> [Créer des index cluster](../../relational-databases/indexes/create-clustered-indexes.md)|  
|Non-cluster|Les index non cluster peuvent être définis dans une table ou dans une vue dotée d'un index cluster ou d'un segment de mémoire. Chaque ligne d'un index non cluster contient la valeur clé non cluster ainsi qu'un localisateur de ligne. Le localisateur pointe vers la ligne de données dans l'index cluster ou dans le segment doté de la valeur clé. Les lignes de l'index sont stockées selon l'ordre des valeurs clés de l'index. L'ordre spécifique des lignes de données n'est garanti que si un index cluster est créé sur la table.|[Description des index cluster et non-cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)<br /><br /> [Créez des index non-cluster](../../relational-databases/indexes/create-nonclustered-indexes.md)|  
|Unique|Un index unique garantit que la clé de l'index ne contient pas de valeur dupliquée et que toute ligne de la table ou de la vue est en quelque sorte unique.<br /><br /> L'unicité peut être une propriété à la fois des index cluster et non cluster.|[Créer des index uniques](../../relational-databases/indexes/create-unique-indexes.md)|  
|columnstore|Un index columnstore en mémoire stocke et gère des données à l'aide du stockage des données en colonnes et du traitement des requêtes en colonnes.<br /><br /> Les index columnstore fonctionnent bien pour les charges de travail de stockage de données qui effectuent principalement des chargements en masse et des requêtes en lecture seule. Utilisez l’index columnstore pour atteindre des **performances des requêtes** pouvant être multipliées par 10 par rapport au stockage orienté lignes traditionnel, et une **compression de données** multipliée par 7 par rapport à la taille des données non compressées.|[Guide des index columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md)<br /><br /> [Utilisation d’index columnstore non cluster](https://msdn.microsoft.com/library/dn589806.aspx)|  
|Index à colonnes incluses|Index non cluster qui est étendu pour inclure des colonnes non clés en plus des colonnes clés.|[Créer des index avec colonnes incluses](../../relational-databases/indexes/create-indexes-with-included-columns.md)|  
|Index sur les colonnes calculées|Index sur une colonne dérivée de la valeur d'une ou de plusieurs autres colonnes, ou certaines entrées déterministes.|[Index sur les colonnes calculées](../../relational-databases/indexes/indexes-on-computed-columns.md)|  
|Filtré|Index non cluster optimisé, convenant tout particulièrement aux requêtes qui effectuent des sélections dans un sous-ensemble précis de données. Il utilise un prédicat de filtre pour indexer une partie des lignes de la table. Un index filtré bien conçu peut améliorer les performances des requêtes, réduire les coûts de maintenance des index et réduire les coûts de stockage des index par rapport aux index de table entière.|[Créer des index filtrés](../../relational-databases/indexes/create-filtered-indexes.md)|  
|Spatial|Un index spatial permet d’effectuer plus efficacement certaines opérations sur des objets spatiaux (*données spatiales*) dans une colonne du type de données **géométrie** . L'index spatial réduit le nombre d'objets sur lesquels des opérations spatiales relativement coûteuses doivent être appliquées.|[Vue d'ensemble des index spatiaux](../../relational-databases/spatial/spatial-indexes-overview.md)|  
|XML|Représentation fragmentée et permanente des objets binaires XML de taille importante (BLOB) dans la colonne de type de données **xml**.|[Index XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)|  
|Texte intégral|Type spécial d'index fonctionnel par jeton qui est construit et géré par le Moteur d'indexation et de recherche en texte intégral Microsoft pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il permet de prendre en charge efficacement toute recherche de mot sophistiqué dans des chaînes de données caractères.|[Alimenter des index de recherche en texte intégral](../../relational-databases/search/populate-full-text-indexes.md)|  
  
## <a name="related-tasks"></a>Tâches associées  
  
## <a name="related-content"></a>Contenu connexe  
 [Option SORT_IN_TEMPDB pour les index](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)  
  
 [Désactiver les index et contraintes](../../relational-databases/indexes/disable-indexes-and-constraints.md)  
  
 [Activer les index et contraintes](../../relational-databases/indexes/enable-indexes-and-constraints.md)  
  
 [Renommer des index](../../relational-databases/indexes/rename-indexes.md)  
  
 [Définir les options d’index](../../relational-databases/indexes/set-index-options.md)  
  
 [Disk Space Requirements for Index DDL Operations](../../relational-databases/indexes/disk-space-requirements-for-index-ddl-operations.md)  
  
 [Réorganiser et reconstruire des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  
 [Spécifier un facteur de remplissage pour un index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)  

[Guide d’architecture des pages et des étendues](../../relational-databases/pages-and-extents-architecture-guide.md)
  
## <a name="see-also"></a>Voir aussi  
 [Description des index cluster et non-cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)  
  
  

