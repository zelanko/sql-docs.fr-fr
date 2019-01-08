---
title: À l’aide d’index cluster Columnstore | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 5af6b91c-724f-45ac-aff1-7555014914f4
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1e65c3e277eb9a3e5e3703525b9c1ac06b423c96
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52502705"
---
# <a name="using-clustered-columnstore-indexes"></a>Utilisation d'index columnstore cluster
  Tâches pour utiliser des index columnstore cluster dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Pour une présentation des index columnstore, consultez [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).  
  
 Pour plus d'informations sur les index columnstore cluster, consultez [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).  
  
## <a name="contents"></a>Sommaire  
  
-   [Créer un Index cluster Columnstore](#create)  
  
-   [Supprimer un Index Columnstore en cluster](#drop)  
  
-   [Charger des données dans un Index cluster Columnstore](#load)  
  
-   [Modifier des données dans un Index cluster Columnstore](#change)  
  
-   [Reconstruire un Index Columnstore en cluster](#rebuild)  
  
-   [Réorganiser un Index cluster Columnstore](#reorganize)  
  
##  <a name="create"></a> Créer un Index cluster Columnstore  
 Pour créer un index cluster columnstore, tout d’abord créer une table rowstore en tant que segment de mémoire ou index cluster, puis utiliser le [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-columnstore-index-transact-sql) instruction pour convertir la table à un cluster index ColumnStore. Si vous souhaitez que l'index columnstore cluster ait le même nom que l'index cluster, utilisez l'option DROP_EXISTING.  
  
 Cet exemple crée une table en tant que segment puis la convertit en un index columnstore cluster nommé cci_Simple. Cela modifie le stockage de la table entière qui change de rowstore en columnstore.  
  
```  
CREATE TABLE T1(  
    ProductKey [int] NOT NULL,   
    OrderDateKey [int] NOT NULL,   
    DueDateKey [int] NOT NULL,   
    ShipDateKey [int] NOT NULL);  
GO  
CREATE CLUSTERED COLUMNSTORE INDEX cci_T1 ON T1;  
GO  
```  
  
 Pour plus d’exemples, consultez la section exemples dans [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).  
  
##  <a name="drop"></a> Supprimer un Index Columnstore en cluster  
 Utilisez le [DROP INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/drop-index-transact-sql) instruction pour supprimer un index cluster columnstore. Cette opération supprime l'index et convertit la table columnstore en un segment de mémoire rowstore.  
  
##  <a name="load"></a> Charger des données dans un Index cluster Columnstore  
 Ajoutez des données à un index columnstore cluster existant à l'aide de l'une des méthodes de chargement standard.  Par exemple, le chargement en masse bcp outil, Integration Services et INSERT... SELECT peut charger des données dans un index columnstore en cluster.  
  
 Les index columnstore cluster tirent parti du deltastore pour éviter la fragmentation de segments de colonne dans le columnstore.  
  
### <a name="loading-into-a-partitioned-table"></a>Chargement dans une table partitionnée  
 Pour les données partitionnées, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] affecte d'abord chaque ligne à une partition, puis effectue les opérations de columnstore sur les données dans la partition. Chaque partition a ses propres rowgroups et au moins un deltastore.  
  
### <a name="deltastore-loading-scenarios"></a>Scénarios de chargement de deltastore  
 Les lignes s'accumulent dans le deltastore tant que le nombre de lignes n'atteint pas le nombre maximal de lignes autorisées pour un rowgroup. Lorsque le deltastore contient le nombre maximal de lignes par rowgroup, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marque le rowgroup en tant que « Fermé ». Un processus en arrière-plan, appelé le « tuple », recherche le rowgroup fermé et le déplace dans le columnstore, où le rowgroup est compressé dans des segments de colonne et les segments de colonne sont stockés dans le columnstore.  
  
 Pour chaque index columnstore cluster il peut y avoir plusieurs deltastores.  
  
-   Si un deltastore est verrouillé, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] essaie d'obtenir un verrou sur un autre deltastore. Si aucun deltastore n'est disponible, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] crée un nouveau deltastore.  
  
-   Pour une table partitionnée, il peut y avoir un ou plusieurs deltastores pour chaque partition.  
  
 Pour les index columnstore cluster uniquement, les scénarios suivants décrivent à quel moment les lignes chargées sont directement placées dans le columnstore ou dans le deltastore.  
  
 Dans l'exemple, chaque rowgroup peut avoir 102 400-1 048 576 lignes par rowgroup.  
  
|Lignes à charger en masse|Lignes ajoutées au columnstore|Lignes ajoutées au deltastore|  
|-----------------------|-----------------------------------|----------------------------------|  
|102 000|0|102 000|  
|145 000|145 000<br /><br /> Taille de rowgroup : 145 000|0|  
|1 048 577|1,048,576<br /><br /> Taille de rowgroup : 1 048 576|1|  
|2 252 152|2 252 152<br /><br /> Tailles de rowgroup : 1 048 576, 1 048 576, 155 000.|0|  
  
 L'exemple suivant montre les résultats du chargement de 1 048 577 lignes dans une partition. Les résultats indiquent un rowgroup COMPRESSÉ dans le columnstore (comme segments de colonne compressés), et 1 ligne dans le deltastore.  
  
```  
SELECT * FROM sys.column_store_row_groups  
```  
  
 ![Rowgroup et deltastore pour un chargement par lot](../../2014/database-engine/media/sql-server-pdw-columnstore-batchload.gif "Rowgroup et deltastore pour un chargement par lot")  
  

  
##  <a name="change"></a> Modifier des données dans un Index cluster Columnstore  
 Les index columnstore cluster prennent en charge les opérations DML d'insertion, mise à jour et suppression.  
  
 Utilisez [insérer &#40;Transact-SQL&#41; ](/sql/t-sql/statements/insert-transact-sql) pour insérer une ligne. La ligne sera ajoutée au deltastore.  
  
 Utilisez [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql) pour supprimer une ligne.  
  
-   Si la ligne est dans le columnstore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marque la ligne comme étant supprimée logiquement, mais ne récupère pas le stockage physique pour la ligne tant que l'index n'est pas reconstruit.  
  
-   Si la ligne est dans le deltastore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] supprime la ligne logiquement et physiquement.  
  
 Utilisez [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) pour mettre à jour une ligne.  
  
-   Si la ligne est dans le columnstore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] marque la ligne comme étant supprimée logiquement, puis insère la ligne mise à jour dans le deltastore.  
  
-   Si la ligne est dans le deltastore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] met à jour la ligne dans le deltastore.  
  
##  <a name="rebuild"></a> Reconstruire un Index Columnstore en cluster  
 Utilisez [CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-columnstore-index-transact-sql) ou [ALTER INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/alter-index-transact-sql) pour effectuer une reconstruction complète d’un index cluster columnstore existant. En outre, vous pouvez utiliser ALTER INDEX ... REBUILD pour reconstruire une partition spécifique.  
  
### <a name="rebuild-process"></a>Processus de reconstruction  
 Pour reconstruire un index cluster columnstore, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] :  
  
