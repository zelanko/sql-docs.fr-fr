---
title: Nom du classement SQL Server (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], SQL collations
- SQL collations
- names [SQL Server], collations
ms.assetid: 56483d24-add7-483d-9b96-c6fda460ddbc
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fc7265f4efe0d790ab61e4e522af83d6b91b710a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-collation-name-transact-sql"></a>Nom du classement SQL Server (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Chaîne unique spécifiant le nom d'un classement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge les classements Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend également en charge un nombre limité (<80) de classements appelés classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui ont été développés avant que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prenne en charge les classements Windows. Les classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont encore pris en charge à des fins de compatibilité descendante, mais ne doivent pas être utilisés pour les nouveaux travaux de développement. Pour plus d’informations sur les classements Windows, consultez [nom de classement Windows &#40; Transact-SQL &#41; ](../../t-sql/statements/windows-collation-name-transact-sql.md).  
  
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
 Nombre de 1 à 4 chiffres identifiant la page de codes utilisée par le classement. **Cp1** spécifie la page de codes 1252, pour toutes les autres pages de codes le numéro de page de code complet est spécifié. Par exemple, **CP1251** spécifie la page de codes 1251 et **CP850** spécifie la page de codes 850.  
  
 *CaseSensitivity*  
 **L’élément de configuration** spécifie pas la casse, **CS** spécifie la casse.  
  
 *AccentSensitivity*  
 **AI** spécifie les accents, **AS** spécifie les accents.  
  
 **EMPLACEMENT**  
 Indique l'ordre de tri binaire à utiliser.  
  
## <a name="remarks"></a>Notes  
 Pour répertorier les classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pris en charge par votre serveur, exécutez la requête suivante.  
  
```  
SELECT * FROM sys.fn_helpcollations()   
WHERE name LIKE 'SQL%';  
```  

>  [!NOTE]  
>  Pour les trier Order ID 80, utiliser les classements de fenêtre avec la page de codes de 1250 et l’ordre binaire. Par exemple : Albanian_BIN, Croatian_BIN, Czech_BIN, Romanian_BIN, Slovak_BIN, Slovenian_BIN.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [Constantes &#40; Transact-SQL &#41;](../../t-sql/data-types/constants-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [table &#40; Transact-SQL &#41;](../../t-sql/data-types/table-transact-sql.md)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)  
  
  

