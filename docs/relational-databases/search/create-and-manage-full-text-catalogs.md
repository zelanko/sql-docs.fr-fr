---
title: Créer et gérer des catalogues de texte intégral | Microsoft Docs
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text search [SQL Server], using SQL Server Management Studio
ms.assetid: 824b7131-44a6-4815-89e6-62b7bab060e3
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ed7e7f31da9cacaf4862c29ada9c98df9559f9c9
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72903862"
---
# <a name="create-and-manage-full-text-catalogs"></a>Créer et gérer des catalogues de texte intégral
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Un catalogue de texte intégral est un conteneur logique pour un groupe d’index de recherche en texte intégral. Vous devez créer un catalogue de texte intégral avant de pouvoir créer un index de recherche en texte intégral.

Un catalogue de texte intégral est un objet virtuel qui n’appartient à aucun groupe de fichiers.
  
##  <a name="creating"></a> Créer un catalogue de texte intégral  

### <a name="create-a-full-text-catalog-with-transact-sql"></a>Créer un catalogue de texte intégral avec Transact-SQL
Utilisez [CREATE FULLTEXT CATALOG](../../t-sql/statements/create-fulltext-catalog-transact-sql.md). Par exemple :

```sql 
USE AdventureWorks;  
GO  
CREATE FULLTEXT CATALOG ftCatalog AS DEFAULT;  
GO  
``` 

### <a name="create-a-full-text-catalog-with-management-studio"></a>Créer un catalogue de texte intégral avec Management Studio
1.  Dans l’Explorateur d’objets, développez successivement le serveur, le nœud **Bases de données**, puis la base de données contenant le catalogue de texte intégral à créer.  
  
2.  Développez **Stockage**, puis cliquez avec le bouton droit sur **Catalogues de texte intégral**.  
  
3.  Sélectionnez **Nouveau catalogue de recherche en texte intégral**.  
  
4.  Dans la boîte de dialogue **Nouveau catalogue de recherche en texte intégral**, précisez les informations relatives au catalogue que vous recréez. Pour plus d’informations, consultez [Recherche en texte intégral &#40;page Général&#41;](/sql/database-engine/new-full-text-catalog-general-page).  
  
    > [!NOTE]  
    >  Les ID de catalogues de texte intégral commencent à 00005 et sont incrémentés d'une unité à chaque fois qu'un catalogue est créé.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

##  <a name="props"></a> Obtenir les propriétés d’un catalogue de texte intégral  
Utilisez la fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] **FULLTEXTCATALOGPROPERTY** pour obtenir la valeur de diverses propriétés relatives aux catalogues de texte intégral. Pour plus d’informations, consultez [FULLTEXTCATALOGPROPERTY](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md).

Par exemple, exécutez la requête suivante pour obtenir le nombre d’index dans le catalogue de texte intégral `Catalog1`.

```sql 
USE <database>;  
GO  
SELECT fulltextcatalogproperty('Catalog1', 'ItemCount');  
GO  
```  
  
Le tableau suivant répertorie les propriétés liées aux catalogues de texte intégral. Ces informations peuvent être utiles pour administrer la recherche en texte intégral et résoudre les problèmes qui la concernent. 
  
|Propriété|Description|  
|--------------|-----------------|  
|**AccentSensitivity**|Respect des accents.|
|**ImportStatus**|Indique si le catalogue de texte intégral est en cours d'importation.|  
|**IndexSize**|Taille du catalogue de texte intégral en mégaoctets (Mo).| 
|**ItemCount**|Nombre d'éléments indexés de texte intégral actuellement dans le catalogue de texte intégral.|  
|**MergeStatus**|Indique si une fusion principale est en cours.| 
|**PopulateCompletionAge**|Différence en secondes entre la fin du remplissage du dernier index de texte intégral et le 01/01/1990 00:00:00.| 
|**PopulateStatus**|État de remplissage.<br /><br /> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|  
|**UniqueKeyCount**|Nombre de clés uniques dans le catalogue de texte intégral.| 

##  <a name="rebuildone"></a> Reconstruire un catalogue de texte intégral  

Exécutez l’instruction Transact-SQL [ALTER FULLTEXT CATALOG... REBUILD](
../../t-sql/statements/alter-fulltext-catalog-transact-sql.md) ou effectuez les opérations suivantes dans SSMS (SQL Server Management Studio).

1.  Dans SSMS, dans l’Explorateur d’objets, développez successivement le serveur, l’option **Bases de données**, puis la base de données contenant le catalogue de texte intégral à reconstruire.  
  
2.  Développez **Stockage**, puis **Catalogues de texte intégral**.  
  
3.  Cliquez avec le bouton droit sur le nom du catalogue de texte intégral que vous souhaitez reconstruire, puis sélectionnez **Reconstruire**.  
  
4.  En réponse à la question **Voulez-vous supprimer le catalogue de texte intégral et le reconstruire ?** , cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue **Reconstruire le catalogue de texte intégral** , cliquez sur **Fermer**.  
   
##  <a name="rebuildall"></a> Reconstruire tous les catalogues de texte intégral pour une base de données  

1.  Dans SSMS, dans l’Explorateur d’objets, développez successivement le serveur, l’option **Bases de données**, puis la base de données contenant les catalogues de texte intégral à reconstruire.  
  
2.  Développez **Stockage**, puis cliquez avec le bouton droit sur **Catalogues de texte intégral**.  
  
3.  Sélectionnez **Tout reconstruire**.  
  
4.  En réponse à la question **Voulez-vous supprimer tous les catalogues de texte intégral et les reconstruire ?** , cliquez sur **OK**.  
  
5.  Dans la boîte de dialogue **Reconstruire tous les catalogues de texte intégral** , cliquez sur **Fermer**.  
  
  
  
##  <a name="removing"></a> Supprimer un catalogue de texte intégral d’une base de données  

Exécutez l’instruction Transact-SQL [DROP FULLTEXT CATALOG](
../../t-sql/statements/drop-fulltext-catalog-transact-sql.md) ou effectuez les opérations suivantes dans SSMS (SQL Server Management Studio).

1.  Dans SSMS, dans l’Explorateur d’objets, développez successivement le serveur, l’option **Bases de données**, puis la base de données qui contient le catalogue de texte intégral à supprimer.  
  
2.  Développez **Stockage**, puis **Catalogues de texte intégral**.  
  
3.  Cliquez avec le bouton droit sur le catalogue de texte intégral à supprimer, puis cliquez sur **Supprimer**.  
  
4.  Dans la boîte de dialogue **Supprimer les objets** , cliquez sur **OK**.  

## <a name="next-step"></a>Étape suivante
[Créer et gérer des index de recherche en texte intégral](../../relational-databases/search/create-and-manage-full-text-indexes.md)
