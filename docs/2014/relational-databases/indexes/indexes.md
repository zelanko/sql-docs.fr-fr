---
title: Index | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index types [SQL Server]
ms.assetid: 00863b10-e77c-44c5-8ac2-bb4ac454eec6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 58d4d71189598a6fd101e6db0a40b8c8b0a3b903
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63161853"
---
# <a name="indexes"></a>Index
  La table suivante répertorie les types d'index disponibles dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et propose des liens correspondants pour plus d'informations.  
  
|Type d’index|Description|Informations supplémentaires|  
|----------------|-----------------|----------------------------|  
|Hachage|Avec un index de hachage, les données sont accédées via une table de hachage en mémoire. Les index de hachage consomment une quantité fixe de mémoire, en fonction du nombre de compartiments.|[Instructions pour utiliser les index sur les tables optimisées en mémoire](../in-memory-oltp/memory-optimized-tables.md)|  
|index non cluster optimisés en mémoire|Pour les index non cluster optimisés en mémoire, la consommation de mémoire est une fonction du nombre de lignes et de la taille des colonnes de clés d'index|[Instructions pour utiliser les index sur les tables optimisées en mémoire](../in-memory-oltp/memory-optimized-tables.md)|  
|Cluster|Un index cluster trie et stocke les lignes de données de la table ou de la vue en fonction de la clé d'index cluster. L'index cluster est mis en œuvre sous la forme d'une structure d'index arborescente binaire permettant la récupération rapide des lignes d'après leurs valeurs clés de l'index cluster.|[Description des index cluster et non cluster](clustered-and-nonclustered-indexes-described.md)<br /><br /> [Créer des index cluster](create-clustered-indexes.md)|  
|Non-cluster|Les index non cluster peuvent être définis dans une table ou dans une vue dotée d'un index cluster ou d'un segment de mémoire. Chaque ligne d'un index non cluster contient la valeur clé non cluster ainsi qu'un localisateur de ligne. Le localisateur pointe vers la ligne de données dans l'index cluster ou dans le segment doté de la valeur clé. Les lignes de l'index sont stockées selon l'ordre des valeurs clés de l'index. L'ordre spécifique des lignes de données n'est garanti que si un index cluster est créé sur la table.|[Description des index cluster et non cluster](clustered-and-nonclustered-indexes-described.md)<br /><br /> [Créer des index non cluster](create-nonclustered-indexes.md)|  
|Unique|Un index unique garantit que la clé de l'index ne contient pas de valeur dupliquée et que toute ligne de la table ou de la vue est en quelque sorte unique.<br /><br /> L'unicité peut être une propriété à la fois des index cluster et non cluster.|[Créer des index uniques](create-unique-indexes.md)|  
|columnstore|Un index columnstore en mémoire stocke et gère des données à l'aide du stockage des données en colonnes et du traitement des requêtes en colonnes.<br /><br /> Les index columnstore fonctionnent bien pour les charges de travail de stockage de données qui effectuent principalement des chargements en masse et des requêtes en lecture seule. Utilisez l’index columnstore pour atteindre des **performances des requêtes** pouvant être multipliées par 10 par rapport au stockage orienté lignes traditionnel, et une **compression de données** multipliée par 7 par rapport à la taille des données non compressées.|[Columnstore Indexes Described](columnstore-indexes-described.md)<br /><br /> [Utilisation d’index ColumnStore non cluster](../../database-engine/using-nonclustered-columnstore-indexes.md)<br /><br /> [Utilisation d'index columnstore cluster](../../database-engine/using-clustered-columnstore-indexes.md)|  
|Index à colonnes incluses|Index non cluster qui est étendu pour inclure des colonnes non clés en plus des colonnes clés.|[Créer des index avec colonnes incluses](create-indexes-with-included-columns.md)|  
|Index sur les colonnes calculées|Index sur une colonne dérivée de la valeur d'une ou de plusieurs autres colonnes, ou certaines entrées déterministes.|[Index sur les colonnes calculées](indexes-on-computed-columns.md)|  
|Filtré|Index non cluster optimisé, convenant tout particulièrement aux requêtes qui effectuent des sélections dans un sous-ensemble précis de données. Il utilise un prédicat de filtre pour indexer une partie des lignes de la table. Un index filtré bien conçu peut améliorer les performances des requêtes, réduire les coûts de maintenance des index et réduire les coûts de stockage des index par rapport aux index de table entière.|[Créer des index filtrés](create-filtered-indexes.md)|  
|spatial|Un index spatial permet d’effectuer plus efficacement certaines opérations sur des objets spatiaux (*données spatiales*) dans une colonne du type de données **géométrie** . L'index spatial réduit le nombre d'objets sur lesquels des opérations spatiales relativement coûteuses doivent être appliquées.|[Vue d’ensemble des index spatiaux](../spatial/spatial-indexes-overview.md)|  
|XML|Représentation fragmentée et permanente des objets binaires XML de taille importante (BLOB) dans la colonne de type de données `xml`.|[Index XML &#40;SQL Server&#41;](../xml/xml-indexes-sql-server.md)|  
|Texte intégral|Type spécial d'index fonctionnel par jeton qui est construit et géré par le Moteur d'indexation et de recherche en texte intégral Microsoft pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il permet de prendre en charge efficacement toute recherche de mot sophistiqué dans des chaînes de données caractères.|[Alimenter des index de recherche en texte intégral](../search/populate-full-text-indexes.md)|  
  
## <a name="related-tasks"></a>Tâches associées  
  
## <a name="related-content"></a>Contenu associé  
 [Option SORT_IN_TEMPDB pour les index](sort-in-tempdb-option-for-indexes.md)  
  
 [Désactiver les index et contraintes](disable-indexes-and-constraints.md)  
  
 [Activer les index et contraintes](enable-indexes-and-constraints.md)  
  
 [Renommer des index](rename-indexes.md)  
  
 [Définir les options d'index](set-index-options.md)  
  
 [Espace disque nécessaire pour les opérations DDL d’index](disk-space-requirements-for-index-ddl-operations.md)  
  
 [Réorganiser et reconstruire des index](reorganize-and-rebuild-indexes.md)  
  
 [Spécifier un facteur de remplissage pour un index](specify-fill-factor-for-an-index.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Description des index cluster et non cluster](clustered-and-nonclustered-indexes-described.md)  
  
  
