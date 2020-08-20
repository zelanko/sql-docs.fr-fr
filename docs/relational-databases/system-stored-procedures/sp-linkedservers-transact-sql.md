---
description: sp_linkedservers (Transact-SQL)
title: sp_linkedservers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_linkedservers
- sp_linkedservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_linkedservers
ms.assetid: d8f82f78-8a1f-4831-bcee-7c36c6e7dfbb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a20fe8ad07a365c8d041794d9f4236abc03f3e93
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493132"
---
# <a name="sp_linkedservers-transact-sql"></a>sp_linkedservers (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Renvoie la liste des serveurs liés définis dans le serveur local.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_linkedservers  
```  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou un nombre différent de zéro (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**SRV_NAME**|**sysname**|Nom du serveur lié.|  
|**SRV_PROVIDERNAME**|**nvarchar (** 128 **)**|Nom du fournisseur OLE DB gérant l'accès au serveur lié spécifié.|  
|**SRV_PRODUCT**|**nvarchar (** 128 **)**|Nom de produit du serveur lié.|  
|**SRV_DATASOURCE**|**nvarchar (** 4000 **)**|Propriété de source de données OLE DB correspondant au serveur lié spécifié.|  
|**SRV_PROVIDERSTRING**|**nvarchar (** 4000 **)**|Propriété de chaîne du fournisseur OLE DB correspondant au serveur lié.|  
|**SRV_LOCATION**|**nvarchar (** 4000 **)**|Propriété d'emplacement OLE DB correspondant au serveur lié spécifié.|  
|**SRV_CAT**|**sysname**|Propriété de catalogue OLE DB correspondant au serveur lié spécifié.|  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation SELECT sur le schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_columns_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_primarykeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [Procédures stockées système &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées de requêtes distribuées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)  
  
  
