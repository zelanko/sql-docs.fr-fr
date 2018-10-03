---
title: sp_changesubscriptiondtsinfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriptiondtsinfo
- sp_changesubscriptiondtsinfo_TSQL
helpviewer_keywords:
- sp_changesubscriptiondtsinfo
ms.assetid: 64fc085f-f81b-493b-b59a-ee6192d9736d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 83355319cc8207369e36cf845005558fa38d4977
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47599797"
---
# <a name="spchangesubscriptiondtsinfo-transact-sql"></a>sp_changesubscriptiondtsinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés de package DTS (Data Transformation Services) d'un abonnement. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changesubscriptiondtsinfo [ [ @job_id = ] job_id ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@job_id=**] *job_id*  
 ID du travail de l'Agent de distribution pour l'abonnement par envoi de données (push). *job_id* est **varbinary (16)**, sans valeur par défaut. Pour rechercher l’ID de tâche de Distribution, exécutez **sp_helpsubscription** ou **sp_helppullsubscription**.  
  
 [ **@dts_package_name**=] **'***l’argument dts_package_name***'**  
 Spécifie le nom du package DTS. *l’argument dts_package_name* est un **sysname**, avec NULL comme valeur par défaut. Par exemple, pour spécifier un package nommé **DTSPub_Package**, vous devez spécifier `@dts_package_name = N'DTSPub_Package'`.  
  
 [ **@dts_package_password**=] **'***dts_package_password***'**  
 Spécifie le mot de passe du package. *dts_package_password* est **sysname** avec une valeur par défaut NULL, qui indique que la propriété de mot de passe ne doit être modifiée.  
  
> [!NOTE]  
>  Un package DTS doit avoir un mot de passe.  
  
 [ **@dts_package_location**=] **'***dts_package_location***'**  
 Spécifie l'emplacement du package. *dts_package_location* est un **nvarchar (12)**, avec NULL comme valeur par défaut qui spécifie que l’emplacement du package doit demeurer inchangé. L’emplacement du package peut être modifié à **distributeur** ou **abonné**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changesubscriptiondtsinfo** est utilisé pour la réplication d’instantané ou transactionnelle qui sont uniquement les abonnements envoyés.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe **db_owner** rôle de base de données fixe ou le créateur de l’abonnement peut exécuter **sp_changesubscriptiondtsinfo**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
