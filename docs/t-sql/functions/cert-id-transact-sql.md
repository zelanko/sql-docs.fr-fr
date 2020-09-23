---
description: CERT_ID (Transact-SQL)
title: CERT_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CERT_ID
- CERT_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identification numbers [SQL Server], certificates
- CERT_ID function
- IDs [SQL Server], certificates
- certificates [SQL Server], IDs
ms.assetid: 59cc06f5-272e-4936-8afe-afba7aba8eea
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 70e1cb5ea77b6bd779d63cd349f1478cda31598f
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91114949"
---
# <a name="cert_id-transact-sql"></a>CERT_ID (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Cette fonction retourne la valeur d’ID d’un certificat.
  
![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
Cert_ID ( 'cert_name' )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
**'** *cert_name* **'**  

Nom d’un certificat dans la base de données.
  
## <a name="return-types"></a>Types de retour
 **int**  
  
## <a name="remarks"></a>Notes  
La vue de catalogue [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) affiche les noms de certificat.
  
## <a name="permissions"></a>Autorisations  
Nécessite des autorisations sur le certificat, et nécessite que l’appelant ne se soit pas vu refuser l’autorisation VIEW DEFINITION pour le certificat. Pour plus d’informations sur les autorisations de certificat, consultez [CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md#permissions).
  
## <a name="examples"></a>Exemples  
Cet exemple retourne l’ID d’un certificat appelé `ABerglundCert3`.
  
```sql
SELECT Cert_ID('ABerglundCert3');  
GO  
```  
  
## <a name="see-also"></a>Voir aussi
[sys.certificates &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md)  
[CREATE CERTIFICATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)  
[Hiérarchie de chiffrement](../../relational-databases/security/encryption/encryption-hierarchy.md)
  
  
