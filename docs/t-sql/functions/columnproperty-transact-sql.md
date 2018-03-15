---
title: COLUMNPROPERTY (Transact-SQL) | Microsoft Docs
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
- COLUMNPROPERTY
- COLUMNPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- column properties [SQL Server]
- parameters [SQL Server], properties
- COLUMNPROPERTY function
ms.assetid: 2408c264-6eca-4120-bb71-df043c7c2792
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 61ac858e029848ef59978669112de3db7c068f67
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="columnproperty-transact-sql"></a>COLUMNPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Renvoie des informations sur une colonne ou un paramètre.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
COLUMNPROPERTY ( id , column , property )   
```  
  
## <a name="arguments"></a>Arguments  
*id*  
[Expression](../../t-sql/language-elements/expressions-transact-sql.md) contenant l’identificateur (ID) de la table ou de la procédure.
  
*column*  
Expression contenant le nom de la colonne ou du paramètre.
  
*property*  
Expression contenant les informations à retourner pour *id* et pouvant prendre l’une des valeurs suivantes.
  
|Valeur|Description|Valeur retournée|  
|---|---|---|
|**AllowsNull**|Autorise les valeurs NULL|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide.|  
|**ColumnId**|Valeur d’identificateur de colonne correspondant à **sys.columns.column_id**.|ID de la colonne<br /><br /> **Remarque :** Lors de requêtes sur plusieurs colonnes, des écarts peuvent apparaître dans l’ordre des valeurs d’identificateur de colonne.|  
|**FullTextTypeColumn**|TYPE COLUMN de la table qui contient les informations sur le type de document de la *colonne*.|Identificateur de TYPE COLUMN en texte intégral pour la colonne passée en tant que second paramètre de cette propriété.|  
|**IsComputed**|Est une colonne calculée.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide.|  
|**IsCursorType**|Le paramètre de la procédure est de type CURSOR.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide.|  
|**IsDeterministic**|La colonne est déterministe. Cette propriété s'applique uniquement aux colonnes calculées et aux colonnes de la vue.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide. Aucune colonne calculée ou colonne de la vue.|  
|**IsFulltextIndexed**|Colonne enregistrée pour l'indexation de texte intégral.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide.|  
|**IsIdentity**|La colonne utilise la propriété IDENTITY.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide.|  
|**IsIdNotForRepl**|La colonne vérifie le paramètre IDENTITY_INSERT.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide.|  
|**IsIndexable**|La colonne peut être indexée.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide.|  
|**IsOutParam**|Le paramètre de la procédure est un paramètre de sortie.|1 = TRUE<br /><br /> 0 = FALSE NULL = Entrée non valide.|  
|**IsPrecise**|La colonne est précise. Cette propriété s'applique uniquement aux colonnes déterministes.|1 = TRUE<br /><br /> 0 = FALSE NULL = Entrée non valide. Colonne non déterministe.|  
|**IsRowGuidCol**|La colonne a le type de données **uniqueidentifier** et est définie à l’aide de la propriété ROWGUIDCOL.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide.|  
|**IsSystemVerified**|Les propriétés de déterminisme et de précision de la colonne peuvent être vérifiées par le [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Cette propriété s'applique uniquement aux colonnes calculées et aux colonnes de vues.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide.|  
|**IsXmlIndexable**|La colonne XML peut être utilisée dans un index XML.|1 = TRUE<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide.|  
|**Précision**|Longueur du type de données de la colonne ou du paramètre.|Longueur du type de données de la colonne spécifiée.<br /><br /> -1 = **xml** ou types de valeur de grande taille<br /><br /> NULL = Entrée non valide.|  
|**Échelle**|Échelle pour le type de données de la colonne ou du paramètre.|L’échelle<br /><br /> NULL = Entrée non valide.|  
|**StatisticalSemantics**|La colonne est activée en vue de l'indexation sémantique.|1 = TRUE<br /><br /> 0 = FALSE|  
|**SystemDataAccess**|La colonne est dérivée d'une fonction qui accède aux données dans les catalogues système ou les tables système virtuelles de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette propriété s'applique uniquement aux colonnes calculées et aux colonnes de vues.|1 = TRUE (indique un accès en lecture seule)<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide.|  
|**UserDataAccess**|La colonne est dérivée d'une fonction qui accède aux données dans les tables utilisateur, y compris les vues et les tables temporaires, stockées dans l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette propriété s'applique uniquement aux colonnes calculées et aux colonnes de vues.|1 = TRUE (indique un accès en lecture seule)<br /><br /> 0 = FALSE<br /><br /> NULL = Entrée non valide.|  
|**UsesAnsiTrim**|ANSI_PADDING avait pour valeur ON lors de la création de la table. Cette propriété ne s’applique qu’aux colonnes ou paramètres de type **char** ou **varchar**.|1 = TRUE<br /><br /> 0= FALSE<br /><br /> NULL = Entrée non valide.|  
|**IsSparse**|La colonne est éparse. Pour plus d’informations, consultez [Utiliser des colonnes éparses](../../relational-databases/tables/use-sparse-columns.md).|1 = TRUE<br /><br /> 0= FALSE<br /><br /> NULL = Entrée non valide.|  
|**IsColumnSet**|La colonne est un jeu de colonnes. Pour plus d’informations, consultez [Utiliser des jeux de colonnes](../../relational-databases/tables/use-column-sets.md).|1 = TRUE<br /><br /> 0= FALSE<br /><br /> NULL = Entrée non valide.|  
|**GeneratedAlwaysType**|Valeur de colonne générée par le système. Correspond à **sys.columns.generated_always_type**|**S'applique à**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 0 = Pas toujours générée<br /><br /> 1 = Toujours générée comme début de ligne<br /><br /> 2 = Toujours générée comme fin de ligne|  
|**IsHidden**|Valeur de colonne générée par le système. Correspond à **sys.columns.is_hidden**|**S'applique à**: [!INCLUDE[ssCurrentLong](../../includes/sscurrentlong-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 0 = Non masquée<br /><br /> 1 = Masquée|  
  
## <a name="return-types"></a>Types de retour
 **Int**  
  
## <a name="exceptions"></a>Exceptions  
Retourne la valeur NULL en cas d'erreur ou si un appelant n'est pas autorisé à afficher l'objet.
  
Un utilisateur peut voir uniquement les métadonnées des éléments sécurisables qui lui appartiennent ou pour lesquels il dispose d'une autorisation. Cela signifie que les fonctions intégrées générant des métadonnées, telles que COLUMNPROPERTY, peuvent retourner la valeur NULL si l'utilisateur ne dispose d'aucune autorisation sur l'objet. Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).
  
## <a name="remarks"></a>Notes   
Lorsque vous vérifiez la propriété déterministe d'une colonne, assurez-vous d'abord que la colonne est calculée. **IsDeterministic** retourne la valeur NULL pour les colonnes non calculées. Les colonnes calculées peuvent être spécifiées sous la forme de colonnes d'index.
  
## <a name="examples"></a>Exemples  
L'exemple suivant renvoie la longueur de la colonne `LastName`.
  
```sql
USE AdventureWorks2012;  
GO  
SELECT COLUMNPROPERTY( OBJECT_ID('Person.Person'),'LastName','PRECISION')AS 'Column Length';  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Column Length
-------------
50
```  
  
## <a name="see-also"></a>Voir aussi
[Fonctions de métadonnées &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)  
[TYPEPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/typeproperty-transact-sql.md)
  
  
