---
title: managed_backup. sp_set_parameter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_set_parameter_TSQL
- sp_set_parameter
- smart_admin.sp_set_parameter
- smart_admin.sp_set_parameter_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_set_parameter
- smart_admin.sp_set_parameter
ms.assetid: bd8ae5fd-1337-4b7f-b0a4-153cbca9fa5f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3eab417e1d959c990e53aca3119546a73a3e1aad
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052912"
---
# <a name="managed_backupsp_set_parameter-transact-sql"></a>managed_backup. sp_set_parameter (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Définit la valeur du paramètre système Smart Admin spécifié.  
  
 Les paramètres disponibles sont associés à la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Ces paramètres sont utilisés pour définir les notifications par courrier électronique, activer les événements étendus et activer la stratégie définie par l'utilisateur en fonction des stratégies de gestion. Vous devez spécifier les paires nom/valeur des paramètres.  

  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
EXEC managed_backup.sp_set_parameter   
    [@parameter_name = ] {'SSMBackup2WANotificationEmailIds' | 'SSMBackup2WAEnableUserDefinedPolicy' | 'SSMBackup2WADebugXevent' | 'FileRetentionDebugXevent' | 'StorageOperationDebugXevent'}  
    ,[@parameter_value = ] 'parameter_value'  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Arguments  
 @parameter_name  
 Nom du paramètre à créer dont vous souhaitez définir la valeur. @parameter_nameest de type NVARCHAR (128). Les noms de paramètres disponibles sont **SSMBackup2WANotificationEmailIds**, **SSMBackup2WADebugXevent**, **SSMBackup2WAEnableUserDefinedPolicy**, **FileRetentionDebugXevent**et **StorageOperationDebugXevent**.  
  
 @parameter_value  
 Valeur du paramètre que vous souhaitez définir. @parameterla valeur est de type NVARCHAR (128).  Voici les paires nom/valeur autorisées pour les paramètres :  
  
-   @parameter_name= 'SSMBackup2WANotificationEmailIds' : @parameter_value = 'email'  
  
-   @parameter_name= 'SSMBackup2WAEnableUserDefinedPolicy' : @parameter_value = {'true' | « false »}  
  
-   @parameter_name= 'SSMBackup2WADebugXevent' : @parameter_value = {'true' | « false »}  
  
-   @parameter_name= 'FileRetentionDebugXevent' : @parameter_value = {'true' | « false »}  
  
-   @parameter_name= 'StorageOperationDebugXevent' = {'true' | « false »}  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Section facultative qui décrit les meilleures pratiques que l'utilisateur doit connaître pour l'exécution de l'instruction ou de la routine.  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Nécessite des autorisations **Execute** sur **managed_backup. sp_set_parameter** procédure stockée.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants activent les événements étendus opérationnels et de débogage.  
  
```  
-- to enable operational events  
Use msdb;  
Go  
         EXEC managed_backup.sp_set_parameter 'FileRetentionOperationalXevent', 'True'  
--  to enable debug events  
Use msdb;  
Go  
         EXEC managed_backup.sp_set_parameter 'FileRetentionDebugXevent', 'True'  
  
```  
  
 L'exemple suivant active les notifications par courrier électronique des erreurs et avertissements, et définit l'ID de courrier électronique auquel envoyer les notifications :  
  
```  
Use msdb  
Go  
EXEC managed_backup.sp_set_parameter @parameter_name = 'SSMBackup2WANotificationEmailIds', @parameter_value = '<email address>'  
  
```  
  
  
