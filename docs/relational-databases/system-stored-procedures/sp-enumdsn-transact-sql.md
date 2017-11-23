---
title: sp_enumdsn (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_enumdsn
- sp_enumdsn_TSQL
helpviewer_keywords: sp_enumdsn
ms.assetid: 171cbc7d-7406-4cb0-8602-9405243bfd1d
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e8d4dcb23cf06385d4c26a198f17e806bdc0671a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spenumdsn-transact-sql"></a>sp_enumdsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la liste de tous les noms de source de données ODBC et OLE DB définis pour un serveur utilisant un compte d'utilisateur [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows spécifique. Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_enumdsn  
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**Nom de Source de données**|**sysname**|Nom de la source de données.|  
|**Description**|**varchar (255)**|Description de la source de données.|  
|**Type**|**int**|Type de la source de données :<br /><br /> **1** = NOM ODBC DSN<br /><br /> **3** = source de données OLE DB|  
|**Nom du fournisseur**|**varchar (255)**|Nom du fournisseur OLE DB. La valeur est NULL pour un DSN ODBC.|  
  
## <a name="remarks"></a>Notes  
 Chaque [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service dispose d’un contexte utilisateur. Par contexte utilisateur, on entend un ensemble d'entrées du Registre qui comprend les définitions des sources de données ODBC pour cet utilisateur. Le contexte utilisateur est fourni par le nom d'utilisateur sous lequel s'exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Par exemple, si le serveur s'exécute dans le contexte utilisateur du compte système, les noms de source de données (DSN) retournés seront tous des DSN système associés au compte système. Si le serveur s'exécute sous un compte d'utilisateur privé, seuls les DSN définis pour le compte privé de cet utilisateur sont retournés.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_enumdsn**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_dsninfo &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dsninfo-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
