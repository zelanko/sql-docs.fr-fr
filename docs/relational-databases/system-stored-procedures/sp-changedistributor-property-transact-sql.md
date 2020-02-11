---
title: sp_changedistributor_property (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changedistributor_property_TSQL
- sp_changedistributor_property
helpviewer_keywords:
- sp_changedistributor_property
ms.assetid: 04f503a1-307c-4de0-bac6-e6e97d5b6940
author: stevestein
ms.author: sstein
ms.openlocfilehash: 18921fa57cfa203b0d8e5274caeb1e17c385405c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68771302"
---
# <a name="sp_changedistributor_property-transact-sql"></a>sp_changedistributor_property (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Modifie les propriétés du serveur de distribution. Cette procédure stockée est exécutée sur n’importe quelle base de données du serveur de distribution.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changedistributor_property [ [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @property = ] 'property'`Propriété d’un serveur de distribution donné. *Property* est de **type sysname**et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**heartbeat_interval**|Nombre maximal de minutes pendant lesquelles un agent peut s'exécuter sans enregistrer de message de progression.|  
|NULL (par défaut)|Toutes les valeurs de *propriété* disponibles sont imprimées.|  
  
`[ @value = ] 'value'`Valeur de la propriété de serveur de distribution donnée. la *valeur* est de type **varchar (255)**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changedistributor_property** est utilisé dans tous les types de réplications.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_changedistributor_property](../../relational-databases/replication/codesnippet/tsql/sp-changedistributor-pro_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_changedistributor_property**.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)   
 [sp_dropdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
