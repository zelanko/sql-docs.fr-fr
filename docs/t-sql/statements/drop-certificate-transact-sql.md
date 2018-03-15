---
title: DROP CERTIFICATE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP CERTIFICATE
- DROP_CERTIFICATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], removing
- removing certificates
- dropping certificates
- DROP CERTIFICATE statement
- deleting certificates
ms.assetid: 5704aa04-68a3-4b29-b62b-8868af487817
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: dc3665867f138d8689adb8a68ef6833c5fa46c24
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="drop-certificate-transact-sql"></a>DROP CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Supprime un certificat de la base de données.  
  
> [!IMPORTANT]  
>  Une sauvegarde du certificat utilisée pour le chiffrement de la base de données doit être conservée même si le chiffrement n'est plus activé sur une base de données. Même si la base de données n'est plus chiffrée, des parties du journal des transactions peuvent toujours être protégées, et le certificat peut être nécessaire pour certaines opérations tant que la sauvegarde complète de la base de données n'a pas été effectuée. Le certificat est également nécessaire pour pouvoir restaurer les sauvegardes créées lorsque la base de données a été chiffrée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DROP CERTIFICATE certificate_name  
```  
  
## <a name="arguments"></a>Arguments  
 *certificate_name*  
 Nom unique sous lequel le certificat est connu dans la base de données.  
  
## <a name="remarks"></a>Notes   
 Les certificats ne peuvent être supprimés que si aucune entité ne leur est associée.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation CONTROL sur le certificat.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime le certificat `Shipping04` de la base de données `AdventureWorks`.  
  
```  
USE AdventureWorks2012;  
DROP CERTIFICATE Shipping04;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant supprime le certificat `Shipping04`.  
  
```  
USE master;  
DROP CERTIFICATE Shipping04;  
```  
  
## <a name="see-also"></a> Voir aussi  
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

