---
title: STRING_SPLIT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
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
- STRING_SPLIT
- STRING_SPLIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_SPLIT function
ms.assetid: 3273dbf3-0b4f-41e1-b97e-b4f67ad370b9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 00debf90f1b79a0e38cb883f31479ae5731f40d3
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="stringsplit-transact-sql"></a>STRING_SPLIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Fractionne l’expression de caractères à l’aide du séparateur spécifié.  
  
> [!NOTE]  
>  Le **STRING_SPLIT** fonction est disponible uniquement au niveau de compatibilité 130. Si votre niveau de compatibilité de base de données est inférieur à 130, SQL Server ne sera pas en mesure de rechercher et exécuter **STRING_SPLIT** (fonction). Vous pouvez modifier un niveau de compatibilité de base de données à l’aide de la commande suivante :  
> ALTER DATABASE nom_base_de_données SET COMPATIBILITY_LEVEL = 130  
>   
>  Notez que le niveau de compatibilité 120 peut être la valeur par défaut même dans les nouvelles bases de données de SQL Azure.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STRING_SPLIT ( string , separator )  
```  
  
## <a name="arguments"></a>Arguments  
 *chaîne*  
 Est un [expression](../../t-sql/language-elements/expressions-transact-sql.md) de n’importe quel type de caractère (c'est-à-dire **nvarchar**, **varchar**, **nchar** ou **char**).  
  
 *separator*  
 Est un caractère unique [expression](../../t-sql/language-elements/expressions-transact-sql.md) de n’importe quel type de caractère (par exemple, **nvarchar(1)**, **varchar (1)**, **nchar (1)** ou **char (1)**) qui est utilisé comme séparateur pour les chaînes concaténées.  
  
## <a name="return-types"></a>Types de retour  
 Retourne une table d’une seule colonne avec des fragments. Le nom de la colonne est **valeur**. Retourne **nvarchar** si un des arguments d’entrée sont **nvarchar** ou **nchar**. Sinon, retourne **varchar**. La longueur du type de retour est identique à la longueur de l’argument de chaîne.  
  
## <a name="remarks"></a>Notes  
 **STRING_SPLIT** prend une chaîne qui doit être divisée et le séparateur qui sera utilisé pour diviser la chaîne. Il retourne une table d’une seule colonne avec les sous-chaînes. Par exemple, l’instruction suivante `SELECT value FROM STRING_SPLIT('Lorem ipsum dolor sit amet.', ' ');` à l’aide de l’espace comme séparateur de retourne tableau de résultats suivant :  
  
|valeur|  
|-----------|  
|Lorem|  
|ipsum|  
|dolor|  
|sit|  
|Amet.|  
  
 Si la chaîne d’entrée est **NULL**, le **STRING_SPLIT** fonction table retourne une table vide.  
  
 **STRING_SPLIT** requiert au moins le mode de compatibilité 130.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-split-comma-separated-value-string"></a>A. Chaîne de valeur séparées par des virgules de fractionnement  
 L’analyse d’une liste séparée par des virgules de valeurs et retourner tous les jetons non vide :  
  
```  
  
DECLARE @tags NVARCHAR(400) = 'clothing,road,,touring,bike'  
  
SELECT value  
FROM STRING_SPLIT(@tags, ',')  
WHERE RTRIM(value) <> '';  
  
```  
  
 STRING_SPLIT retourne une chaîne vide si aucun élément n’entre le séparateur. Condition RTRIM(value) <> '' supprimera les jetons vides.  
  
### <a name="b-split-comma-separated-value-string-in-a-column"></a>B. Chaîne de valeur dans une colonne séparés par des virgules de fractionnement  
 Table Product a une colonne avec une liste séparée de virgules de balises indiqué dans l’exemple suivant :  
  
|productId|Nom|Balises|  
|---------------|----------|----------|  
|1|À un doigt intégral gants|vêtements, route, touring, bike|  
|2|LL casque|bike|  
|3|HL Mountain Frame|vélo, mountain|  
  
 Requête suivante transforme chaque liste de balises et les joint avec la ligne d’origine :  
  
```  
SELECT ProductId, Name, value  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|productId|Nom|valeur|  
|---------------|----------|-----------|  
|1|À un doigt intégral gants|habillement|  
|1|À un doigt intégral gants|feuille de route|  
|1|À un doigt intégral gants|Touring|  
|1|À un doigt intégral gants|bike|  
|2|LL casque|bike|  
|3|HL Mountain Frame|bike|  
|3|HL Mountain Frame|Mountain|  
  
### <a name="c-aggregation-by-values"></a>C. Agrégation de valeurs  
 Les utilisateurs doivent créer un rapport qui indique le nombre de produits par chaque balise, classés par nombre de produits et pour filtrer uniquement les balises avec plus de 2 produits.  
  
```  
SELECT value as tag, COUNT(*) AS [Number of articles]  
FROM Product  
    CROSS APPLY STRING_SPLIT(Tags, ',')  
GROUP BY value  
HAVING COUNT(*) > 2  
ORDER BY COUNT(*) DESC;  
```  
  
### <a name="d-search-by-tag-value"></a>D. Effectuer une recherche par la valeur de balise  
 Les développeurs doivent créer des requêtes de recherche d’articles par mots clés. Ils peuvent utiliser à la suite de requêtes :  
  
 Pour rechercher les produits avec une seule balise (vêtements) :  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE 'clothing' IN (SELECT value FROM STRING_SPLIT(Tags, ','));  
```  
  
 Rechercher les produits avec deux balises spécifiées (vêtements et route) :  
  
```  
  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE EXISTS (SELECT *  
    FROM STRING_SPLIT(Tags, ',')  
    WHERE value IN ('clothing', 'road');  
```  
  
### <a name="e-find-rows-by-list-of-values"></a>E. Rechercher des lignes par liste de valeurs  
 Les développeurs doivent créer une requête qui recherche des articles d’une liste d’identificateurs. Ils peuvent utiliser de requête suivante :  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
JOIN STRING_SPLIT('1,2,3',',')   
    ON value = ProductId;  
```  
  
 Voici un remplacement pour anti-modèle courantes telles que la création d’une chaîne SQL dynamique dans la couche d’application ou [!INCLUDE[tsql](../../includes/tsql-md.md)], ou à l’aide de LIKE (opérateur) :  
  
```  
SELECT ProductId, Name, Tags  
FROM Product  
WHERE ',1,2,3,' LIKE '%,' + CAST(ProductId AS VARCHAR(20)) + ',%';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)  
 [LTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/ltrim-transact-sql.md)  
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
 [TRIM &#40;Transact-SQL&#41;](../../t-sql/functions/trim-transact-sql.md)  
 [Fonctions de chaîne &#40; Transact-SQL &#41;](../../t-sql/functions/string-functions-transact-sql.md)   
  
  
