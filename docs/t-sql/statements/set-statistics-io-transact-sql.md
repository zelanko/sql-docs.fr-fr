---
title: "DÉFINIR des statistiques d’e/s (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 11/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_STATISTICS_IO_TSQL
- IO
- IO_TSQL
- SET STATISTICS IO
dev_langs:
- TSQL
helpviewer_keywords:
- disk I/O statistics [SQL Server]
- I/O [SQL Server], disk activity information
- disks [SQL Server], statement statistics
- STATISTICS IO option
- statements [SQL Server], statistical information
- SET STATISTICS IO statement
- statistical information [SQL Server], disk activity
ms.assetid: 7033aac9-a944-4156-9ff4-6ef65717a28b
caps.latest.revision: 40
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 99e1dc183844f25002057b7cebd4729ff5f1bbe5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="set-statistics-io-transact-sql"></a>SET STATISTICS IO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Force [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à afficher des informations sur la quantité d'activité générée sur le disque par les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SET STATISTICS IO { ON | OFF }  
```  
  
## <a name="remarks"></a>Notes  
 Si STATISTICS IO est défini sur ON, des informations statistiques sont affichées. Si l'option est désactivée (OFF), ces informations ne sont pas affichées.  
  
 Une fois l'option activée, toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes renvoient des informations statistiques, jusqu'à ce que l'option soit de nouveau désactivée.  
  
 Le tableau ci-dessous répertorie et décrit les éléments de sortie.  
  
|Élément de sortie|Signification|  
|-----------------|-------------|  
|**Table**|Nom de la table.|  
|**Nombre d’analyses**|Nombre de recherches/analyses démarrées après avoir atteint le niveau feuille dans n'importe quelle direction afin de récupérer toutes les valeurs pour construire le dataset final de la sortie.<br /><br /> Le nombre d'analyses est 0 si l'index utilisé est un index unique ou un index cluster sur une clé principale et que vous recherchez une seule valeur. Par exemple, `WHERE Primary_Key_Column = <value>`.<br /><br /> Le nombre d'analyses est 1 lorsque vous recherchez une valeur à l'aide d'un index cluster non unique qui est défini sur une colonne clé non principale. Cela permet de rechercher les valeurs en double de la valeur clé que vous recherchez. Par exemple, `WHERE Clustered_Index_Key_Column = <value>`.<br /><br /> Le nombre d'analyses est N lorsque N correspond au nombre de recherches/analyses différentes à gauche ou à droite au niveau feuille après avoir recherché une valeur clé à l'aide de la clé d'index.|  
|**lectures logiques**|Nombre de pages lues à partir du cache de données.|  
|**lectures physiques**|Nombre de pages lues depuis le disque.|  
|**lectures anticipées**|Nombre de pages placées dans le cache pour la requête.|  
|**lectures logiques métier**|Nombre de **texte**, **ntext**, **image**, ou le type de valeur élevée (**varchar (max)**, **nvarchar (max)**, **varbinary (max)**) pages lues à partir du cache de données.|  
|**lectures physiques métier**|Nombre de **texte**, **ntext**, **image** ou lire des pages de type de valeur élevée à partir du disque.|  
|**lectures anticipées LOB**|Nombre de **texte**, **ntext**, **image** ou pages placées dans le cache pour la requête de type de valeur élevée.|  
  
 L'option SET STATISTICS IO est définie lors de l'exécution, et non pas durant l'analyse.  
  
> [!NOTE]  
>  Lorsque des instructions Transact-SQL extraient des colonnes LOB, certaines opérations d'extraction peuvent entraîner le parcours de l'arbre LOB à de multiples reprises. L'option SET STATISTICS IO peut alors signaler un nombre de lectures logiques plus élevé que prévu.  
  
## <a name="permissions"></a>Permissions  
 Pour utiliser SET STATISTICS IO, les utilisateurs doivent disposer des autorisations appropriées pour exécuter l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'autorisation SHOWPLAN n'est pas nécessaire.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant illustre comment de nombreuses lectures logiques et physiques sont utilisées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], durant le traitement d'instructions.  
  
```  
USE AdventureWorks2012;  
GO         
SET STATISTICS IO ON;  
GO  
SELECT *   
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;  
GO  
SET STATISTICS IO OFF;  
GO  
```  
  
 Voici l'ensemble de résultats obtenu :  
  
```  
Table 'ProductCostHistory'. Scan count 1, logical reads 5, physical   
reads 0, read-ahead reads 0, lob logical reads 0, lob physical reads 0,   
lob read-ahead reads 0.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_ALL &#40; Transact-SQL &#41;](../../t-sql/statements/set-showplan-all-transact-sql.md)   
 [DÉFINIR STATISTICS TIME &#40; Transact-SQL &#41;](../../t-sql/statements/set-statistics-time-transact-sql.md)  
  
  

