---
title: sp_getdefaultdatatypemapping (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getdefaultdatatypemapping_TSQL
- sp_getdefaultdatatypemapping
helpviewer_keywords:
- sp_getdefaultdatatypemapping
ms.assetid: b8401de1-f135-41d0-ba79-ce8fe1f48c00
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 31755bb0ca1ba00d8d9b6f61b6091ce2e997f58e
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528351"
---
# <a name="spgetdefaultdatatypemapping-transact-sql"></a>sp_getdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur le mappage par défaut pour le type de données spécifié entre [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de base de données de gestion (SGBD). Cette procédure stockée est exécutée sur le serveur de distribution sur une base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_getdefaultdatatypemapping [ @source_dbms = ] 'source_dbms'   
    [ , [ @source_version = ] 'source_version' ]  
        , [ @source_type = ] 'source_type'    
    [ , [ @source_length = ] source_length ]  
    [ , [ @source_precision = ] source_precision ]  
    [ , [ @source_scale = ] source_scale ]  
    [ , [ @source_nullable = ] source_nullable ]  
        , [ @destination_dbms = ] 'destination_dbms'   
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' OUTPUT ]  
    [ , [ @destination_length = ] destination_length OUTPUT ]  
    [ , [ @destination_precision = ] destination_precision OUTPUT ]  
    [ , [ @destination_scale = ] destination_scale OUTPUT ]  
    [ , [ @destination_nullable = ] source_nullable OUTPUT ]  
    [ , [ @dataloss = ] dataloss OUTPUT ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @source_dbms = ] 'source_dbms'` Est le nom du SGBD à partir duquel les types de données sont mappés. *source_dbms* est **sysname**, et peut prendre l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Base de données source au format [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Base de données Oracle source.|  
  
 Ce paramètre est obligatoire.  
  
`[ @source_version = ] 'source_version'` Est le numéro de version du SGBD source. *source_version* est **varchar (10)**, avec NULL comme valeur par défaut.  
  
`[ @source_type = ] 'source_type'` Est le type de données dans le SGBD source. *source_type* est **sysname**, sans valeur par défaut.  
  
`[ @source_length = ] source_length` Est la longueur du type de données dans le SGBD source. *source_length* est **bigint**, avec NULL comme valeur par défaut.  
  
`[ @source_precision = ] source_precision` Est la précision du type de données dans le SGBD source. *source_precision* est **bigint**, avec NULL comme valeur par défaut.  
  
`[ @source_scale = ] source_scale` Correspond à l’échelle du type de données dans le SGBD source. *source_scale* est **int**, avec NULL comme valeur par défaut.  
  
`[ @source_nullable = ] source_nullable` Est si le type de données dans le SGBD source prend en charge une valeur NULL. *source_nullable* est **bits**, avec une valeur par défaut **1**, ce qui signifie que les valeurs NULL sont prises en charge.  
  
`[ @destination_dbms = ] 'destination_dbms'` Est le nom de la destination du SGBD. *destination_dbms* est **sysname**, et peut prendre l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de destination.|  
|**ORACLE**|Base de données Oracle de destination.|  
|**DB2**|Base de données IBM DB2 de destination.|  
|**SYBASE**|Base de données Sybase de destination.|  
  
 Ce paramètre est obligatoire.  
  
`[ @destination_version = ] 'destination_version'` Est la version de produit du SGBD de destination. *destination_version* est **varchar (10)**, avec NULL comme valeur par défaut.  
  
`[ @destination_type = ] 'destination_type' OUTPUT` Le type de données est répertorié dans le SGBD de destination. *destination_type* est **sysname**, avec NULL comme valeur par défaut.  
  
`[ @destination_length = ] destination_length OUTPUT` Est la longueur du type de données du SGBD de destination. *destination_length* est **bigint**, avec NULL comme valeur par défaut.  
  
`[ @destination_precision = ] destination_precision OUTPUT` Est la précision du type de données du SGBD de destination. *destination_precision* est **bigint**, avec NULL comme valeur par défaut.  
  
`[ @destination_scale = ] _destination_scaleOUTPUT` Correspond à l’échelle du type de données du SGBD de destination. *destination_scale* est **int**, avec NULL comme valeur par défaut.  
  
`[ @destination_nullable = ] _destination_nullableOUTPUT` Est si le type de données du SGBD de destination prend en charge une valeur NULL. *destination_nullable* est **bits**, avec NULL comme valeur par défaut. **1** signifie que les valeurs NULL sont prises en charge.  
  
`[ @dataloss = ] _datalossOUTPUT` Indique si le mappage présente le risque de perte de données. *perte de données* est **bits**, avec NULL comme valeur par défaut. **1** signifie qu’il existe un risque potentiel de perte de données.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_getdefaultdatatypemapping** est utilisée dans tous les types de réplication entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SGBD.  
  
 **sp_getdefaultdatatypemapping** retourne les données de destination par défaut de type qui est la plus proche pour le type de données source spécifiée.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_getdefaultdatatypemapping**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_helpdatatypemap &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Abonnés Oracle](../../relational-databases/replication/non-sql/oracle-subscribers.md)  
  
  
