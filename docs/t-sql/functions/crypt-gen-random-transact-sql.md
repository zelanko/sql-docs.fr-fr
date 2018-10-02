---
title: CRYPT_GEN_RANDOM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CRYPT_GEN_RANDOM_TSQL
- CRYPT_GEN_RANDOM
dev_langs:
- TSQL
helpviewer_keywords:
- CRYPT_GEN_RANDOM function
ms.assetid: b74bd9d4-758e-4b94-89a0-76dcda6d8c42
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7fa0beb2e7b920e24e77ce9fbb498f7386f57847
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850047"
---
# <a name="cryptgenrandom-transact-sql"></a>CRYPT_GEN_RANDOM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Cette fonction retourne un nombre aléatoire de chiffrement généré par l'API Crypto (CAPI). `CRYPT_GEN_RANDOM` retourne un nombre hexadécimal avec une longueur d’un nombre spécifié d’octets.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
CRYPT_GEN_RANDOM ( length [ , seed ] )   
```  
  
## <a name="arguments"></a>Arguments  
*length*  
La longueur, en octets, du nombre que `CRYPT_GEN_RANDOM` va créer. L’argument *length* comporte un type de données **int** et une plage de valeurs comprises entre 1 et 8000. `CRYPT_GEN_RANDOM` retourne la valeur NULL pour une valeur **int** en dehors de cette plage. 
  
*seed*  
Un nombre hexadécimal facultatif à utiliser comme valeur de départ aléatoire. La longueur de la valeur *seed* doit correspondre à la valeur de l’argument *length*. L’argument *seed* comporte un type de données **varbinary(8000)**.
  
## <a name="returned-types"></a>Types retournés  
**varbinary(8000)**
  
## <a name="permissions"></a>Permissions  
Cette fonction est publique et ne requiert pas d'autorisation spéciale.
  
## <a name="examples"></a>Exemples  
  
### <a name="a-generating-a-random-number"></a>A. Génération d'un nombre aléatoire  
Cet exemple génère un nombre aléatoire d’une longueur de 50 octets :
  
```sql
SELECT CRYPT_GEN_RANDOM(50) ;  
```  
  
Cet exemple génère un nombre aléatoire d'une longueur de 4 octets à l'aide d'une valeur de départ de 4 octets :
  
```sql
SELECT CRYPT_GEN_RANDOM(4, 0x25F18060) ;  
```  
  
## <a name="see-also"></a>Voir aussi
[RAND &#40;Transact-SQL&#41;](../../t-sql/functions/rand-transact-sql.md)
  
  
