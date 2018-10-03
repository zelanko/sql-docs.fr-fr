---
title: EntityType, élément (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 372e2c13-ec38-4bb1-981c-50758d59a1da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f3d1db1998e91eedf4ebc8f759550b2088a29d03
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48139989"
---
# <a name="entitytype-element-csdlbi"></a>Élément EntityType (CSDLBI)
  L'élément `EntityType` est un type complexe qui représente la structure d'une entité de niveau supérieur, par exemple un client ou un tri, dans un modèle de données. Le `bi:EntityType` élément étend la définition de [EntityType](http://msdn.microsoft.com/library/bb399206.aspx) utilisé dans le [Entity Data Framework](/dotnet/framework/data/adonet/ef/overview).  
  
 Un élément EntityType doit être spécifié pour chacune des entités qui sont incluses dans le modèle de données. Les sous-éléments de l'élément EntityType décrivent les colonnes et les mesures dans la table. Les relations entre les tables sont incluses dans `EntityContainer`.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément `EntityType`. Consultez également les attributs applicables à l'élément [EntityType](http://msdn.microsoft.com/library/bb399206.aspx) .  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Sommaire|non|Chaîne qui contient les types de données possibles dans une colonne. La valeur est dérivée de la valeur de DimensionAttributeTypeEnumType dans le modèle de données.<br /><br /> Si la valeur de DimensionAttributeTypeEnumType est « ExtendedType », la valeur de Contents est dérivée de l'élément ExtendedType de DimensionAttribute. Le client n'est pas nécessaire pour répondre à ces valeurs.|  
|DefaultDetails|non|Liste des références de propriété, qui représentent l'ensemble de colonnes dans la table.<br /><br /> Consultez [élément DefaultDetails &#40;CSDLBI&#41;](defaultdetails-element-csdlbi.md).|  
|DefaultImage|non|Référence à une colonne qui contient l'image utilisée pour illustrer l'entité.<br /><br /> Dans les modèles multidimensionnels, cet élément correspond à un attribut binaire de l'attribut de dimension. Si cet attribut est présent, l'élément doit contenir un seul élément MemberRef.<br /><br /> Consultez [élément MemberRef &#40;CSDLBI&#41;](memberref-element-csdlbi.md).|  
|DefaultMeasure|non|Référence à une mesure dans l'entité qui doit être utilisée comme valeur par défaut durant les calculs sur l'entité. Si cet argument n'est pas spécifié, la valeur par défaut est SUM.<br /><br /> Consultez [élément MemberRef &#40;CSDLBI&#41;](memberref-element-csdlbi.md).|  
|DisplayKey|non|Liste de références à des colonnes ou aux fins de rôle, constituant un identificateur fort qui désigne une instance d'entité.<br /><br /> Consultez [élément DisplayKey &#40;CSDLBI&#41;](displaykey-element-csdlbi.md).|  
|Hierarchy|non|Liste de hiérarchies dans le modèle.<br /><br /> Consultez [élément Hierarchy &#40;CSDLBI&#41;](hierarchy-element-csdlbi.md).|  
|ReferenceName|Oui|Identificateur qui peut être utilisé pour référencer cette entité dans une requête DAX (Data Analysis Expressions).<br /><br /> Si cet attribut n'est pas présent, le nom complet du champ de l'entité est utilisé.|  
|SortMembers|non|Liste de propriétés sur lesquelles opérer un tri. L'attribut SortDirection indique si l'ordre est croissant ou décroissant.|  
  
## <a name="contents-element"></a>Élément Contents  
 L'élément `Contents` est un type simple qui décrit le type de données de l'entité.  
  
 Le contenu de l'entité (colonne) peut prendre l'une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|Regular|Pas définie autrement.|  
|Time|Les attributs représentent des périodes de temps, telles que des années, des semestres, des trimestres, des mois ou des jours.|  
|Géographie (Geography)|Les attributs représentent des informations géographiques, telles que des villes ou des codes postaux.|  
|Organisation (Organization)|Les attributs représentent des informations organisationnelles, telles que des employés ou des filiales.|  
|BillOfMaterials|Les attributs représentent des informations d'inventaire ou de fabrication, telles que des listes de composants pour des produits.|  
|Comptes (Accounts)|Les attributs représentent un graphique de comptes utilisé à des fins de génération de rapports financiers.|  
|Clients (Customers)|Les attributs représentent des informations relatives à des clients ou des contacts.|  
|Produits (Products)|Les attributs représentent des informations relatives à des produits.|  
|Scénario|Les attributs représentent des informations de planification ou d'analyse stratégique.|  
|Quantitative|Les attributs représentent des informations quantitatives.|  
|Utility|Les attributs représentent des informations diverses.|  
|Monétaire (Currency)|Contient des données et des métadonnées monétaires.|  
|Taux (Rates)|Les attributs représentent des informations relatives à des taux de devises.|  
|Canal (Channel)|Les attributs représentent des informations relatives à des canaux.|  
|Promotion|Les attributs représentent des informations de promotion commerciale.|  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L'exemple suivant illustre une partie de la représentation de CSDLBI version 1.1 de la table Geography utilisée dans le modèle tabulaire AdventureWorks. La colonne RowNumber est une colonne masquée générée automatiquement comme identificateur de ligne dans les modèles tabulaires, et par conséquent elle possède l'attribut Contents, `RowNumber`.  
  
```  
  
<EntityType   
     Name="DimGeography">  
     <Key>  
        <PropertyRef Name="RowNumber" />  
     </Key>  
     <Property   
        Name="RowNumber"   
        Type="Int64" Nullable="false">  
     <bi:Property   
        Hidden="true"   
        Contents="RowNumber"   
        Stability="RowNumber" />  
     </Property>  
....  
  
```  
  
## <a name="example"></a>Exemple  
 **(Multidimensionnel)**  
  
 L'exemple suivant affiche les éléments EntityType dans CSDLBI version 1.1 qui représentent une partie d'une dimension de temps du cube Contoso Operations.  
  
```  
<EntityType   
       Name="CalendarQuarter">  
    <Key>  
       <PropertyRef Name="RowNumber" />  
    </Key>  
  
    <Property Name="RowNumber"   
       Type="Int64"   
       Nullable="false">  
    <bi:Property   
       Hidden="true"   
       Contents="RowNumber"   
       Stability="RowNumber"   
    />  
    </Property>  
  
    <Property Name="CalendarQuarter2"   
       Type="String"   
       MaxLength="Max"   
       Unicode="true"   
       FixedLength="false"   
       Nullable="false">  
    <bi:Property   
       Caption="CalendarQuarter"   
       ReferenceName="CalendarQuarter"   
    />  
    </Property>  
   <bi:EntityType />  
</EntityType>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations techniques de référence sur les annotations pour le décisionnel dans CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
