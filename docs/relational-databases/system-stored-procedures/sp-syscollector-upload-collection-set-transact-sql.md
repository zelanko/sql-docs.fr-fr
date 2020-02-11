---
title: sp_syscollector_upload_collection_set (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_upload_collection_set
- sp_syscollector_upload_collection_set_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_upload_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: eed9232c-2b0a-4b6a-8ba0-76b7c99f48dc
author: stevestein
ms.author: sstein
ms.openlocfilehash: eb5b4b9dce229a028be45565203bce90883e21f3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68010533"
---
# <a name="sp_syscollector_upload_collection_set-transact-sql"></a>sp_syscollector_upload_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Démarre un téléchargement de données d'un jeu d'éléments de collecte si le jeu d'éléments de collecte est activé.  
  
> [!IMPORTANT]  
>  Cette procédure stockée peut être uniquement utilisée pour les jeux d'éléments de collecte configurés pour la collecte et le téléchargement de données en mode mis en cache.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_syscollector_upload_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @collection_set_id = ] collection_set_id`Identificateur local unique pour le jeu d’Collections. *collection_set_id* est de **type int** et doit avoir une valeur si *Name* est null.  
  
`[ @name = ] 'name'`Nom du jeu d’entités de collecte. *Name* est de **type sysname** et doit avoir une valeur si *collection_set_id* a la valeur null.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 *Collection_set_id* ou le *nom* doit avoir une valeur ; les deux ne peuvent pas avoir la valeur NULL.  
  
 Cette procédure peut être utilisée pour démarrer un téléchargement à la demande pour un jeu d'éléments de collecte en cours d'exécution. Elle peut être uniquement utilisée pour les jeux d'éléments de collecte configurés pour la collecte et le téléchargement de données en mode mis en cache. Cela permet à un utilisateur d'obtenir des données à analyser sans devoir attendre un téléchargement planifié.  
  
## <a name="permissions"></a>Autorisations  
 Requiert l’appartenance au rôle de base de données fixe **dc_operator** (avec autorisation EXECUTE) pour exécuter cette procédure.  
  
## <a name="example"></a>Exemple  
 Exécute un téléchargement à la demande d'un jeu d'éléments de collecte nommé `Simple Collection Set`.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_upload_collection_set @name = 'Simple Collection Set' ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)  
  
  
