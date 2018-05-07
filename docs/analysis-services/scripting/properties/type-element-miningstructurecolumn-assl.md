---
title: Type d’élément (MiningStructureColumn) (ASSL) | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Type Element (MiningStructureColumn)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ce999716-9487-4348-bc42-270a2026a452
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ec79db597b6d7b9079e556628f0856e5257cf5d2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="type-element-miningstructurecolumn-assl"></a>Élément Type (MiningStructureColumn) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contient le type de la [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md) élément.  
  
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
|Valeur par défaut|Aucune|  
|Cardinalité|1-1 : élément requis qui apparaît une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 La valeur de cet élément est limitée à l'une des chaînes répertoriées dans le tableau suivant.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*Long*|Entier signé de 64 bits. Ce type de données est mappé à la **Int64** de type de données dans le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] de type .NET Framework et les données DBTYPE_I8 dans OLE DB.|  
|*Booléen*|Valeur booléenne. Ce type de données est mappé à la **booléenne** type de données dans le .NET Framework et le type de données DBTYPE_BOOL dans OLE DB.|  
|*Texte*|Flux de caractères Unicode terminé par le caractère NULL. Ce type de données est mappé à la **chaîne** type de données dans le .NET Framework et le type de données DBTYPE_WSTR dans OLE DB.|  
|*Double*|Nombre à virgule flottante double précision compris dans la plage de -1.79E +308 à 1.79E +308. Ce type de données est mappé à la **Double** type de données dans le .NET Framework et le type de données DBTYPE_R8 dans OLE DB.|  
|*Date*|Données de date, stockées en tant que nombre à virgule flottante double précision. La partie entière correspond au nombre de jours depuis le 30 décembre 1899 tandis que la partie fractionnaire désigne une fraction d'un jour. Ce type de données est mappé à la **DateTime** type de données dans le .NET Framework et le type de données DBTYPE_DATE dans OLE DB.|  
|*Table*|Table imbriquée. Ce type de données est mappé sur le type de données DBTYPE_HCHAPTER dans OLE DB.<br /><br /> Remarque : Les colonnes de Table dans le .NET Framework n’ont pas un type de données intrinsèque équivalent mais sont plutôt pris en charge par le **DataReader** classe.|  
  
 L’énumération qui correspond aux valeurs autorisées pour **Type** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.MiningStructureColumnTypes>.  
  
 L’élément qui correspond au parent de **Type** dans l’objet d’objets AMO (Analysis Management) est modèle <xref:Microsoft.AnalysisServices.MiningStructureColumn>.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés & #40 ; ASSL & #41 ;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
