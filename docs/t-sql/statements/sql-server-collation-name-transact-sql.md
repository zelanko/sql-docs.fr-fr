---
title: Nom du classement SQL Server (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], SQL collations
- SQL collations
- names [SQL Server], collations
ms.assetid: 56483d24-add7-483d-9b96-c6fda460ddbc
caps.latest.revision: 30
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: a59461aa29a524d5d92681bbd1f76889e4239fca
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39451963"
---
# <a name="sql-server-collation-name-transact-sql"></a>Nom du classement SQL Server (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Chaîne unique spécifiant le nom d'un classement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge les classements Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend également en charge un nombre limité (<80) de classements appelés classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui ont été développés avant que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prenne en charge les classements Windows. Les classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont encore pris en charge à des fins de compatibilité descendante, mais ne doivent pas être utilisés pour les nouveaux travaux de développement. Pour plus d’informations sur le classement Windows, consultez [Nom de classement Windows &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<SQL_collation_name> :: =   
SQL_SortRules[_Pref]_CPCodepage_<ComparisonStyle>  
  
<ComparisonStyle> ::=  
_CaseSensitivity_AccentSensitivity | _BIN  
```  
  
## <a name="arguments"></a>Arguments  
 *SortRules*  
 Chaîne identifiant l'alphabet ou la langue dont les règles de tri sont appliquées lorsque le tri du dictionnaire est spécifié. Exemples : Latin1_General ou Polonais.  
  
 **Pref**  
 Préférence pour les caractères majuscules. Même si la comparaison ne respecte pas la casse, la version majuscule d'une lettre est triée avant la version minuscule lorsqu'il n'y a aucune autre distinction.  
  
 *Codepage*  
 Nombre de 1 à 4 chiffres identifiant la page de codes utilisée par le classement. **CP1** indique la page de codes 1252. Le numéro de page de codes complet est indiqué pour toutes les autres pages de codes. Par exemple, **CP1251** correspond à la page de codes 1251 et **CP850** correspond à la page de codes 850.  
  
 *CaseSensitivity*  
 **CI** ne respecte pas la casse, contrairement à **CS**.  
  
 *AccentSensitivity*  
 **AI** ne respecte pas les accents, contrairement à **AS**.  
  
 **BIN**  
 Indique l'ordre de tri binaire à utiliser.  
  
## <a name="remarks"></a>Notes   
 Pour répertorier les classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pris en charge par votre serveur, exécutez la requête suivante.  
  
```  
SELECT * FROM sys.fn_helpcollations()   
WHERE name LIKE 'SQL%';  
```  

>  [!NOTE]  
>  Pour l’ordre de tri 80, utilisez n’importe quel classement Windows comportant la page de codes 1250 et l’ordre binaire. Par exemple : Albanian_BIN, Croatian_BIN, Czech_BIN, Romanian_BIN, Slovak_BIN, Slovenian_BIN.  
  
## <a name="see-also"></a> Voir aussi  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [Constantes &#40;Transact-SQL&#41;](../../t-sql/data-types/constants-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-transact-sql.md?&tabs=sqlserver)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [table &#40;Transact-SQL&#41;](../../t-sql/data-types/table-transact-sql.md)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)  
  
  
