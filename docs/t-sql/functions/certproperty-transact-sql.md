---
title: CERTPROPERTY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/24/2017
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
- CERTPROPERTY
- CERTPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], schema names
- schemas [SQL Server], names
- CERTPROPERTY function
ms.assetid: 966c09aa-bc4e-45b0-ba53-c8381871f638
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d63968d8b07a37ea49662bd0727632a1675b3913
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="certproperty-transact-sql"></a>CERTPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne la valeur d'une propriété de certificat spécifiée.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CertProperty ( Cert_ID , '<PropertyName>' )  
  
<PropertyName> ::=  
   Expiry_Date | Start_Date | Issuer_Name   
   | Cert_Serial_Number | Subject | SID | String_SID   
```  
  
## <a name="arguments"></a>Arguments  
*Cert_ID*  
ID du certificat. *Cert_ID* est un entier.
  
*Expiry_Date*  
Date d'expiration du certificat.
  
*Start_Date*  
Date à laquelle le certificat devient valide.
  
*Issuer_Name*  
Nom de l'émetteur du certificat.
  
*Cert_Serial_Number*  
Numéro de série du certificat.
  
*Objet*  
Objet du certificat.
  
 *SID*  
SID du certificat. C'est également le SID de n'importe quelle connexion ou utilisateur mappés à ce certificat.
  
*String_SID*  
SID du certificat, sous forme de chaîne de caractères. C'est également le SID de n'importe quelle connexion ou utilisateur mappés à ce certificat.
  
## <a name="return-types"></a>Types de retour
La spécification de la propriété doit être placée dans des guillemets simples (').
  
Le type de valeur retournée dépend de la propriété qui est spécifiée dans l'appel de la fonction. Toutes les valeurs retournent sont contenues dans le type de retour de **sql_variant**.
-   *Expiry_Date* et *Start_Date* retourner **datetime**.  
-   *Cert_Serial_Number*, *Issuer_Name*, *sujet*, et *String_SID* retourner **nvarchar**.  
-   *SID* retourne **varbinary**.  
  
## <a name="remarks"></a>Notes  
Informations sur les certificats sont visibles dans le [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) affichage catalogue.
  
## <a name="permissions"></a>Permissions  
Il faut des autorisations sur le certificat et l'appelant ne doit pas avoir refusé l'autorisation VIEW DEFINITION sur le certificat.
  
## <a name="examples"></a>Exemples  
L'exemple suivant retourne l'objet du certificat.
  
```sql
-- First create a certificate.  
CREATE CERTIFICATE Marketing19 WITH   
    START_DATE = '04/04/2004' ,  
    EXPIRY_DATE = '07/07/2007' ,  
    SUBJECT = 'Marketing Print Division';  
GO  
  
-- Now use CertProperty to examine certificate  
-- Marketing19's properties.  
DECLARE @CertSubject sql_variant;  
set @CertSubject = CertProperty( Cert_ID('Marketing19'), 'Subject');  
PRINT CONVERT(nvarchar, @CertSubject);  
GO  
```  
  
## <a name="see-also"></a>Voir aussi
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[ALTER CERTIFICATE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-certificate-transact-sql.md)  
[CERT_ID &#40; Transact-SQL &#41; ](../../t-sql/functions/cert-id-transact-sql.md) 
 [Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)
[sys.certificates &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) 
 [Affichages catalogue de sécurité &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)
  
  
