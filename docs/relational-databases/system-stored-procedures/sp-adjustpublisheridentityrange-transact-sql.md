---
title: sp_adjustpublisheridentityrange (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_adjustpublisheridentityrange_TSQL
- sp_adjustpublisheridentityrange
helpviewer_keywords:
- sp_adjustpublisheridentityrange
ms.assetid: 64f111fd-fb7d-4459-93f7-65f0f8dd7efe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2016996f05393777f8284c78d854301f22ba8f73
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47625017"
---
# <a name="spadjustpublisheridentityrange-transact-sql"></a>sp_adjustpublisheridentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajuste la plage d'identités sur une publication et réaffecte de nouvelles plages en fonction de la valeur de seuil définie pour la publication. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_adjustpublisheridentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @table_name = ] 'table_name' ]  
    [ , [ @table_owner= ] 'table_owner' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=**] **'***publication***'**  
 Nom de la publication dans laquelle de nouvelles plages d'identité sont réaffectées. *publication* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@table_name=**] **'***table_name***'**  
 Nom de la table dans laquelle de nouvelles plages d'identité sont réaffectées. *table_name* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@table_owner=**] **'***table_owner***'**  
 Nom du propriétaire de la table au niveau du serveur de publication. *TABLE_OWNER* est **sysname**, avec NULL comme valeur par défaut. Si *table_owner* n’est pas spécifié, le nom de l’utilisateur actuel est utilisé.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_adjustpublisheridentityrange** est utilisée dans tous les types de réplication.  
  
 Lorsque le paramètre d'affectation automatique de plage d'identités est activé pour une publication, l'Agent de distribution ou de fusion est responsable de l'ajustement automatique de la plage d'identités en fonction de la valeur de seuil de la publication. Toutefois, si pour une raison quelconque l’Agent de Distribution ou l’Agent de fusion n'a pas été exécuté pendant une période de temps, et la ressource de plage d’identité a été sensiblement sollicitée jusqu’au point de seuil, les utilisateurs peuvent appeler **sp_adjustpublisheridentityrange** pour allouer une nouvelle plage de valeurs pour un serveur de publication.  
  
 Lors de l’exécution **sp_adjustpublisheridentityrange**, soit *publication* ou *table_name* doit être spécifié. Si les deux sont spécifiés ou aucun des deux, un message d'erreur est renvoyé.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_adjustpublisheridentityrange**.  
  
## <a name="see-also"></a>Voir aussi  
 [Répliquer des colonnes d’identité](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
