---
title: "Changements importants dans les fonctionnalités du moteur de base de données de SQL Server 2016 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/15/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Database Engine [SQL Server], what's new
- breaking changes [SQL Server]
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
caps.latest.revision: 144
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f45be24e7164076948dbfa28702311dd9641eae7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="breaking-changes-to-database-engine-features-in-sql-server-2016"></a>Changements importants dans les fonctionnalités du moteur de base de données de SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique décrit les modifications importantes apportées à [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)] et aux versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Ces modifications peuvent interrompre les applications, scripts ou fonctionnalités fondés sur les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Il se peut que vous rencontriez ces problèmes lors d'une mise à niveau.  
  
##  <a name="SQL15"></a> Modifications avec rupture dans [!INCLUDE[ssSQL15](../includes/sssql15-md.md)]  
  
-   La colonne sample_ms de sys.dm_io_virtual_file_stats est passée du type de données **int** à **bigint** .  
  
-   La colonne TimeStamp de sys.fn_virtualfilestats est passée du type de données **int** à **bigint** .  

-   L’utilisation (déconseillée) des algorithmes de hachage MD2, MD4, MD5, SHA ou SHA1 nécessite de définir une valeur inférieure à 130 comme niveau de compatibilité de la base de données.  

-   Sous le niveau de compatibilité de base de données 130, les conversions implicites des types de données **datetime** en **datetime2** offrent une meilleure précision en prenant en compte les fractions de milliseconde, ce qui génère différentes valeurs converties. Utilisez un transtypage explicite vers le type de données datetime2 chaque fois qu’il existe un scénario de comparaison mixte entre les types de données datetime et datetime2.

  
## <a name="previous-versions"></a>Versions précédentes  
  
-   [Changements essentiels dans les fonctionnalités du moteur de base de données de SQL Server 2014](https://msdn.microsoft.com/library/ms143179\(v=sql.120\))  
  
-   [Changements essentiels dans les fonctionnalités du moteur de base de données de SQL Server 2012](https://msdn.microsoft.com/library/ms143179\(v=sql.110\))  
  
-   [Changements essentiels dans les fonctionnalités du moteur de base de données de SQL Server 2008](https://msdn.microsoft.com/library/ms143179\(v=sql.100\))  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités du moteur de base de données dépréciées dans SQL Server 2016](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [Fonctionnalités du moteur de base de données supprimées dans SQL Server 2016](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [Compatibilité descendante du moteur de base de données SQL Server](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  

