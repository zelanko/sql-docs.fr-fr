---
title: DROP CERTIFICATE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f68e801dfbc073e1ecccbf347589a891e2a3d032
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="drop-certificate-transact-sql"></a>DROP CERTIFICATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Supprime un certificat de la base de données.  
  
> [!IMPORTANT]  
>  Une sauvegarde du certificat utilisée pour le chiffrement de la base de données doit être conservée même si le chiffrement n'est plus activé sur une base de données. Même si la base de données n'est plus chiffrée, des parties du journal des transactions peuvent toujours être protégées, et le certificat peut être nécessaire pour certaines opérations tant que la sauvegarde complète de la base de données n'a pas été effectuée. Le certificat est également nécessaire pour pouvoir restaurer les sauvegardes créées lorsque la base de données a été chiffrée.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DROP CERTIFICATE certificate_name  
```  
  
## <a name="arguments"></a>Arguments  
 *nom_certificat*  
 Nom unique sous lequel le certificat est connu dans la base de données.  
  
## <a name="remarks"></a>Notes  
 Les certificats ne peuvent être supprimés que si aucune entité ne leur est associée.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation CONTROL sur le certificat.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime le certificat `Shipping04` de la base de données `AdventureWorks`.  
  
```  
USE AdventureWorks2012;  
DROP CERTIFICATE Shipping04;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L’exemple suivant supprime le certificat `Shipping04`.  
  
```  
USE master;  
DROP CERTIFICATE Shipping04;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  


