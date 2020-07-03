---
title: IHsyscolumns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHsyscolumns
- IHsyscolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHsyscolumns view
ms.assetid: 263452f1-9708-48f0-9536-402a89e7f5bf
author: stevestein
ms.author: sstein
ms.openlocfilehash: 38522539230fd35aca058f9a26b53a3f4baa682b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889180"
---
# <a name="ihsyscolumns-transact-sql"></a>IHsyscolumns (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  La vue **IHsyscolumns** expose des informations sur les colonnes pour les articles publiés à partir d’un serveur de publication non SQL Server. Cette vue est stockée dans la DistributionDatabase.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom de la colonne ou du paramètre de la procédure.|  
|**id**|**int**|Identificateur d'objet de la table à laquelle cette colonne appartient ou identificateur de la procédure stockée à laquelle ce paramètre est associé.|  
|**xtype**|**tinyint**|Le type de stockage physique des [types desys.sys&#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**typestat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**tinyint**|Identificateur du type de données étendu défini par l'utilisateur.|  
|**length**|**bigint**|La longueur maximale de stockage physique des [types desys.sys&#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**xprec**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xscale**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colid**|**int**|Identificateur de colonne ou de paramètre.|  
|**xoffset**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**bitpos**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**réservé**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**colstat**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**cdefault**|**int**|Identificateur de la valeur par défaut pour cette colonne.|  
|**Domain**|**int**|Identificateur de la règle ou de la contrainte CHECK pour cette colonne.|  
|**number**|**int**|Numéro de sous-procédure lorsque la procédure est regroupée (**0** pour les entrées qui ne sont pas des procédures).|  
|**colorder**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**autoval**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**offset**|**int**|Déplacement dans la ligne où cette colonne apparaît.|  
|**CollationID**|**int**|Identificateur du classement de la colonne. NULL pour les colonnes non basées sur les caractères.|  
|**langue**|**int**|Identificateur du langage de la colonne.|  
|**statut**|**int**|Bitmap utilisée pour décrire une propriété de la colonne ou du paramètre :<br /><br /> **0x08** = la colonne autorise les valeurs NULL.<br /><br /> **0x10** = le remplissage ANSI était en vigueur lorsque des colonnes **varchar** ou **varbinary** étaient ajoutées. Les espaces à droite sont conservés pour les colonnes **varchar** et les zéros à droite sont conservés pour les colonnes **varbinary** .<br /><br /> **0x40** = le paramètre est un paramètre de sortie.<br /><br /> **0x80** = la colonne est une colonne d’identité.|  
|**type**|**int**|Le type de stockage physique des [types desys.sys&#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**UserType**|**tinyint**|L’ID du type de données défini par l’utilisateur à partir des [types desys.sys&#40;&#41;Transact-SQL ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md).|  
|**printfmt**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**prec**|**int**|Niveau de précision de cette colonne.|  
|**scale**|**int**|Échelle de cette colonne.|  
|**IsComputed**|**int**|Indicateur spécifiant si la colonne est calculée :<br /><br /> **0** = n’est pas calculé.<br /><br /> **1** = calculée.|  
|**isoutparam**|**int**|Indique si le paramètre de la procédure est un paramètre de sortie ou non :<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**IsNullable**|**int**|Indique si les colonnes autorisent les valeurs NULL :<br /><br /> **1** = true.<br /><br /> **0** = false.|  
|**classement**|**int**|Nom du classement de la colonne. NULL pour les colonnes non basées sur les caractères.|  
|**tdscollation**|**int**|Nom du classement de la colonne lors du retour dans un flux de données tabulaires (TDS).|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de bases de données hétérogènes](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tables de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Vues de réplication &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
  
  
