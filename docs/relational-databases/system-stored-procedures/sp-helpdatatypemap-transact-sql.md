---
title: sp_helpdatatypemap (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdatatypemap
- sp_helpdatatypemap_TSQL
helpviewer_keywords:
- sp_helpdatatypemap
ms.assetid: 800c9c65-723e-4961-a63d-327987f129f0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0b9666c13a2e4d8183d19fade64bf49b13377b9a
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771062"
---
# <a name="sphelpdatatypemap-transact-sql"></a>sp_helpdatatypemap (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Retourne des informations sur les mappages de types de [!INCLUDE[msCoName](../../includes/msconame-md.md)] données définis entre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les systèmes de gestion de base de données (SGBD). Cette procédure stockée est exécutée sur n’importe quelle base de données du serveur de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpdatatypemap [ @source_dbms = ] 'source_dbms'   
    [ , [ @source_version = ] 'source_version' ]  
    [ , [ @source_type = ] 'source_type' ]   
    [ , [ @destination_dbms = ] 'destination_dbms' ]  
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' ]  
    [ , [ @defaults_only = ] defaults_only ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @source_dbms = ] 'source_dbms'`Nom du SGBD à partir duquel les types de données sont mappés. *source_dbms* est de **type sysname**et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Base de données source au format [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**SOLUTION**|Base de données Oracle source.|  
  
`[ @source_version = ] 'source_version'`Version du produit du SGBD source. *source_version*est de type **varchar (10)** et, s’il n’est pas spécifié, les mappages de types de données pour toutes les versions du SGBD source sont retournés. Permet de filtrer le jeu de résultats en fonction de la version source du SGBD.  
  
`[ @source_type = ] 'source_type'`Type de données indiqué dans le SGBD source. *source_type* est de **type sysname**et, s’il n’est pas spécifié, les mappages de tous les types de données dans le SGBD source sont retournés. Permet de filtrer le jeu de résultats en fonction du type de données indiqué dans le SGBD source.  
  
`[ @destination_dbms = ] 'destination_dbms'`Nom du SGBD de destination. *destination_dbms* est de **type sysname**et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de destination.|  
|**SOLUTION**|Base de données Oracle de destination.|  
|**DB2**|Base de données IBM DB2 de destination.|  
|**INTERFACES**|Base de données Sybase de destination.|  
  
`[ @destination_version = ] 'destination_version'`Version du produit du SGBD de destination. *destination_version*est de type **varchar (10)** et, s’il n’est pas spécifié, les mappages de toutes les versions du SGBD de destination sont retournés. Permet de filtrer le jeu de résultats en fonction de la version de destination du SGBD.  
  
`[ @destination_type = ] 'destination_type'`Type de données indiqué dans le SGBD de destination. *destination_type*est de **type sysname**et, s’il n’est pas spécifié, les mappages de tous les types de données du SGBD de destination sont retournés. Permet de filtrer le jeu de résultats en fonction du type de données indiqué dans le SGBD de destination.  
  
`[ @defaults_only = ] defaults_only`Est si seuls les mappages de type de données par défaut sont retournés. *defaults_only* est de valeur de **bit**, avec **0**comme valeur par défaut. **1** signifie que seuls les mappages de type de données par défaut sont retournés. **0** signifie que les mappages par défaut et les mappages de types de données définis par l’utilisateur sont retournés.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|**mapping_id**|Identifie un mappage de type de données.|  
|**source_dbms**|Nom et numéro de version du SGBD source.|  
|**source_type**|Type de données répertorié dans le SGBD source.|  
|**destination_dbms**|Nom du SGBD de destination.|  
|**destination_type**|Type de données répertorié dans le SGBD de destination.|  
|**is_default**|Indique si le mappage est un mappage par défaut ou un autre mappage. La valeur **0** indique que ce mappage est défini par l’utilisateur.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpdatatypemap** définit les mappages de types de données à partir des serveurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publication non-SQL Server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et des serveurs de publication vers des abonnés non-.  
  
 Lorsque la combinaison spécifiée de SGBD source et de destination n’est pas prise en charge, **sp_helpdatatypemap** retourne un jeu de résultats vide.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** sur le serveur de distribution ou les membres du rôle de base de données fixe **db_owner** sur la base de données de distribution peuvent exécuter **sp_helpdatatypemap**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_getdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_setdefaultdatatypemapping &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setdefaultdatatypemapping-transact-sql.md)  
  
  
