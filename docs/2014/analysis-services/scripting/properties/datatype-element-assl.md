---
title: DataType, élément (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataType
helpviewer_keywords:
- DataType element
ms.assetid: efe6f717-8288-4ca2-85ed-9b63d27c02d8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 92c3981344d0425c46ef283fa8792de942d6193b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191039"
---
# <a name="datatype-element-assl"></a>Élément DataType (ASSL)
  Définit le type de données de l'élément associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<DataItem> <!-- or Measure -->  
   ...  
   <DataType>...</DataType>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Chaîne (énumération)|  
|Valeur par défaut|None|  
|Cardinalité|0-1 : élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DataItem](../data-type/dataitem-data-type-assl.md), [mesure](../objects/measure-element-assl.md)|  
|Éléments enfants|None|  
  
## <a name="remarks"></a>Notes  
 Les valeurs de l'élément `DataType` sont définies dans l'énumération `System.Data.OleDb.OleDbType`. Toutefois, seules les valeurs d'énumération présentées dans le tableau suivant sont valides dans l'élément `DataType`.  
  
|Valeur|Description|  
|-----------|-----------------|  
|*BigInt*|Entier signé de 64 bits. Ce type de données est mappé à la `Int64` type de données dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] type de .NET Framework et les données DBTYPE_I8 dans OLE DB.|  
|*bool*|Valeur booléenne. Ce type de données est mappé sur le type de données `Boolean` dans .NET Framework et sur le type de données DBTYPE_BOOL dans OLE DB.|  
|*Devise*|Valeur monétaire comprise entre -2<sup>63</sup> (ou -922,337,203,685,477.5808) à 2<sup>63</sup>-1 (ou + 922,337,203,685,477.5807) avec une précision d’un dix millième d’unité monétaire. Ce type de données est mappé sur le type de données `Decimal` dans .NET Framework et sur le type de données DBTYPE_CY dans OLE DB.|  
|*Date*|Données de date, stockées en tant que nombre à virgule flottante double précision. La partie entière correspond au nombre de jours depuis le 30 décembre 1899 tandis que la partie fractionnaire désigne une fraction d'un jour. Ce type de données est mappé sur le type de données `DateTime` dans .NET Framework et sur le type de données DBTYPE_DATE dans OLE DB.|  
|*Double*|Nombre de double précision à virgule flottante dans la plage de - 1.79E + 308 et 1,79E + 308. Ce type de données est mappé sur le type de données `Double` dans .NET Framework et sur le type de données DBTYPE_R8 dans OLE DB.|  
|*Entier*|Entier signé de 32 bits. Ce type de données est mappé sur le type de données `Int32` dans .NET Framework et sur le type de données DBTYPE_I4 dans OLE DB.|  
|*Unique*|Nombre d’une à virgule flottante simple précision dans la plage de - 3,40E + 38 et 3,40E + 38. Ce type de données est mappé sur le type de données `Single` dans .NET Framework et sur le type de données DBTYPE_R4 dans OLE DB.|  
|*SmallInt*|Entier signé 16 bits. Ce type de données est mappé sur le type de données `Int16` dans .NET Framework et sur le type de données DBTYPE_I4 dans OLE DB.|  
|*TinyInt*|Entier signé 8 bits. Ce type de données est mappé sur le type de données `SByte` dans .NET Framework et sur le type de données DBTYPE_I1 dans OLE DB.|  
|*UnsignedBigInt*|Entier non signé 64 bits. Ce type de données est mappé sur le type de données `UInt64` dans .NET Framework et sur le type de données DBTYPE_UI8 dans OLE DB.|  
|*entier non signé*|Entier non signé 32 bits. Ce type de données est mappé à la `UInt32` type de données dans le .NET Framework et le type de données DBTYPE_UI4 dans OLE DB.|  
|*UnsignedSmallInt*|Entier non signé 16 bits. Ce type de données est mappé sur le type de données `UInt16` dans .NET Framework et sur le type de données DBTYPE_UI4 dans OLE DB.|  
|*WChar*|Flux de caractères Unicode terminé par le caractère NULL. Ce type de données est mappé sur le type de données `String` dans .NET Framework et sur le type de données DBTYPE_WSTR dans OLE DB.|  
|*Héritée*|Le type de données de la `DataItem` contenus dans le [Source](source-element-measure-assl.md) élément de la `Measure` élément. **Remarque :** s’applique uniquement aux `Measure` éléments.|  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40;ASSL&#41;](properties-assl.md)  
  
  
