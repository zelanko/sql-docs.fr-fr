---
title: Commande COLLATIONPROPERTY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 10/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f47c45f892618120b06a17f45f5d3155e092987a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="collation-functions---collationproperty-transact-sql"></a>Fonctions de classement - commande COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Retourne la propriété d'un classement spécifié dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>Arguments  
*collation_name*  
Est le nom du classement. *collation_name* est **nvarchar (128)**, sans valeur par défaut.
  
*propriété*  
Propriété du classement. *propriété* est **varchar (128)**, et peut prendre l’une des valeurs suivantes :
  
|Nom de la propriété| Description|  
|---|---|
|**CodePage**|Page de codes non-Unicode du classement. Consultez [annexe G DBCS/Unicode mappage des Tables](https://msdn.microsoft.com/en-us/library/cc194886.aspx) et [Pages de codes annexe H](https://msdn.microsoft.com/en-us/library/cc195051.aspx) pour convertir ces valeurs et voir leurs mappages de caractères.|  
|**LCID**|Indicateur LCID Windows du classement. Consultez [LCID Structure](https://msdn.microsoft.com/en-us/library/cc233968.aspx) pour convertir ces valeurs (vous devrez convertir **varbinary** premier).|  
|**ComparisonStyle**|Style de comparaison Windows du classement. Retourne 0 pour tous les classements binaires, à la fois (\_BIN) et (\_BIN2), ainsi que lorsque toutes les propriétés sont sensibles. Valeurs de masque de bits :<br /><br /> Ignorer la casse : 1<br /><br /> Ignorer les accents : 2<br /><br /> Ignorer les caractères Kana : 65536<br /><br /> Ignorer la largeur : 131072<br /><br /> Remarque : Même si elle affecte le comportement de comparaison, la variante sélecteur-sensible (\_VSS) option n’est pas représentée dans cette valeur.|  
|**Version**|Version du classement, dérivée du champ de version de l'ID du classement. Retourne une valeur entière comprise entre 0 et 3.<br /><br /> Classements avec « 140 » dans le nom de retour 3.<br /><br /> Classements avec le nom « 100 » retournent 2.<br /><br /> Classements avec le nom « 90 » retournent 1.<br /><br /> Tous les autres classements retournent 0.|  
  
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
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>Voir aussi
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  

