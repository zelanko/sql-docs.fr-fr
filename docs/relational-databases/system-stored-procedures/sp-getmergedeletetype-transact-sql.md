---
title: sp_getmergedeletetype (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getmergedeletetype
- sp_getmergedeletetype_TSQL
helpviewer_keywords:
- sp_getmergedeletetype
ms.assetid: 64450e4d-844d-4176-874e-f3845536f7d2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 406eb51a43b350a5e6f0f2d4723baab40a62ce5e
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881612"
---
# <a name="sp_getmergedeletetype-transact-sql"></a>sp_getmergedeletetype (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Renvoie le type de suppression de fusion. Cette procédure stockée est exécutée sur la base de données de publication du serveur de publication ou sur la base de données d’abonnement de l’abonné.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_getmergedeletetype [ @source_object = ] 'source_object', [ @rowguid =] 'rowguid', [ @delete_type=] delete_type OUTPUT  
```  
  
## <a name="arguments"></a>Arguments  
`[ @source_object = ] 'source_object'`Nom de l’objet source. *source_object* est de type **nvarchar (386)**, sans valeur par défaut.  
  
`[ @rowguid = ] 'rowguid'`Identificateur de ligne pour le type de suppression. *rowguid* est de type **uniqueidentifier**et n’a pas de valeur par défaut.  
  
`[ @delete_type = ] delete_type OUTPUT`Code indiquant le type de suppression. *delete_type* est de **type int**, sans valeur par défaut. *delete_type* est également un paramètre de sortie, et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Suppression par l'utilisateur|  
|**5**|Suppression partielle|  
|**6**|Suppression par le système|  
  
## <a name="remarks"></a>Remarques  
 **sp_getmergedeletetype** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_getmergedeletetype**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
