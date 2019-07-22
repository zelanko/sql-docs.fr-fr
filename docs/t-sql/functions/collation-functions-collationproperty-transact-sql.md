---
title: COLLATIONPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COLLATIONPROPERTY_TSQL
- COLLATIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], properties
- COLLATIONPROPERTY function
ms.assetid: f5029e74-a1db-4f69-b0f5-5ee920c3311d
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 842c70125c5d311f36df50afa72feae47c47bd55
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064712"
---
# <a name="collation-functions---collationproperty-transact-sql"></a>Fonctions de classement - COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Cette fonction retourne la propriété demandée d’un classement spécifié.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>Arguments  
*collation_name*  
Nom du classement. L’argument *collation_name* a un type de données **nvarchar(128)** , sans valeur par défaut.
  
*property*  
Propriété du classement. L’argument *property* a un type de données **varchar(128)** et peut avoir une des valeurs suivantes :
  
|Nom de la propriété|Description|  
|---|---|
|**CodePage**|Page de codes non-Unicode du classement. Il s’agit du jeu de caractères utilisé pour les données **varchar**. Consultez [Annexe G – Tables de mappage DBCS/Unicode](https://msdn.microsoft.com/library/cc194886.aspx) et [Annexe H – Pages de code](https://msdn.microsoft.com/library/cc195051.aspx) pour convertir ces valeurs et voir leurs mappages de caractères.<br /><br />Type de données de base : **int**|  
|**LCID**|ID des paramètres régionaux Windows. Il s’agit de la culture utilisée pour les règles de tri et de comparaison. Consultez [Structure LCID](https://msdn.microsoft.com/library/cc233968.aspx) pour convertir ces valeurs (vous devrez commencer par les convertir en **varbinary**).<br /><br />Type de données de base : **int**|  
|**ComparisonStyle**|Style de comparaison Windows du classement. Retourne 0 pour les classements binaires - à la fois (\_BIN) et (\_BIN2) - ainsi que quand toutes les propriétés respectent les caractères (\_CS\_AS\_KS\_WS) et (\_CS\_AS\_KS\_WS\_SC) et (\_CS\_AS\_KS\_WS\_VSS). Valeurs de masque de bits :<br /><br /> Ignorer la casse : 1<br /><br /> Ignorer les accents : 2<br /><br /> Ignorer le type de caractères Kana : 65536<br /><br /> Ignorer la largeur : 131072<br /><br /> Remarque : L’option de sélecteur de variante (\_VSS) n’est pas représentée dans cette valeur, même si elle affecte le comportement de la comparaison.<br /><br />Type de données de base : **int**|  
|**Version**|Version du classement. Retourne une valeur comprise entre 0 et 3.<br /><br /> Les classements dont le nom contient « 140 » retournent 3.<br /><br /> Les classements dont le nom contient « 100 » retournent 2.<br /><br /> Les classements dont le nom contient « 90 » retournent 1.<br /><br /> Tous les autres classements retournent 0.<br /><br />Type de données de base : **tinyint**|  
  
## <a name="return-types"></a>Types de retour
**sql_variant**
  
## <a name="examples"></a>Exemples  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>Voir aussi
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  

