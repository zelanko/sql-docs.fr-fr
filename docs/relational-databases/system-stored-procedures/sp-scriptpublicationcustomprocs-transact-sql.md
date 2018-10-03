---
title: sp_scriptpublicationcustomprocs (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_scriptpublicationcustomprocs
- sp_scriptpublicationcustomprocs_TSQL
helpviewer_keywords:
- sp_scriptpublicationcustomprocs
ms.assetid: b06102d5-4284-4834-b126-bc0baea49be5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3c6a24a03e1ac8b4fff3fe4af878f051cf2e35a5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815450"
---
# <a name="spscriptpublicationcustomprocs-transact-sql"></a>sp_scriptpublicationcustomprocs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée un script pour les procédures personnalisées INSERT, UPDATE et DELETE pour tous les articles de table d'une publication dans laquelle l'option de schéma de génération automatique de procédure stockée est activée. **sp_scriptpublicationcustomprocs** est particulièrement utile pour configurer des abonnements pour lesquels l’instantané est appliqué manuellement.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_scriptpublicationcustomprocs [ @publication = ] 'publication_name'  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@publication**=] **'***publication_name***'**  
 Nom de la publication. *publication_name* est **sysname** sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Retourne un jeu de résultats qui se compose d’un seul **nvarchar (4000)** colonne. L'ensemble de résultats forme l'instruction CREATE PROCEDURE complète, nécessaire à la création de la procédure stockée personnalisée.  
  
## <a name="remarks"></a>Notes  
 Les procédures personnalisées ne font pas l'objet de scripts pour les articles sans l'option de schéma (0x2) de génération automatique de procédure personnalisée.  
  
 Les procédures suivantes sont utilisées par **sp_scriptpublicationcustomprocs** pour créer des procédures de l’abonné et ne doit pas être exécuté directement :  
  
 **sp_script_reconciliation_delproc**  
  
 **sp_script_reconciliation_insproc**  
  
 **sp_script_reconciliation_vdelproc**  
  
 **sp_script_reconciliation_xdelproc**  
  
 **sp_scriptdelproc**  
  
 **sp_scriptinsproc**  
  
 **sp_scriptmappedupdproc**  
  
 **sp_scriptupdproc**  
  
 **sp_scriptvdelproc**  
  
 **sp_scriptvupdproc**  
  
 **sp_scriptxdelproc**  
  
 **sp_scriptxupdproc**  
  
## <a name="permissions"></a>Permissions  
 Exécutez autorisation est accordée aux **public**; une vérification procédurale de sécurité est effectuée à l’intérieur de cette procédure stockée pour restreindre l’accès aux membres de la **sysadmin** rôle serveur fixe et **db_ propriétaire** rôle de base de données fixe dans la base de données actuelle.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
