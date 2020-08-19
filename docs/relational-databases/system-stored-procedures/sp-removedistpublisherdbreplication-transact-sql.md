---
description: sp_removedistpublisherdbreplication (Transact-SQL)
title: sp_removedistpublisherdbreplication (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_removedistpublisherdbreplication_TSQL
- sp_removedistpublisherdbreplication
helpviewer_keywords:
- sp_removedistpublisherdbreplication
ms.assetid: 9bfe002a-25b5-4226-bcfb-feb2060d6b4a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d8ecdfd856555885eb14af34451e1a939c00b233
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469205"
---
# <a name="sp_removedistpublisherdbreplication-transact-sql"></a>sp_removedistpublisherdbreplication (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Supprime les métadonnées de publication appartenant à une publication spécifique sur le serveur de distribution. Cette procédure stockée est exécutée au niveau du serveur de distribution sur la base de données de distribution.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_removedistpublisherdbreplication [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication. *Publisher* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'` Nom de la base de données de publication. *publisher_db* est de **type sysname** et n’a pas de valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_removedistpublisherdbreplication** est utilisé par la réplication transactionnelle et d’instantané.  
  
 **sp_removedistpublisherdbreplication** est utilisé lorsqu’une base de données publiée doit être recréée sans supprimer également la base de données de distribution. Les métadonnées suivantes sont supprimées :  
  
-   Toutes les métadonnées de publication  
  
-   Les métadonnées de tous les articles appartenant à la publication  
  
-   Les métadonnées de tous les abonnements à la publication  
  
-   Les métadonnées de tous les travaux d'Agent de réplication appartenant à la publication  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** sur le serveur de distribution ou les membres du rôle de base de données fixe **db_owner** dans la base de données de distribution peuvent exécuter **sp_removedistpublisherdbreplication**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
