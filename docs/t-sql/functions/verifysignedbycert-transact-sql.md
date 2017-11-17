---
title: VERIFYSIGNEDBYCERT (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VERIFYSIGNEDBYCERT
- VERIFYSIGNEDBYCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- digitally signed data for changes [SQL Server]
- verifying digitally signed data for changes
- testing digitally signed data for changes
- checking digitally signed data for changes
- VERIFYSIGNEDBYCERT
- signatures [SQL Server]
- digital signatures [SQL Server]
ms.assetid: 4e041f33-60c4-4190-91c7-220d51dd6c8f
caps.latest.revision: 41
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6d4725d6e9e28100333040061eafb54f07db9066
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="verifysignedbycert-transact-sql"></a>VERIFYSIGNEDBYCERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Teste si les données signées numériquement ont été modifiées depuis leur dernière signature.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
VerifySignedByCert( Cert_ID , signed_data , signature )  
```  
  
## <a name="arguments"></a>Arguments  
 *Cert_ID*  
 Identificateur d'un certificat dans la base de données. *Cert_ID* est **int**.  
  
 *signed_data*  
 Est une variable de type **nvarchar**, **char**, **varchar**, ou **nchar** qui contient les données qui a été signées avec un certificat.  
  
 *signature*  
 Signature attachée aux données signées. *signature* est **varbinary**.  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
 Retourne 1 lorsque les données signées n'ont pas changé, sinon 0.  
  
## <a name="remarks"></a>Notes  
 **VerifySignedBycert** déchiffre la signature des données à l’aide de la clé publique du certificat spécifié et compare la valeur déchiffrée à un hachage MD5 calculée qui vient d’être des données. Si les valeurs correspondent, la validité de la signature est confirmée.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation VIEW DEFINITION sur le certificat.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-verifying-that-signed-data-has-not-been-tampered-with"></a>A. Vérification de la non-falsification des données signées  
 L'exemple suivant vérifie si les informations contenues dans `Signed_Data` ont été modifiées depuis leur signature à l'aide du certificat `Shipping04`. La signature est stockée dans `DataSignature`. Le certificat, `Shipping04`, est transmis à `Cert_ID` qui retourne l'ID du certificat dans la base de données. Si `VerifySignedByCert` retourne la valeur 1, la signature est correcte. Si `VerifySignedByCert` retourne la valeur 0, les données de `Signed_Data` sont différentes de celles utilisées pour générer `DataSignature`. Dans ce cas, soit `Signed_Data` a été modifié depuis qu’il a été signé ou `Signed_Data` a été signé avec un certificat différent.  
  
```  
SELECT Data, VerifySignedByCert( Cert_Id( 'Shipping04' ),  
    Signed_Data, DataSignature ) AS IsSignatureValid  
FROM [AdventureWorks2012].[SignedData04]   
WHERE Description = N'data signed by certificate ''Shipping04''';  
GO  
```  
  
### <a name="b-returning-only-records-that-have-a-valid-signature"></a>B. Obtention des seuls enregistrements dont la signature est valide  
 Cette requête retourne uniquement les enregistrements qui n'ont pas été modifiés depuis leur signature à l'aide du certificat `Shipping04`.  
  
```  
SELECT Data FROM [AdventureWorks2012].[SignedData04]   
WHERE VerifySignedByCert( Cert_Id( 'Shipping04' ), Data,   
    DataSignature ) = 1   
AND Description = N'data signed by certificate ''Shipping04''';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CERT_ID &#40; Transact-SQL &#41;](../../t-sql/functions/cert-id-transact-sql.md)   
 [SIGNBYCERT &#40; Transact-SQL &#41;](../../t-sql/functions/signbycert-transact-sql.md)   
 [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [BACKUP CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/backup-certificate-transact-sql.md)   
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  

