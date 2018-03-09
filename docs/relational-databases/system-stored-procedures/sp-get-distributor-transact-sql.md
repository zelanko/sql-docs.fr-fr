---
title: sp_get_distributor (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_get_distributor
- sp_get_distributor_TSQL
helpviewer_keywords:
- sp_get_distributor
ms.assetid: f0134448-bc17-4f2f-bd81-619351ce56ac
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5a9a52ebbb8e17ff88008b2b04208a0d383179ea
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spgetdistributor-transact-sql"></a>sp_get_distributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Détermine si un serveur de distribution est installé sur un serveur. Cette procédure stockée est exécutée sur n'importe quelle base de données de l'ordinateur sur lequel le serveur de distribution est recherché.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_get_distributor   
```  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**installé**|**int**|**0** = No ; **1** = Oui|  
|**serveur de distribution**|**sysname**|Nom du serveur de distribution|  
|**base de données de distribution installé**|**int**|**0** = No ; **1** = Oui|  
|**est le serveur de publication de distribution**|**int**|**0** = No ; **1** = Oui|  
|**a le serveur de publication de distribution distant**|**int**|**0** = No ; **1** = Oui|  
  
## <a name="remarks"></a>Notes  
 **sp_get_distributor** est utilisée principalement par le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dans l’instantané, transactionnelle et la réplication de fusion.  
  
## <a name="permissions"></a>Permissions  
 Tout utilisateur peut exécuter **sp_get_distributor**. Un jeu de résultats non NULL est retourné lorsque cette stockée procédure est exécutée par les membres de la **db_owner** ou **replmonitor** base de données fixe sur la base de données de distribution, ou les membres de la **db_owner** rôle de base de données fixe sur au moins une base de données publiée. Un jeu de résultats non NULL est également retourné lorsque cette procédure stockée est exécutée par les utilisateurs dans la liste d’accès de publication (PAL) d’au moins une base de données publiée, ou à la publication de la base de données de distribution pour un serveur non-SQL, peuvent également exécuter **sp_get_distributor**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Script d’information du serveur de distribution et du serveur de publication](../../relational-databases/replication/administration/distributor-and-publisher-information-script.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
