---
title: sp_redirect_publisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_redirect_publisher_TSQL
- sp_redirect_publisher
helpviewer_keywords:
- sp_redirect_publisher
ms.assetid: af45e2b2-57fb-4bcd-a58b-e61401fb3b26
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6062522ca6c5c3a311ba2f2c796f791c47e874ab
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252116"
---
# <a name="sp_redirect_publisher-transact-sql"></a>sp_redirect_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Spécifie un serveur de publication redirigé pour une paire serveur de publication/base de données existante. Si la base de données du serveur de publication appartient à un groupe de disponibilité Always On, le serveur de publication Redirigé est le nom de l’écouteur de groupe de disponibilité associé au groupe de disponibilité.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_redirect_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name'   
    [ , [ @redirected_publisher = ] 'new_publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @original_publisher = ] 'original_publisher'` nom de l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui a initialement publié la base de données. *original_publisher* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'` nom de la base de données en cours de publication. *publisher_db* est de **type sysname**, sans valeur par défaut.  
  
`[ @redirected_publisher = ] 'redirected_publisher'` nom d’écouteur de groupe de disponibilité associé au groupe de disponibilité qui sera le nouveau serveur de publication. *redirected_publisher* est de **type sysname**, sans valeur par défaut. Lorsque l'écouteur du groupe de disponibilité est configuré sur un port non défini par défaut, spécifiez le numéro de port avec le nom d'écouteur, par exemple `'Listenername,51433'`  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="remarks"></a>Notes  
 **sp_redirect_publisher** permet de rediriger un serveur de publication de réplication vers le réplica principal actuel d’un groupe de disponibilité Always on en associant la paire serveur de publication/base de données à l’écouteur d’un groupe de disponibilité. Exécutez **sp_redirect_publisher** une fois que l’écouteur GA a été configuré pour le groupe de disponibilité qui contient la base de données publiée.  
  
 Si la base de données de publication sur le serveur de publication d’origine est supprimée d’un groupe de disponibilité sur le réplica principal, exécutez **sp_redirect_publisher** sans spécifier de valeur pour le paramètre *\@redirected_publisher* pour supprimer la redirection pour la paire serveur de publication/base de données. Pour plus d’informations sur la redirection du serveur de publication lorsque, consultez [maintenance d' &#40;une&#41;base de données de publication AlwaysOn SQL Server](../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md).  
  
## <a name="permissions"></a>Autorisations  
 L’appelant doit être membre du rôle serveur fixe **sysadmin** , du rôle de base de données fixe **db_owner** pour la base de données de distribution ou d’un membre d’une liste d’accès à la publication pour une publication définie associée à la base de données du serveur de publication.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
