---
title: sp_gettopologyinfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_gettopologyinfo_TSQL
- sp_gettopologyinfo
helpviewer_keywords:
- sp_gettopologyinfo
ms.assetid: 8bbe8a06-a4aa-4219-8402-12db6a4682c6
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ee8f192a96bc88c1e37d0d61b6dcf12dc074d1ea
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43025291"
---
# <a name="spgettopologyinfo-transact-sql"></a>sp_gettopologyinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur une topologie de réplication transactionnelle d'égal à égal. Exécutez [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) pour collecter des informations avant d’exécuter cette procédure.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_gettopologyinfo [ @request_id = ] request_id  
```  
  
## <a name="arguments"></a>Arguments  
 [ @request_id=] *request_id*  
 ID d'une demande de statut de topologie. *request_id* est **int**, avec NULL comme valeur par défaut. Pour obtenir un ID, utilisez le @request_id paramètre à partir de sortie [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) ou interroger la [MSpeer_topologyrequest](../../relational-databases/system-tables/mspeer-topologyrequest-transact-sql.md) (table système).  
  
## <a name="result-sets"></a>Jeux de résultats  
 sp_gettopologyinfo retourne un jeu de résultats contenant une seule colonne XML. Les données dans la colonne XML sont le même que les données de la [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) (table système).  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 sp_gettopologyinfo est utilisé dans la réplication transactionnelle d'égal à égal. Exécutez [sp_requestpeertopologyinfo](../../relational-databases/system-stored-procedures/sp-requestpeertopologyinfo-transact-sql.md) avant d’exécuter sp_gettopologyinfo. Ces procédures sont utilisées par l'Assistant Configurer la topologie d'égal à égal, mais ils peuvent également être utilisés directement si vous avez besoin d'informations de topologie dans un format XML. Si vous préférez des résultats tabulaires, interroger la [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) (table système).  
  
## <a name="permissions"></a>Permissions  
 Requiert l'appartenance au rôle serveur fixe sysadmin ou au rôle de base de données fixe db_owner.  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication transactionnelle d’égal à égal](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
