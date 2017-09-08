---
title: "MODIFIER les informations d’identification inclus dans l’étendue de base de données (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 02/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER DATABASE SCOPED CREDENTIAL
- ALTER_DATABASE_SCOPED_CREDENTIAL_TSQL
helpviewer_keywords:
- ALTER DATABASE SCOPED CREDENTIAL statement
- credentials [SQL Server], ALTER DATABASE SCOPED CREDENTIAL statement
ms.assetid: 966b75b5-ca87-4203-8bf9-95c4e00cb0b5
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 91224c6e96fb3ee3962331ec6f378ea9aad1a5b5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-scoped-credential-transact-sql"></a>Informations d’identification des inclus dans l’étendue de la base de données ALTER (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Modifie les propriétés d’une base de données d’une étendue d’informations d’identification.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
```  
  
## <a name="arguments"></a>Arguments  
 *credential_name*  
 Spécifie le nom de l’information d’identification de base de données applique en cours de modification.  
  
 IDENTITÉ **='***identity_name***'**  
 Spécifie le nom du compte à utiliser lors d'une connexion en dehors du serveur. Pour importer un fichier à partir du stockage d’objets Blob Azure, le nom de l’identité doit être `SHARED ACCESS SIGNATURE`.  Pour plus d’informations sur les signatures d’accès partagé, consultez [à l’aide d’accès partagé des Signatures (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1).  
    
  
 SECRET **='***secret***'**  
 Spécifie le secret requis pour l'authentification sortante. *secret* est requis pour importer un fichier à partir du stockage d’objets Blob Azure. *secret* peut être facultative à d’autres fins.   
>  [!WARNING]
>  La valeur de clé SAS pourrait commencer par un ' ?' (point d’interrogation). Lorsque vous utilisez la clé SAS, vous devez supprimer l’interligne ' ?'. Dans le cas contraire, vos efforts risque d’être bloqués.    
  
## <a name="remarks"></a>Notes  
 Lorsqu’une base de données d’une étendue informations d’identification est modifié, les valeurs des deux *identity_name* et *secret* sont réinitialisés. Si l'argument facultatif SECRET n'est pas spécifié, sa valeur stockée est NULL.  
  
 Le secret est chiffré au moyen de la clé principale du service. Si cette clé est regénérée, le secret est à nouveau chiffré à l'aide de la nouvelle clé principale du service.  
  
 Informations d’identification de base de données d’une étendue sont visibles dans le [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) affichage catalogue.  
  
## <a name="permissions"></a>Permissions  
 Requiert `ALTER` autorisation sur les informations d’identification.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-changing-the-password-of-a-database-scoped-credential"></a>A. Modifier le mot de passe d’une base de données d’une étendue d’informations d’identification  
 L’exemple suivant modifie le secret stocké dans les informations d’identification d’une étendue de la base de données appelée `Saddles`. Les informations d’identification de la portée de la base de données contient le nom de connexion Windows `RettigB` et son mot de passe. Le nouveau mot de passe est ajouté à l’aide de la clause SECRET des informations d’identification d’une étendue de la base de données.  
  
```  
ALTER DATABASE SCOPED CREDENTIAL AppCred WITH IDENTITY = 'RettigB',   
    SECRET = 'sdrlk8$40-dksli87nNN8';  
GO  
```  
  
### <a name="b-removing-the-password-from-a-credential"></a>B. Suppression du mot de passe d'une information d'identification  
 L’exemple suivant supprime le mot de passe à partir d’une information d’identification de base de données d’une étendue nommée `Frames`. Contient les informations d’identification de base de données applique la connexion Windows `Aboulrus8` et un mot de passe. Une fois que l’instruction est exécutée, les informations d’identification de la portée de la base de données aura un mot de passe NULL, car l’option SECRET n’est pas spécifiée.  
  
```  
ALTER DATABASE SCOPED CREDENTIAL Frames WITH IDENTITY = 'Aboulrus8';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations d’identification &#40; moteur de base de données &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CRÉER des informations d’identification inclus dans l’étendue de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [SUPPRIMER les informations d’identification inclus dans l’étendue de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [Sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  

