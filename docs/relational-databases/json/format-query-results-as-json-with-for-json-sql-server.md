---
title: "Mettre les résultats de requête au format JSON avec FOR JSON (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON
- JSON, exporting
- exporting JSON
ms.assetid: 15b56365-58c2-496c-9d4b-aa2600eab09a
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c439a76e3e925d00e88adaaefa616e59f8529a40
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="format-query-results-as-json-with-for-json-sql-server"></a>Mettre les résultats de requête au format JSON avec FOR JSON (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Mettez les résultats de la requête au format JSON ou exportez les données à partir de SQL Server au format JSON, en ajoutant la clause **FOR JSON** à une instruction **SELECT**. Utilisez la clause **FOR JSON** pour déléguer à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la mise en forme de la sortie JSON produite par les applications clientes.
  
 Lorsque vous utilisez la clause **FOR JSON** , vous pouvez spécifier de manière explicite la structure de la sortie ou laisser la structure de l'instruction SELECT déterminer la sortie.  
  
-   Utilisez le mode **PATH** avec la clause **FOR JSON** pour conserver le contrôle intégral sur le format de la sortie JSON. Vous pouvez créer des objets wrapper et imbriquer des propriétés complexes.  
  
-   Utilisez le mode **AUTO** avec la clause **FOR JSON** pour mettre en forme automatiquement la sortie JSON en fonction de la structure de l’instruction SELECT.  
  
Voici l’exemple d’une instruction **SELECT** avec la clause **FOR JSON** et sa sortie.
  
 ![FOR JSON](../../relational-databases/json/media/jsonslides2forjson.png "FOR JSON")  
  
## <a name="maintain-control-over-json-output-with-path-mode"></a>Conserver le contrôle sur la sortie JSON avec le mode PATH  
En mode **PATH** , vous pouvez utiliser la syntaxe à point (par exemple `'Item.Price'` ) pour mettre en forme la sortie imbriquée. L’exemple suivant utilise également l’option **ROOT** pour spécifier un élément racine nommé.  

Voici un exemple de requête qui utilise le mode **PATH** avec la clause **FOR JSON** .
  
 ![Diagramme de flux de la sortie FOR JSON](../../relational-databases/json/media/forjson-example1.png "Diagramme de flux de la sortie FOR JSON")  

### <a name="more-info"></a>En savoir plus
Pour obtenir plus d’informations et des exemples, consultez [Mettre en forme la sortie JSON imbriquée avec le mode PATH &#40;SQL Server&#41;](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).

Pour plus d’informations sur la syntaxe et l’utilisation, consultez [Clause FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md).  

## <a name="let-the-select-statement-control-json-output-with-auto-mode"></a>Laisser le contrôle à l’instruction SELECT de la sortie JSON avec le mode AUTO  
Dans le mode **AUTO** , la structure de l'instruction SELECT détermine le format de la sortie JSON. Par défaut, les valeurs **Null** ne sont pas incluses dans la sortie. Vous pouvez utiliser **INCLUDE_NULL_VALUES** pour modifier ce comportement.  

Voici un exemple de requête qui utilise le mode **AUTO** avec la clause **FOR JSON** .
 
**Requête :**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO  
```  
  
 **Résultats**  
  
```json  
[{
    "name": "John"
}, {
    "name": "Jane",
    "surname": "Doe"
}]
```  
### <a name="more-info"></a>En savoir plus
Pour obtenir plus d’informations et des exemples, consultez [Mettre en forme automatiquement la sortie JSON avec le mode AUTO &#40;SQL Server&#41;](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).

Pour plus d’informations sur la syntaxe et l’utilisation, consultez [Clause FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md).  
  
## <a name="control-other-json-output-options"></a>Contrôler d’autres options de sortie JSON  
 Contrôlez la sortie de la clause **FOR JSON** à l'aide des options suivantes.  
  
-   Pour ajouter un élément de niveau supérieur unique à la sortie JSON, spécifiez l’option **ROOT** . Si vous ne spécifiez pas l’option **ROOT** , la sortie JSON n'aura pas d’élément racine. Pour plus d’informations, consultez [Ajouter un nœud racine à la sortie JSON avec l’option ROOT &#40;SQL Server&#41;](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md).  
  
-   Pour inclure des valeurs Null dans la sortie JSON, spécifiez l’option **INCLUDE_NULL_VALUES** . Si vous ne spécifiez cette option, la sortie n'inclura pas les propriétés JSON pour les valeurs NULL dans les résultats de la requête. Pour plus d’informations, consultez[Inclure des valeurs Null dans une sortie JSON avec l’option INCLUDE_NULL_VALUES &#40;SQL Server&#41;](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).   

-   Pour supprimer les crochets qui entourent par défaut la sortie JSON de la clause **FOR JSON** , spécifiez l’option **WITHOUT_ARRAY_WRAPPER** . Utilisez cette option pour générer un seul objet JSON en sortie. Si vous ne spécifiez pas cette option, la sortie JSON sera placée entre crochets. Pour plus d’informations, consultez [Supprimer les crochets de la sortie JSON avec l’option WITHOUT_ARRAY_WRAPPER &#40;SQL Server&#41;](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md). 
   
## <a name="output-of-the-for-json-clause"></a>Sortie de la clause FOR JSON  
 La sortie de la clause **FOR JSON** présente les caractéristiques suivantes.  
  
1.  Le jeu de résultats contient une seule colonne. Un jeu de résultats de petite taille peut ne contenir qu’une seule ligne. Un grand jeu de résultats contient plusieurs lignes.  
  
     ![Exemple de sortie FOR JSON](../../relational-databases/json/media/forjson-example2.png "Exemple de sortie FOR JSON")  
  
2.  Les résultats sont présentés sous forme de tableau d'objets JSON.  
  
    -   Le nombre d'éléments du tableau est égal au nombre de lignes dans les résultats.  
  
    -   Chaque ligne du jeu de résultats devient un objet JSON distinct dans le tableau.  
  
    -   Chaque colonne du jeu de résultats devient une propriété de l'objet JSON.  
  
3.  Le nom et la valeur des colonnes sont échappés selon la syntaxe JSON. Pour plus d’informations, consultez [Comment FOR JSON place dans une séquence d’échappement les caractères spéciaux et les caractères de contrôle &#40;SQL Server&#41;](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md).
  
 Voici un exemple illustrant la mise en forme de la sortie JSON.  
  
 **Résultats de la requête**  
  
|||||  
|-|-|-|-|  
|**Objet**|**B**|**C**|**D**|  
|10|11|12|X|  
|20|21|22|O|  
|30|31|32|Z|  
  
 **Sortie JSON**  
  
```json  
[{
    "A": 10,
    "B": 11,
    "C": 12,
    "D": "X"
}, {
    "A": 20,
    "B": 21,
    "C": 22,
    "D": "Y"
}, {
    "A": 30,
    "B": 31,
    "C": 32,
    "D": "Z"
}] 
```  
 Pour obtenir plus d’informations sur ce que vous voyez dans la sortie de la clause **FOR JSON**, consultez les rubriques suivantes.  
-   [Conversion par FOR JSON des types de données SQL Server en types de données JSON &#40;SQL Server&#41;](../../relational-databases/json/how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server.md)  
La clause **FOR JSON** utilise les règles décrites dans cette rubrique pour convertir les types de données SQL en types JSON dans la sortie JSON.  

-   [Comment FOR JSON place dans une séquence d’échappement les caractères spéciaux et les caractères de contrôle &#40;SQL Server&#41;](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md)  
 La clause **FOR JSON** échappe les caractères spéciaux et représente les caractères de contrôle dans la sortie JSON comme le décrit cette rubrique.  

## <a name="learn-more-about-for-json-and-built-in-json-support-in-sql-server"></a>En savoir plus sur FOR JSON et la prise en charge JSON intégrée dans SQL Server  
 [Billets de blog de Jovan Popovic, gestionnaire de programmes Microsoft](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## <a name="see-also"></a>Voir aussi  
 [Clause FOR &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)   
 [Utiliser la sortie de FOR JSON dans SQL Server et les applications clientes &#40;SQL Server&#41;](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)  
  
  

