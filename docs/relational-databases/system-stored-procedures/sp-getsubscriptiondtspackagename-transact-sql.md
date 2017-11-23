---
title: sp_getsubscriptiondtspackagename (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- sp_getsubscriptiondtspackagename
- sp_getsubscriptiondtspackagename_TSQL
helpviewer_keywords: sp_getsubscriptiondtspackagename
ms.assetid: 606c40aa-2593-43af-9762-0f260bbb51f2
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 80eaff3653634de814935f31b9312ab5db17f0f4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spgetsubscriptiondtspackagename-transact-sql"></a>sp_getsubscriptiondtspackagename (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie le nom du package DTS (Data Transformation Services) utilisé pour transformer les données avant leur envoi à un abonné. Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_getsubscriptiondtspackagename [ @publication = ] 'publication'   
    [ , [ @subscriber = ] 'subscriber' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication** =] **'***publication***'**  
 Nom de la publication. **'***publication***'** est **sysname**, sans valeur par défaut.  
  
 [  **@subscriber=**] **'***abonné***'**  
 Nom de l'Abonné. *abonné* est de type sysname, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**new_package_name**|**sysname**|Nom du package DTS.|  
  
## <a name="remarks"></a>Notes  
 **sp_getsubscriptiondtspackagename** est utilisé dans la réplication de capture instantanée et la réplication transactionnelle.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** du rôle de base de données fixe peut exécuter **sp_getsubscriptiondtspackagename**.  
  
  
