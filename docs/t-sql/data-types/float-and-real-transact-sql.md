---
title: float et real (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- float
- real_TSQL
- real
- float_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- numeric data type, floating point
- float data type
- floating point data [SQL Server]
- real data type
ms.assetid: 08ea66b7-624e-4d8b-86bc-750ff76cdfc5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5f955e5d367a17602959f5294f9fb5d393b186b5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="float-and-real-transact-sql"></a>float et real (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Types de données approximatives à utiliser avec des données numériques à virgule flottante. Les données à virgule flottante sont approximatives ; il n'est donc pas possible de représenter précisément toutes les valeurs de ce type de données. Le synonyme ISO de **real** est **float(24)**.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
**float** [ **(***n***)** ] Où *n* est le nombre de bits utilisés pour stocker la mantisse du nombre de type **float** en notation scientifique et indique par conséquent le niveau de précision et la taille de stockage. Si *n* est spécifié, sa valeur doit être comprise entre **1** et **53**. La valeur par défaut de *n* est **53**.
  
|Valeur *n*|Précision|Taille de stockage|  
|---|---|---|
|**1-24**|7 chiffres|4 octets|  
|**25-53**|15 chiffres|8 octets|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] traite *n* comme l’une de deux valeurs possibles. Si **1**<=n<=**24**, *n* est considéré comme égal à **24**. Si **25**<=n<=**53**, *n* est considéré comme égal à **53**.  
  
Le type de données **float**[**(n)**] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est conforme à la norme ISO pour toutes les valeurs de *n* comprises entre **1** et **53**. Le synonyme de **double precision** est **float(53)**.
  
## <a name="remarks"></a>Notes   
  
|Type de données|Plage|Stockage|  
|---|---|---|
|**float**|- 1,79E+308 à -2,23E-308, 0 et 2,23E-308 à 1,79E+308|Dépend de la valeur de *n*|  
|**real**|- 3,40E + 38 à -1,18E - 38, 0 et 1,18E - 38 à 3,40E + 38|Quatre octets|  
  
##  <a name="converting-float-and-real-data"></a>Conversion de données float et real  
Les valeurs de **float** sont tronquées quand elles sont converties en un type entier.
  
Si vous souhaitez effectuer une conversion de **float** ou **real** en données caractères, la fonction de chaîne STR constitue généralement un meilleur choix que CAST( ), car STR permet un plus grand contrôle sur le format. Pour plus d’informations, consultez [STR &#40;Transact-SQL&#41;](../../t-sql/functions/str-transact-sql.md) et [Fonctions &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md).
  
La conversion des valeurs **float** qui utilisent la notation scientifique en **decimal** ou en **numeric** est limitée à des valeurs d’une précision de 17 chiffres uniquement. N’importe quelle valeur < 5E-18 est arrondie à 0.
  
## <a name="see-also"></a>Voir aussi
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Conversion de type de données &#40;moteur de base de données&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
