---
title: sp_resetsnapshotdeliveryprogress (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
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
- sp_resetsnapshotdeliveryprogress
- sp_resetsnapshotdeliveryprogress_TSQL
helpviewer_keywords:
- sp_resetsnapshotdeliveryprogress
ms.assetid: 5df7d86b-d343-4d9b-88b1-74429ed092e6
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 899a590bb2c634568399aca6f5520b52d26a52b4
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022735"
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
 [ **@verbose_level**=] *verbose_level*  
 Spécifie la quantité d'informations renvoyées. *verbose_level*est **int**, avec une valeur par défaut **1**. La valeur **1** signifie qu’une erreur est renvoyée si les verrous nécessaires ne peuvent pas être obtenues sur le **MSsnapshotdeliveryprogress** table, et **0** signifie qu’aucune erreur n’est retournée.  
  
 [ **@drop_table**=] **'***drop_table***'**  
 S’il faut supprimer ou tronquer les table contenant des informations sur la progression de la capture instantanée est. *drop_table* est **nvarchar (5)**, avec une valeur par défaut **FALSE**. FALSE signifie que la table est tronquée tandis que TRUE indique que la table est supprimée.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_resetsnapshotdeliveryprogress** supprime toutes les lignes dans le **MSsnapshotdeliveryprogress** table. Elle supprime efficacement toutes les métadonnées laissées sur la base de données d'abonnement par les progressions précédentes des processus de livraison d'instantanés.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_resetsnapshotdeliveryprogress**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
