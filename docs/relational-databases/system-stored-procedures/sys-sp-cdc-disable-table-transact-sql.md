---
title: Sys.sp_cdc_disable_table (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_disable_table
- sp_cdc_disable_table
- sys.sp_cdc_disable_table_TSQL
- sp_cdc_disable_table_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_disable_table
- sys.sp_cdc_disable_table
- change data capture [SQL Server], disabling tables
ms.assetid: da2156c0-504e-4d76-b9a0-4448becf9bda
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b797301b5b778bea34ad1552152e7e3e147dde37
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169169"
---
# <a name="sysspcdcdisabletable-transact-sql"></a>sys.sp_cdc_disable_table (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Désactive la capture de données modifiées pour la table source spécifiée et l'instance de capture dans la base de données actuelle. La capture des modifications de données n’est pas disponible dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prise en charge par les éditions de SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.sp_cdc_disable_table   
  [ @source_schema = ] 'source_schema' ,   
  [ @source_name = ] 'source_name'  
  [ , [ @capture_instance = ] 'capture_instance' | 'all' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@source_schema=** ] **'**_source\_schéma_**'**  
 Nom du schéma auquel appartient la table source. *source_schema* est **sysname**, sans valeur par défaut, et ne peut pas être NULL.  
  
 *source_schema* doit exister dans la base de données actuelle.  
  
 [  **@source_name=** ] **'**_source\_nom_**'**  
 Nom de la table source à partir de laquelle la capture de données modifiées doit être désactivée. *source_name* est **sysname**, sans valeur par défaut, et ne peut pas être NULL.  
  
 *source_name* doit exister dans la base de données actuelle.  
  
 [  **@capture_instance=** ] **'**_capturer\_instance_**'** | **'** tous les **'**  
 Nom de l'instance de capture à désactiver pour la table source spécifiée. *capture_instance* est **sysname** et ne peut pas être NULL.  
  
 Lorsque 'all' est spécifié, toutes les instances de capture définies pour *source_name* sont désactivés.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 **Sys.sp_cdc_disable_table** supprime la capture de données modifiées modifier la table et les fonctions système associées à l’instance de capture et de la table source spécifié. Il supprime toutes les lignes associées à l’instance de capture spécifiée à partir de la modification des tables de système de capture de données et jeux le **is_tracked_by_cdc** colonne pour l’entrée de table dans le [sys.tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) vue de catalogue égal à 0.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance dans le **db_owner** rôle de base de données fixe.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant désactive la capture des données modifiées pour la table `HumanResources.Employee`.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_disable_table   
    @source_schema = N'HumanResources',   
    @source_name = N'Employee',  
    @capture_instance = N'HumanResources_Employee';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Sys.sp_cdc_enable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)  
  
  
