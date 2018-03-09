---
title: sp_resetsnapshotdeliveryprogress (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
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
- sp_resetsnapshotdeliveryprogress
- sp_resetsnapshotdeliveryprogress_TSQL
helpviewer_keywords:
- sp_resetsnapshotdeliveryprogress
ms.assetid: 5df7d86b-d343-4d9b-88b1-74429ed092e6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0aa67918309c5c34bbe3826853c26cf7422c4666
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spresetsnapshotdeliveryprogress-transact-sql"></a>sp_resetsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Réinitialise le processus de livraison de l'instantané pour un abonnement par extraction de données (pull), afin de permettre le redémarrage de ce processus. Exécuté sur la base de données d'abonnement de l'abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_resetsnapshotdeliveryprogress [ [ @verbose_level = ] verbose_level ]  
    [ , [ @drop_table = ] 'drop_table' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@verbose_level** =] *verbose_level*  
 Spécifie la quantité d'informations renvoyées. *verbose_level*est **int**, avec une valeur par défaut **1**. La valeur **1** signifie qu’une erreur est renvoyée si les verrous nécessaires ne peut pas être obtenues sur le **MSsnapshotdeliveryprogress** table, et **0** signifie qu’aucune erreur n’est retournée.  
  
 [  **@drop_table** =] **'***drop_table***'**  
 Indique s’il faut supprimer ou tronquer les table contenant des informations sur la progression de l’instantané. *drop_table* est **nvarchar (5)**, avec une valeur par défaut **FALSE**. FALSE signifie que la table est tronquée tandis que TRUE indique que la table est supprimée.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_resetsnapshotdeliveryprogress** supprime toutes les lignes de la **MSsnapshotdeliveryprogress** table. Elle supprime efficacement toutes les métadonnées laissées sur la base de données d'abonnement par les progressions précédentes des processus de livraison d'instantanés.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** du rôle de base de données fixe peut exécuter **sp_resetsnapshotdeliveryprogress**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
