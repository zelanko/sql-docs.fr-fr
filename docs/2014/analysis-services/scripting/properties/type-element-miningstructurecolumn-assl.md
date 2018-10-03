---
title: Type d’élément (MiningStructureColumn) (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element (MiningStructureColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ce999716-9487-4348-bc42-270a2026a452
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ea27ce8418922be1e92200aa3426b280fac76ace
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48148609"
---
# <a name="type-element-miningstructurecolumn-assl"></a>Élément Type (MiningStructureColumn) (ASSL)
  Contient le type de la [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) élément.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<MiningStructureColumn>  
   ...  
   <Type>...</Type>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|None|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Long*|Entier signé de 64 bits. Ce type de données est mappé à la `Int64` type de données dans le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] type de .NET Framework et les données DBTYPE_I8 dans OLE DB.|  
|*Booléen*|Valeur booléenne. Ce type de données est mappé sur le type de données `Boolean` dans .NET Framework et sur le type de données DBTYPE_BOOL dans OLE DB.|  
|*Texte*|Flux de caractères Unicode terminé par le caractère NULL. Ce type de données est mappé sur le type de données `String` dans .NET Framework et sur le type de données DBTYPE_WSTR dans OLE DB.|  
|*Double*|Nombre à virgule flottante double précision compris dans la plage de -1.79E +308 à 1.79E +308. Ce type de données est mappé sur le type de données `Double` dans .NET Framework et sur le type de données DBTYPE_R8 dans OLE DB.|  
|*Date*|Données de date, stockées en tant que nombre à virgule flottante double précision. La partie entière correspond au nombre de jours depuis le 30 décembre 1899 tandis que la partie fractionnaire désigne une fraction d'un jour. Ce type de données est mappé sur le type de données `DateTime` dans .NET Framework et sur le type de données DBTYPE_DATE dans OLE DB.|  
|*Table*|Table imbriquée. Ce type de données est mappé sur le type de données DBTYPE_HCHAPTER dans OLE DB. **Remarque :** des colonnes de Table dans le .NET Framework n’ont pas un type de données intrinsèque équivalent, mais au lieu de cela prend en charge la `DataReader` classe.|  
  
 L’énumération qui correspond aux valeurs autorisées pour `Type` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.MiningStructureColumnTypes>.  
  
 L’élément qui correspond au parent de `Type` dans l’objet d’objets AMO (Analysis Management) modèle est <xref:Microsoft.AnalysisServices.MiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
