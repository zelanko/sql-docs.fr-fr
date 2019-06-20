---
title: sp_dsninfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dsninfo
- sp_dsninfo_TSQL
helpviewer_keywords:
- sp_dsninfo
ms.assetid: 34648615-814b-42bc-95a3-50e86b42ec4d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e6eacb453fc2f66f4b87790770fa50916916a27c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62724015"
---
# <a name="spdsninfo-transact-sql"></a>sp_dsninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les informations sur la source de données ODBC ou OLE DB à partir du serveur de distribution associé au serveur actuel. Cette procédure stockée est exécutée sur le serveur de distribution sur une base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dsninfo [ @dsn =] 'dsn'   
    [ , [ @infotype =] 'info_type']   
    [ , [ @login =] 'login']   
    [ , [ @password =] 'password']  
    [ , [ @dso_type=] dso_type]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @dsn = ] 'dsn'` Est le nom du serveur lié ODBC DSN ou OLE DB. *DSN* est **varchar (128)**, sans valeur par défaut.  
  
`[ @infotype = ] 'info_type'` Est le type d’informations à retourner. Si *type_info* n’est pas spécifié ou si NULL est spécifié, tous les types d’informations sont retournées. *type_info* est **varchar (128)**, avec NULL comme valeur par défaut et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**DBMS_NAME**|Spécifie le nom du fournisseur de la source de données.|  
|**DBMS_VERSION**|Spécifie la version de la source de données.|  
|**DATABASE_NAME**|Spécifie le nom de la base de données.|  
|**SQL_SUBSCRIBER**|Spécifie que la source de données peut être un Abonné.|  
  
`[ @login = ] 'login'` Est le nom de connexion pour la source de données. Si la source de données comporte une connexion, spécifiez NULL ou omettez le paramètre. *connexion*est **varchar (128)**, avec NULL comme valeur par défaut.  
  
`[ @password = ] 'password'` Est le mot de passe pour la connexion. Si la source de données comporte une connexion, spécifiez NULL ou omettez le paramètre. *mot de passe*est **varchar (128)**, avec NULL comme valeur par défaut.  
  
`[ @dso_type = ] dso_type` Est le type de source de données. *type_dso* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1** (par défaut)|Source de données ODBC|  
|**3**|Source de données OLE DB|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**Type d’informations**|**nvarchar(64)**|Types d'information, tels que DBMS_NAME, DBMS_VERSION, DATABASE_NAME, SQL_SUBSCRIBER.|  
|**Valeur**|**nvarchar(512)**|Valeur du type d'information associé.|  
  
## <a name="remarks"></a>Notes  
 **sp_dsninfo** est utilisée dans tous les types de réplication.  
  
 **sp_dsninfo** récupère ODBC ou OLE DB informations de source de données qui indique si la base de données peut être utilisé pour la réplication ou l’interrogation.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_dsninfo**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_enumdsn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-enumdsn-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