-   Acquiert un verrou exclusif sur la table ou la partition lorsque la reconstruction se produit.  Les données sont « hors connexion » et indisponibles pendant la reconstruction.  
  
-   Défragmente le columnstore en supprimant physiquement les lignes qui ont été logiquement supprimées de la table ; les octets supprimés sont récupérés sur le support physique.  
  
-   Fusionne les données rowstore dans le deltastore, avec les données du columnstore avant de reconstruire l'index. Lorsque la reconstruction est terminée, toutes les données sont stockées au format columnstore, puis le deltastore est vide.  
  
-   Recompresse toutes les données dans le columnstore. Il existe deux copies de l'index columnstore pendant la reconstruction. Lorsque la reconstruction est terminée, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] supprime l'index columnstore d'origine.  
  
### <a name="recommendations-for-rebuilding-a-clustered-columnstore-index"></a>Recommandations pour reconstruire un index columnstore cluster  
 Reconstruire un index columnstore cluster est utile pour supprimer une fragmentation, et pour déplacer toutes les lignes dans le columnstore. Tenez compte des recommandations suivantes :  
  
-   Reconstruisez une partition au lieu de la table entière.  
  
    1.  Reconstruire un index columnstore cluster entier prend beaucoup de temps si l'index est volumineux, et cela nécessite suffisamment d'espace disque pour stocker une copie supplémentaire de l'index pendant la reconstruction. Généralement il est nécessaire de reconstruire que la dernière partition utilisée.  
  
    2.  Pour les tables partitionnées, vous n'avez pas besoin de reconstruire l'index columnstore entier, car la fragmentation se produira probablement uniquement dans les partitions modifiées récemment. Les tables de faits et de dimension volumineuses sont généralement partitionnées pour exécuter des opérations de sauvegarde et de gestion sur les segments de la table.  
  
-   Reconstruisez une partition après des opérations DML lourdes.  
  
     Reconstruire une partition la défragmentera et réduira la mémoire sur disque. La reconstruction supprimera toutes les lignes du columnstore marquées pour suppression, et déplacera toutes les lignes du deltastore dans le columnstore.  
  
-   Reconstruisez une partition après le chargement des données.  
  
     Cela garantit que toutes les données sont stockées dans le columnstore. Si plusieurs chargements se produisent simultanément, chaque partition peut disposer de plusieurs deltastores. La reconstruction déplacera toutes les lignes du deltastore dans le columnstore.  
  
##  <a name="reorganize"></a> Réorganiser un Index cluster Columnstore  
 La réorganisation des index columnstore cluster déplace tous les rowgroups fermés dans le columnstore. Pour effectuer une réorganisation, utilisez [ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)avec l’option REORGANIZE.  
  
 La réorganisation n'est pas requise pour déplacer les rowgroups fermés dans le columnstore. Le processus de déplacement de tuple recherche tous les rowgroups CLOSED et les déplace. Toutefois, le processus de déplacement de tuple est monothread et peut ne pas déplacer les rowgroups suffisamment rapidement pour votre charge de travail.  
  
### <a name="recommendations-for-reorganizing"></a>Recommandations pour la réorganisation  
 Quand réorganiser un index cluster columnstore :  
  
-   Réorganisez un index columnstore cluster après un ou plusieurs chargements de données pour obtenir des gains de performance des requêtes aussi rapidement que possible. La réorganisation nécessite initialement des ressources processeur supplémentaires pour compresser les données, ce qui peut ralentir les performances globales du système. Toutefois, dès que les données sont compressées, les performances des requêtes s'améliorent.  
  
  
