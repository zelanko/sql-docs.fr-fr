---
title: DBCC DBREINDEX (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC DBREINDEX
- DBREINDEX_TSQL
- DBREINDEX
- DBCC_DBREINDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- index rebuilding [SQL Server]
- rebuilding indexes
- dynamic index rebuilding [SQL Server]
- DBCC DBREINDEX statement
ms.assetid: 6e929d09-ccb5-4855-a6af-b616022bc8f6
caps.latest.revision: 52
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 16f1fb5a028efe879c1059f079b3d611b26616e4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-dbreindex-transact-sql"></a>DBCC DBREINDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]Reconstruit un ou plusieurs index pour une table dans la base de données spécifié.
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) à la place.  
  
**S’applique aux**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DBCC DBREINDEX   
(   
    table_name   
    [ , index_name [ , fillfactor ] ]  
)  
    [ WITH NO_INFOMSGS ]   
```  
  
## <a name="arguments"></a>Arguments  
 *table_name*  
 Nom de la table contenant le ou les index spécifiés à reconstruire. Les noms de tables doivent respecter les règles pour [identificateurs](../../relational-databases/databases/database-identifiers.md)*.*  
  
 *index_name*  
 Nom de l'index à reconstruire. Les noms d'index doivent respecter les règles applicables aux identificateurs. Si *index_name* est spécifié, *table_name* doit être spécifié. Si *index_name* n’est pas spécifié ou est « », tous les index de la table sont reconstruits.  
  
 *facteur de remplissage*  
 Pourcentage d'espace à utiliser sur chaque page d'index pour le stockage des données lors de la création ou de la reconstruction de l'index. *facteur de remplissage* remplace le facteur de remplissage lors de la création de l’index, devenant la nouvelle valeur par défaut pour l’index et pour tout autre index non-cluster reconstruit suite à la reconstruction d’un index cluster.  
 Lorsque *fillfactor* est 0, DBCC DBREINDEX utilise la valeur de facteur de remplissage dernière spécifiée pour l’index. Cette valeur est stockée dans le **sys.indexes** vue de catalogue.   
 Si *fillfactor* est spécifié, *table_name* et *index_name* doit être spécifié. Si *fillfactor* n’est pas spécifié, le facteur de remplissage par défaut, 100, est utilisé. Pour plus d’informations, consultez [Spécifier un facteur de remplissage pour un index](../../relational-databases/indexes/specify-fill-factor-for-an-index.md).  
  
 WITH NO_INFOMSGS  
 Supprime tous les messages d'information dont les niveaux de gravité sont compris entre 0 et 10.  
  
## <a name="remarks"></a>Notes  
L'instruction DBCC DBREINDEX reconstruit un index pour une table ou tous les index définis pour une table. En permettant la reconstruction dynamique d'un index, les index qui appliquent les contraintes PRIMARY KEY ou UNIQUE peuvent être reconstruits sans devoir supprimer et recréer ces contraintes. Autrement dit, vous pouvez reconstruire un index sans connaître la structure d'une table ou ses contraintes. Cela peut arriver après une copie en bloc de données dans la table.

DBCC DBREINDEX peut reconstruire tous les index d'une table en une seule instruction. Cette opération est plus simple que de coder plusieurs instructions DROP INDEX et CREATE INDEX. Comme le travail est effectué par une seule instruction, DBCC DBREINDEX est automatiquement atomique, tandis que les instructions individuelles DROP INDEX et CREATE INDEX doivent être intégrées à une transaction pour être atomiques. De même, DBCC DBREINDEX offre un plus grand nombre d'optimisations que les instructions individuelles DROP INDEX et CREATE INDEX.

Contrairement à DBCC INDEXDEFRAG ou à ALTER INDEX avec l'option REORGANIZE, DBCC DBREINDEX est une opération hors ligne. Lorsqu'un index non-cluster est reconstruit, un verrou partagé est maintenu sur la table en question pendant la durée de l'opération. Cela empêche toute modification de la table. Si la reconstruction porte sur l'index cluster, c'est un verrou de table exclusif qui est mis en place. Tout accès à la table étant bloqué, la table est effectivement hors ligne. Pour procéder à une reconstruction d'index en ligne, ou pour contrôler le degré de parallélisme lors de l'opération de reconstruction d'index, utilisez l'instruction ALTER INDEX REBUILD avec l'option ONLINE.

Pour plus d’informations sur la sélection d’une méthode pour reconstruire ou réorganiser un index, consultez [réorganiser et reconstruire des index](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md) .
  
## <a name="restrictions"></a>Restrictions  
DBCC DBREINDEX n'est pas pris en charge pour une utilisation sur les objets suivants :
-   Tables système  
-   Index spatiaux  
-   Index columnstore optimisés en mémoire xVelocity  
  
## <a name="result-sets"></a>Jeux de résultats  
À moins que NO_INFOMSGS soit spécifié (le nom de table doit être spécifié), DBCC DBREINDEX retourne toujours :
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  
L’appelant doit posséder la table ou être membre du **sysadmin** rôle serveur fixe le **db_owner** rôle de base de données fixe ou **db_ddladmin** rôle de base de données fixe.
  
## <a name="examples"></a>Exemples  
### <a name="a-rebuilding-an-index"></a>A. Reconstruction d'un index  
Dans l'exemple suivant, l'index cluster `Employee_EmployeeID` est reconstruit avec un facteur de remplissage de `80` sur la table `Employee` de la base de données `AdventureWorks`.
  
```sql  
USE AdventureWorks2012;   
GO  
DBCC DBREINDEX ('HumanResources.Employee', PK_Employee_BusinessEntityID,80);  
GO  
```  
  
### <a name="b-rebuilding-all-indexes"></a>B. Reconstruction de tous les index  
Dans l'exemple suivant, tous les index de la table `Employee` de `AdventureWorks` sont reconstruits avec un facteur de remplissage de `70`.
  
```sql
USE AdventureWorks2012;   
GO  
DBCC DBREINDEX ('HumanResources.Employee', ' ', 70);  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)  
  
  


