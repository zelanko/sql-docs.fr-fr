---
title: sp_helpreplicationoption (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplicationoption
- sp_helpreplicationoption_TSQL
helpviewer_keywords:
- sp_helpreplicationoption
ms.assetid: ef988dbc-dd0b-4132-80ab-81eebec1cffe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e04daaa5be757df60f07a8bd9205e1fd44f95502
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775744"
---
# <a name="sp_helpreplicationoption-transact-sql"></a>sp_helpreplicationoption (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Indique les types des options de réplication activées pour un serveur. Cette procédure stockée est exécutée sur n'importe quelle base de données de n'importe quel serveur.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpreplicationoption [ [ @optname =] 'option_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @optname = ] 'option_name'`Nom de l’option de réplication à interroger. *option_name* est de **type sysname**, avec NULL comme valeur par défaut.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**transactionnelle**|Un ensemble de résultats est renvoyé lorsque la réplication transactionnelle est activée.|  
|**fusion**|Un ensemble de résultats est renvoyé lorsque la réplication de fusion est activée.|  
|NULL (par défaut)|Aucun ensemble de résultats n'est renvoyé.|  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**optname**|**sysname**|Nom de l'option de réplication ; il peut s’agir de l'une des options suivantes :<br /><br /> **transactionnelle**<br /><br /> **fusion**|  
|**value**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**major_version**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**minor_version**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**faisant**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**install_failures**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Remarques  
 **sp_helpreplicationoption** est utilisé pour obtenir des informations sur les options de réplication activées sur un serveur particulier. Pour obtenir des informations sur une base de données particulière, utilisez **sp_helpreplicationdboption**.  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution reviennent par défaut au rôle **public** .  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
