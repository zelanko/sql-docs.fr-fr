---
title: BACKUP SERVICE MASTER KEY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BACKUP SERVICE MASTER KEY
- DUMP_SERVICE_MASTER_KEY_TSQL
- DUMP SERVICE MASTER KEY
- BACKUP_SERVICE_MASTER_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backing up service master keys [SQL Server]
- BACKUP SERVICE MASTER KEY statement
- cryptography [SQL Server], Service Master Key
- exporting Service Master Keys
- encryption [SQL Server], Service Master Key
- service master key [SQL Server], exporting
ms.assetid: f8356683-6680-4f1c-9eaf-5c29a9a9020d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 427b2a7c0faff9f00d37e3d85c79c5bd2c15a2f4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="backup-service-master-key-transact-sql"></a>BACKUP SERVICE MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet d'exporter la clé principale de base de service.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BACKUP SERVICE MASTER KEY TO FILE = 'path_to_file'   
    ENCRYPTION BY PASSWORD = 'password'  
```  
  
## <a name="arguments"></a>Arguments  
 FICHIER **='***chemin_fichier***'**  
 Spécifie le chemin d'accès complet, y compris le nom de fichier, du fichier dans lequel la clé principale de service sera exportée. Cela peut être un chemin d'accès local ou le chemin UNC d'un emplacement réseau.  
  
 Mot de passe **='***mot de passe***'**  
 Mot de passe utilisé pour chiffrer la clé principale de service dans le fichier de sauvegarde. Ce mot de passe est sujet à des vérifications de complexité. Pour plus d'informations, consultez [Password Policy](../../relational-databases/security/password-policy.md).  
  
## <a name="remarks"></a>Notes  
 La clé principale de service doit être sauvegardée et stockée en lieu sûr, en dehors de votre lieu de travail. La création de cette sauvegarde doit être l'une des premières actions administratives effectuées sur le serveur.  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL SERVER sur le serveur.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple ci-dessous la clé principale de service est sauvegardée dans un fichier.  
  
```  
BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_key' ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER SERVICE MASTER KEY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-service-master-key-transact-sql.md)   
 [RESTORE SERVICE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/restore-service-master-key-transact-sql.md)  
  
  
