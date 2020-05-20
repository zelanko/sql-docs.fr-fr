---
title: managed_backup. sp_backup_on_demand (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- smart_admin.sp_backup_on_demand
- smart_admin.sp_backup_on_demand_TSQL
- sp_backup_on_demand_TSQL
- sp_backup_on_demand
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.sp_backup_on_demand
- sp_backup_on_demand
ms.assetid: 638f809f-27fa-4c44-a549-9cf37ecc920c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bb2bda2d58504033469e8ed0f6455784efb113b8
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830441"
---
# <a name="managed_backupsp_backup_on_demand-transact-sql"></a>managed_backup. sp_backup_on_demand (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Demande la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] pour effectuer une sauvegarde de la base de données spécifiée.  
  
 Utilisez cette procédure stockée pour effectuer des sauvegardes ad hoc d'une base de données configurée avec la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Cela empêche toute interruption dans la chaîne de sauvegarde et [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] les processus sont pris en charge et la sauvegarde est stockée dans le même conteneur de stockage d’objets BLOB Azure.  
  
 À la fin de la sauvegarde, le chemin de fichier de sauvegarde complet est retourné. Il comprend le nom et l'emplacement du nouveau fichier de sauvegarde résultant de l'opération de sauvegarde.  
  
 Une erreur est retournée si la [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est sur le point d'exécuter une sauvegarde d'un type donné pour une base de données spécifiée. Dans ce cas, le message d'erreur retourné comprend le chemin de fichier de sauvegarde complet où la sauvegarde est actuellement téléchargée.  
   
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
EXEC managed_backup.sp_backup_on_demand   
[@database_name  =]  'database name',[@type = ] { 'Database' | 'Log' }  
  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Arguments  
 @database_name  
 Nom de la base de données sur laquelle la sauvegarde doit être effectuée. @database_nameEst de **type sysname**.  
  
 @type  
 Type de sauvegarde à effectuer : base de données ou journal. Le @type paramètre est de type **nvarchar (32)**.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Requiert l’appartenance au rôle de base de données **db_backupoperator** , avec les autorisations **ALTER ANY CREDENTIAL** et **Execute** sur **sp_delete_backuphistory**procédure stockée.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant effectue une demande de sauvegarde de base de données pour la base de données « TestDB ». La [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] est activée pour cette base de données.  
  
```  
Use MSDB  
Go  
EXEC managed_backup.sp_backup_on_demand  
 @database_name = 'TestDB'  
,@type = 'Database'  
  
```  
  
 Pour chaque extrait de code, sélectionnez « tsql » dans le champ d'attribut de langage.  
  
  
