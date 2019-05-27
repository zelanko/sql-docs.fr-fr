---
title: CURRENT_REQUEST_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CURRENT_REQUEST_ID_TSQL
- CURRENT_REQUEST_ID
dev_langs:
- TSQL
helpviewer_keywords:
- CURRENT_REQUEST_ID
ms.assetid: 949f6e5f-bf5f-49d6-a763-c443d1d51fe2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3efa9db81b9079f35cafb245dc10f3437c5c445d
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65944606"
---
# <a name="currentrequestid-transact-sql"></a>CURRENT_REQUEST_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Cette fonction retourne l'ID de la demande actuelle dans la session en cours.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CURRENT_REQUEST_ID()  
```  
  
## <a name="return-types"></a>Types de retour
**smallint**
  
## <a name="remarks"></a>Notes   
Pour rechercher des informations exactes sur la session active, utilisez @@SPID. Pour obtenir des informations exactes sur la requête actuelle, utilisez CURRENT_REQUEST_ID().
  
## <a name="see-also"></a>Voir aussi
[@@SPID &#40;Transact-SQL&#41;](../../t-sql/functions/spid-transact-sql.md)
  
  
