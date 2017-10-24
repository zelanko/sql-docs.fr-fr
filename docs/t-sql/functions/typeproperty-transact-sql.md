---
title: TYPEPROPERTY (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TYPEPROPERTY
- TYPEPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server], data types
- data types [SQL Server], status information
- TYPEPROPERTY function
ms.assetid: bc311c80-bac5-46ab-a5c8-68b1c6bbf24a
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: 8608de51a13d2bc0109b9874b30749b10b65eaea
ms.contentlocale: fr-fr
ms.lasthandoff: 10/24/2017

---
# <a name="typeproperty-transact-sql"></a>TYPEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Renvoie des informations sur un type de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
TYPEPROPERTY (type , property)  
```  
  
## <a name="arguments"></a>Arguments  
 *type*  
 Est le nom du type de données.  
  
 *propriété*  
 Type d'informations à renvoyer pour le type de données. *propriété* peut prendre l’une des valeurs suivantes.  
  
|Propriété| Description|Valeur retournée|  
|--------------|-----------------|--------------------|  
|**AllowsNull**|Type de données autorisant les valeurs NULL.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Type de données introuvable.|  
|**OwnerId**|Propriétaire du type.<br /><br /> Remarque : Le propriétaire du schéma n’est pas nécessairement le propriétaire du type.|Non NULL = ID utilisateur de base de données du propriétaire du type.<br /><br /> NULL = Type non pris en charge, ou ID de type non valide.|  
|**Précision**|Précision du type de données.|Nombre de chiffres ou de caractères.<br /><br /> -1 = **xml** ou type de données de valeur élevée<br /><br /> NULL = Type de données introuvable.|  
|**Échelle**|Échelle du type de données.|Nombre de décimales pour le type de données.<br /><br /> NULL = type de données non **numérique** ou introuvable.|  
|**UsesAnsiTrim**|Le paramètre de remplissage ANSI était activé lors de la création du type de données.|1 = True<br /><br /> 0 = False<br /><br /> NULL = Type de données introuvable ou différent d'un type de données binaire ou chaîne.|  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
## <a name="exceptions"></a>Exceptions  
 Retourne la valeur NULL en cas d'erreur ou si un appelant n'est pas autorisé à afficher l'objet.  
  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un utilisateur peut voir uniquement les métadonnées des éléments sécurisables qui lui appartiennent ou pour lesquels il dispose d'un droit d'accès. Cela signifie que les fonctions intégrées générant des métadonnées, telles que TYPEPROPERTY, peuvent retourner la valeur NULL si l'utilisateur ne dispose d'aucune autorisation sur l'objet. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-identifying-the-owner-of-a-data-type"></a>A. Identification du propriétaire d'un type de données  
 L'exemple suivant retourne le propriétaire d'un type de données.  
  
```  
SELECT TYPEPROPERTY(SCHEMA_NAME(schema_id) + '.' + name, 'OwnerId') AS owner_id, name, system_type_id, user_type_id, schema_id  
FROM sys.types;  
```  
  
### <a name="b-returning-the-precision-of-the-tinyint-data-type"></a>B. Renvoi de la précision du type de données tinyint  
 L'exemple suivant renvoie la précision ou le nombre de chiffres pour le type de données `tinyint`.  
  
```  
SELECT TYPEPROPERTY( 'tinyint', 'PRECISION');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [TYPE_ID &#40; Transact-SQL &#41;](../../t-sql/functions/type-id-transact-sql.md)   
 [TYPE_NAME &#40; Transact-SQL &#41;](../../t-sql/functions/type-name-transact-sql.md)   
 [COLUMNPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/columnproperty-transact-sql.md)   
 [Fonctions de métadonnées &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [Sys.types &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)  
  
  


