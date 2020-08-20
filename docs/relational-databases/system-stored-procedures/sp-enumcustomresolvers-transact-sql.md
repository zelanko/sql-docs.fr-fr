---
description: sp_enumcustomresolvers (Transact-SQL)
title: sp_enumcustomresolvers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_enumcustomresolvers
- sp_enumcustomresolvers_TSQL
helpviewer_keywords:
- sp_enumcustomresolvers
ms.assetid: 81bd0d3a-48dc-42b1-b662-c630f61fc630
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2579e1d099d0543b1ed8d14bccef877bb892c64e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469497"
---
# <a name="sp_enumcustomresolvers-transact-sql"></a>sp_enumcustomresolvers (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Retourne la liste de tous les gestionnaires de logique métier et résolveurs personnalisés disponibles inscrits sur le serveur de distribution. Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de publication.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_enumcustomresolvers [ [ @distributor =] 'distributor']  
```  
  
## <a name="arguments"></a>Arguments  
`[ @distributor = ] 'distributor'` Nom du serveur de distribution où se trouve le programme de résolution personnalisé. *Distributor* est de **type sysname**, avec NULL comme valeur par défaut. *Ce paramètre est déconseillé et sera supprimé dans une future version.*  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**article_resolver**|**nvarchar(255)**|Nom convivial du gestionnaire de logique métier ou du résolveur de conflit.|  
|**resolver_clsid**|**nvarchar(50)**|ID de classe (CLSID) du résolveur COM. Dans le cas d'un gestionnaire de logique métier, cette colonne retourne zéro comme valeur CLSID.|  
|**is_dotnet_assembly**|**bit**|Indique si l'inscription concerne un gestionnaire de logique métier.<br /><br /> **0** = programme de résolution des conflits basé sur com<br /><br /> **1** = gestionnaire de logique métier|  
|**dotnet_assembly_name**|**nvarchar(255)**|Nom de l'assembly [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework qui implémente le gestionnaire de logique métier.|  
|**dotnet_class_name**|**nvarchar(255)**|Nom de la classe qui remplace <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> pour implémenter le gestionnaire de logique métier.|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_enumcustomresolvers** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** et du rôle de base de données fixe **db_owner** peuvent exécuter **sp_enumcustomresolvers**.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter un gestionnaire de logique métier pour un article de fusion](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Implémenter un outil personnalisé de résolution des conflits pour un article de fusion](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [sp_lookupcustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
