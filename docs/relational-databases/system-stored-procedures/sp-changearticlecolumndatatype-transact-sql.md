---
title: sp_changearticlecolumndatatype (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changearticlecolumndatatype
- sp_changearticlecolumndatatype_TSQL
helpviewer_keywords:
- sp_changearticlecolumndatatype
ms.assetid: 0db80e08-fb77-4d0c-aa41-455b13ffa9b4
author: stevestein
ms.author: sstein
ms.openlocfilehash: f101d9081c7eb898d43c461a3bd64eca0c043b64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67995518"
---
# <a name="sp_changearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie le mappage du type de données de colonne d'article pour une publication Oracle. Cette procédure stockée est exécutée sur n’importe quelle base de données du serveur de distribution.  
  
> [!NOTE]  
>  Les mappages de type de données entre les types de serveur de publication pris en charge sont fournis par défaut. Utilisez **sp_changearticlecolumndatatype** uniquement lors du remplacement de ces paramètres par défaut.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changearticlecolumndatatype [ @publication= ] 'publication'  
    [ @article = ] 'article'   
    [ @column = ] 'column'  
    [ , [ @type = ] 'type' ]  
    [ , [ @length = ] length ]  
    [ , [ @precision = ] precision ]  
    [ , [ @scale = ] scale ]  
    [ , [ @publisher = ] 'publisher'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication Oracle. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @article = ] 'article'`Nom de l’article. *article* est de **type sysname**et n’a pas de valeur par défaut.  
  
`[ @column = ] 'column'`Nom de la colonne dont le mappage de type de données doit être modifié. *Column* est de **type sysname**, sans valeur par défaut.  
  
`[ @type = ] 'type'`Nom du type de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données dans la colonne de destination. *type* est de type **sysname**, avec NULL comme valeur par défaut.  
  
`[ @length = ] length`Longueur du type de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données dans la colonne de destination. *Length* est de type **bigint**, avec NULL comme valeur par défaut.  
  
`[ @precision = ] precision`Précision du type de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données dans la colonne de destination. *PRECISION* est de type **bigint**, avec NULL comme valeur par défaut.  
  
`[ @publisher = ] 'publisher'`Spécifie un serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de publication non-. *Publisher* est de **type sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **Sp_changearticlecolumndatatype** est utilisé pour remplacer les mappages de type de données par défaut entre les types de serveur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de publication pris en charge (Oracle et). Pour afficher ces mappages de type de données par défaut, exécutez [sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md).  
  
 **sp_changearticlecolumndatatype** est pris en charge uniquement pour les serveurs de publication Oracle. L'exécution de cette procédure stockée sur une publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entraîne une erreur.  
  
 **sp_changearticlecolumndatatype** doit être exécutée pour chaque mappage de colonne d’article qui doit être modifié.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_changearticlecolumndatatype**.  
  
## <a name="see-also"></a>Voir aussi  
 [Changer les propriétés des publications et des articles](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
