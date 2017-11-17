---
title: "DBCC SHRINKLOG (entrepôt de données SQL Azure) | Documents Microsoft"
ms.custom: 
ms.date: 07/17/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
caps.latest.revision: 11
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f572bdbf8a0606c6652de4838b7b72664040156a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-shrinklog-azure-sql-data-warehouse"></a>DBCC SHRINKLOG (entrepôt de données SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

Réduit la taille du journal des transactions *sur l’appliance* pour actuel [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] base de données. Les données sont défragmentées afin de réduire le journal des transactions. Au fil du temps, le journal des transactions de base de données peut devenir fragmentée et inefficace. Utilisez DBCC SHRINKLOG pour réduire la fragmentation et de réduire la taille du journal.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "icône lien de rubrique") [Conventions de syntaxe Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DBCC SHRINKLOG   
    [ ( SIZE = { target_size [ MB | GB | TB ]  } | DEFAULT ) ]   
    [ WITH NO_INFOMSGS ]   
[;]  
```  
  
## <a name="arguments"></a>Arguments  
TAILLE = { *target_size* [Mo | **Go** | TO]} | **Par défaut**.  
*target_size* est la taille souhaitée pour le journal des transactions sur tous les nœuds de calcul, une fois que DBCC SHRINKLOG se termine. Il est un entier supérieur à 0.  
La taille du journal est mesurée en mégaoctets (Mo), gigaoctets (Go) ou téraoctets (To). Il s’agit de la taille combinée du journal des transactions sur tous les nœuds de calcul.  
Par défaut, DBCC SHRINKLOG réduit le journal des transactions à la taille du journal stockée dans les métadonnées de la base de données. La taille du journal dans les métadonnées est déterminée par le paramètre LOG_SIZE dans [CREATE DATABASE &#40; Entrepôt de données SQL Azure &#41; ](../../t-sql/statements/create-database-azure-sql-data-warehouse.md) ou [ALTER DATABASE &#40; Entrepôt de données SQL Azure &#41; ](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md). DBCC SHRINKLOG réduit la taille du journal des transactions à la valeur par défaut lorsque la taille `SIZE=DEFAULT` est spécifié, ou lorsque le `SIZE` clause est omise.
  
WITH NO_INFOMSGS  
Messages d’information ne sont pas affichés dans les résultats DBCC SHRINKLOG.  
  
## <a name="permissions"></a>Permissions  
Nécessite l’autorisation ALTER SERVER STATE.
  
## <a name="general-remarks"></a>Remarques d'ordre général  
DBCC SHRINKLOG ne modifie pas la taille du journal stockée dans les métadonnées de la base de données. Les métadonnées continue à contenir le paramètre LOG_SIZE qui a été spécifié dans l’instruction CREATE DATABASE ou ALTER DATABASE.
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
### <a name="a-shrink-the-transaction-log-to-the-original-size-specified-by-create-database"></a>A. Réduire le journal des transactions à la taille d’origine spécifiée par créer la base de données.  
Supposons que le journal des transactions pour la base de données d’adresses a été défini sur 100 Mo lors de la création de la base de données d’adresses. Autrement dit, l’instruction CREATE DATABASE pour les adresses avait LOG_SIZE = 100 Mo. Maintenant, supposons que le journal a été augmenté de manière à 150 Mo et que vous voulez réduire le retour de 100 Mo.
  
Chacune des instructions suivantes va tenter de réduire le journal des transactions pour la base de données d’adresses à la taille par défaut de 100 Mo. Si la réduction du journal de 100 Mo entraîne la perte de données, DBCC SHRINKLOG diminue le journal à la plus petite possible de taille, supérieure à 100 Mo, sans perte de données.
  
```sql
USE Addresses;  
DBCC SHRINKLOG ( SIZE = 100 MB );  
DBCC SHRINKLOG ( SIZE = DEFAULT );  
DBCC SHRINKLOG;  
```  
  
  

