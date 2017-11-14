---
title: "L’élément DataType (ASSL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DataType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DataType
helpviewer_keywords:
- DataType element
ms.assetid: efe6f717-8288-4ca2-85ed-9b63d27c02d8
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1e1cdd832a006148a8d72c8e7931ae4d662bce00
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

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
|Valeur par défaut|Aucune|  
|Cardinalité|0-1: élément facultatif qui peut apparaître une fois et une seule.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Élément parent|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md), [mesure](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|Éléments enfants|Aucune|  
  
## <a name="remarks"></a>Notes  
 Les valeurs de **DataType** sont définies dans le **System.Data.OleDb.OleDbType** énumération. Toutefois, seules les valeurs d’énumération dans le tableau suivant sont valides dans le **DataType** élément.  
  
|Valeur| Description|  
|-----------|-----------------|  
|*BigInt*|Entier signé de 64 bits. Ce type de données est mappé à la **Int64** de type de données dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] de type .NET Framework et les données DBTYPE_I8 dans OLE DB.|  
|*Bool*|Valeur booléenne. Ce type de données est mappé à la **booléenne** type de données dans le .NET Framework et le type de données DBTYPE_BOOL dans OLE DB.|  
|*Devise*|Valeur monétaire comprise entre -2<sup>63</sup> (ou -922,337,203,685,477.5808) à 2<sup>63</sup>-1 (ou + 922,337,203,685,477.5807) avec une précision au dix-millième d’unité monétaire. Ce type de données est mappé à la **décimal** type de données dans le .NET Framework et le type de données DBTYPE_CY dans OLE DB.|  
|*Date*|Données de date, stockées en tant que nombre à virgule flottante double précision. La partie entière correspond au nombre de jours depuis le 30 décembre 1899 tandis que la partie fractionnaire désigne une fraction d'un jour. Ce type de données est mappé à la **DateTime** type de données dans le .NET Framework et le type de données DBTYPE_DATE dans OLE DB.|  
|*Double*|Une virgule flottante double précision nombre compris entre - 1.79E + 308 et 1,79E + 308. Ce type de données est mappé à la **Double** type de données dans le .NET Framework et le type de données DBTYPE_R8 dans OLE DB.|  
|*Entier*|Entier signé de 32 bits. Ce type de données est mappé à la **Int32** type de données dans le .NET Framework et le type de données DBTYPE_I4 dans OLE DB.|  
|*Unique*|Une virgule flottante simple précision nombre compris entre - 3,40E 3,40E par le biais de +38 +38. Ce type de données est mappé à la **unique** type de données dans le .NET Framework et le type de données DBTYPE_R4 dans OLE DB.|  
|*SmallInt*|Entier signé 16 bits. Ce type de données est mappé à la **Int16** type de données dans le .NET Framework et le type de données DBTYPE_I2 dans OLE DB.|  
|*TinyInt*|Entier signé 8 bits. Ce type de données est mappé à la **SByte** type de données dans le .NET Framework et le type de données DBTYPE_I1 dans OLE DB.|  
|*UnsignedBigInt*|Entier non signé 64 bits. Ce type de données est mappé à la **UInt64** type de données dans le .NET Framework et le type de données DBTYPE_UI8 dans OLE DB.|  
|*Entier non signé*|Entier non signé 32 bits. Ce type de données est mappé à la **UInt32** type de données dans le .NET Framework et le type de données DBTYPE_UI4 dans OLE DB.|  
|*UnsignedSmallInt*|Entier non signé 16 bits. Ce type de données est mappé à la **UInt16** type de données dans le .NET Framework et le type de données DBTYPE_UI2 dans OLE DB.|  
|*WChar*|Flux de caractères Unicode terminé par le caractère NULL. Ce type de données est mappé à la **chaîne** type de données dans le .NET Framework et le type de données DBTYPE_WSTR dans OLE DB.|  
|*Héritée*|Type de données de la **DataItem** contenus dans le [Source](../../../analysis-services/scripting/properties/source-element-measure-assl.md) élément de la **mesure** élément.<br /><br /> Remarque : Applicable uniquement aux **mesure** éléments.|  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

