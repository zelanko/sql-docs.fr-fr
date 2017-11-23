---
title: Sys.fn_cdc_get_column_ordinal (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 01/25/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server (starting with 2008)
f1_keywords:
- sys.fn_cdc_get_column_ordinal
- fn_cdc_get_column_ordinal_TSQL
- fn_cdc_get_column_ordinal
- sys.fn_cdc_get_column_ordinal_TSQL
dev_langs: TSQL
helpviewer_keywords:
- fn_cdc_get_column_ordinal
- sys.fn_cdc_get_column_ordinal
ms.assetid: 4bb21a57-2b94-4208-8bdf-6a3e2681d881
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c15bd3ef8ebed161705e3b8e7373cf8574161a27
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysfncdcgetcolumnordinal-transact-sql"></a>sys.fn_cdc_get_column_ordinal (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne l’ordinal de colonne de la colonne spécifiée tel qu’il apparaît dans le [table de modifications](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) associé à l’instance de capture spécifiée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sys.fn_cdc_get_column_ordinal ( 'capture_instance','column_name')  
```  
  
## <a name="arguments"></a>Arguments  
 **'** *capture_instance* **'**  
 Nom de l'instance de capture dans laquelle la colonne spécifiée est identifiée comme une colonne capturée. *capture_instance* est **sysname**.  
  
 **'** *column_name* **'**  
 Colonne sur laquelle des rapports doivent être effectués. *column_name* est **sysname**.  
  
## <a name="return-type"></a>Type de retour  
 **int**  
  
## <a name="remarks"></a>Notes  
 Cette fonction est utilisée pour identifier la position ordinale d'une colonne capturée dans le masque de mise à jour de capture des données modifiées. Il est principalement utilisé conjointement avec la fonction [sys.fn_cdc_is_bit_set](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md) pour extraire des informations du masque de mise à jour lors de l’interrogation des données modifiées.  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation SELECT sur toutes les colonnes capturées de la table source. Si un rôle de base de données pour le composant de capture des données modifiées est spécifié pour l'instance de capture, l'appartenance à ce rôle est également requise.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant obtient la position ordinale de la colonne `VacationHours` dans le masque de mise à jour pour l'instance de capture `HumanResources_Employee`. Cette valeur est ensuite utilisée dans l'appel à `sys.fn_cdc_is_bit_set` pour extraire des informations du masque de mise à jour retourné.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10),  @VacationHoursOrdinal int;  
SET @from_lsn = sys.fn_cdc_get_min_lsn('HumanResources_Employee');  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
SET @VacationHoursOrdinal = sys.fn_cdc_get_column_ordinal   
    ( 'HumanResources_Employee','VacationHours');  
SELECT *, sys.fn_cdc_is_bit_set(@VacationHoursOrdinal,  
    __$update_mask) as 'VacationHours'  
FROM cdc.fn_cdc_get_net_changes_HumanResources_Employee  
    ( @from_lsn, @to_lsn, 'all with mask');  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de capture de données modifiées &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)   
 [À propos de la capture de données modifiées &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)   
 [Sys.sp_cdc_help_change_data_capture &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [Sys.sp_cdc_get_captured_columns &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md)   
 [Sys.fn_cdc_is_bit_set &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md)  
  
  
