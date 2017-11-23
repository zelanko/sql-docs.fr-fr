---
title: "CLÉ principale du SERVICE de restauration (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RESTORE SERVICE MASTER KEY
- RESTORE_SERVICE_MASTER_KEY_TSQL
- LOAD SERVICE MASTER KEY
- LOAD_SERVICE_MASTER_KEY_TSQL
dev_langs: TSQL
helpviewer_keywords:
- importing Service Master Keys
- copying Service Master Keys
- service master key [SQL Server], importing
- RESTORE SERVICE MASTER KEY statement
- transferring Service Master Keys
ms.assetid: a68fd0ee-70ce-4104-aca0-fcae5f41fc38
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f88ab43c6e452bbbb3b6cfa32e858ee1f091e366
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="restore-service-master-key-transact-sql"></a>RESTORE SERVICE MASTER KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet d'importer une clé principale de service à partir d'un fichier de sauvegarde.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RESTORE SERVICE MASTER KEY FROM FILE = 'path_to_file'   
    DECRYPTION BY PASSWORD = 'password' [FORCE]  
```  
  
## <a name="arguments"></a>Arguments  
 FICHIER **='***chemin_fichier***'**  
 Spécifie le chemin d'accès complet, y compris le nom de fichier, de la clé principale de service stockée. *chemin_fichier* peut être un chemin d’accès local ou un chemin d’accès UNC vers un emplacement réseau.  
  
 Mot de passe **='***mot de passe***'**  
 Spécifie le mot de passe requis pour déchiffrer la clé principale de service à importer à partir d'un fichier.  
  
 FORCE  
 Impose le remplacement de la clé principale de service, même au risque de perdre des données.  
  
## <a name="remarks"></a>Notes  
 Lorsque la clé principale de service est restaurée, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] déchiffre toutes les clés et les secrets qui ont été chiffrés au moyen de la clé principale de service en cours, puis les chiffre au moyen de la clé principale de service chargée à partir du fichier de sauvegarde.  
  
 Si l'un des déchiffrements échoue, la restauration échoue. Vous pouvez utiliser l'option FORCE pour ignorer les erreurs, mais cette option entraîne la perte de toutes les données ne pouvant pas être déchiffrées.  
  
> [!CAUTION]  
>  La clé principale de service représente la racine de la hiérarchie de chiffrement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La clé principale de service sécurise de manière directe ou indirecte toutes les autres clés de l'arborescence. Si une clé dépendante ne peut pas être déchiffrée au cours d'une restauration forcée, les données sécurisées par cette clé sont perdues.  
  
 La régénération de la hiérarchie de chiffrement est une opération qui consomme beaucoup de ressources. Par conséquent, vous devez planifier cette opération au cours d'une période de faible demande.  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation CONTROL SERVER sur le serveur.  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, la clé principale de service est restaurée à partir d'un fichier de sauvegarde.  
  
```  
RESTORE SERVICE MASTER KEY   
    FROM FILE = 'c:\temp_backups\keys\service_master_key'   
    DECRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Clé principale du service](../../relational-databases/security/encryption/service-master-key.md)   
 [ALTER SERVICE MASTER KEY &#40; Transact-SQL &#41;](../../t-sql/statements/alter-service-master-key-transact-sql.md)   
 [BACKUP SERVICE MASTER KEY &#40; Transact-SQL &#41;](../../t-sql/statements/backup-service-master-key-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
