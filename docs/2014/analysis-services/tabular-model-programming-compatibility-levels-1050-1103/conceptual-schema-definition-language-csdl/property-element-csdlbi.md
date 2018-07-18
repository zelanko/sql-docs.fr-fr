---
title: Property, élément (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f0770c5e-6420-4d0c-a5bf-b94eaf6877ca
caps.latest.revision: 7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e056baf1edf447b0ed321406af12f9260dfcdd12
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37280035"
---
# <a name="property-element-csdlbi"></a>Élément Property (CSDLBI)
  L'élément Property en CSDLBI est un type complexe qui apporte des ajouts à l'élément Property CSDL, pour la prise en charge des modèles de données Business Intelligence.  
  
## <a name="elements-and-attributes"></a>Éléments et attributs  
 Le tableau suivant répertorie les éléments et les attributs qui définissent l'élément Property CSDLBI.  
  
|Nom   |Est obligatoire|Description|  
|----------|-----------------|-----------------|  
|Sommaire|non|Chaîne qui contient le LCID de la demande.|  
|DefaultAggregationFunction|Oui|Chaîne qui spécifie la fonction d'agrégation qui doit être utilisée si des calculs sont effectués sur l'attribut et qu'aucune autre fonction n'a été spécifiée.<br /><br /> S'il n'est pas spécifié, l'agrégation par défaut du modèle est utilisé, généralement SUM.|  
|GroupingBehavior|non|Valeur qui spécifie la manière dont les résultats de la requête sont regroupés. Le contenu de l'attribut est défini par le type simple TGroupingBehavior (voir le tableau ci-dessous).|  
|OrderBy|non|Référence à une autre propriété du modèle qui définit l'ordre de tri pour les valeurs de cette propriété.<br /><br /> Les valeurs des deux propriétés doivent disposer d'un mappage un-à-un. Sinon, le comportement de tri n'est pas défini.<br /><br /> Si cet élément est omis, les propriétés sont triées en fonction de leurs valeurs.|  
|Stability|non|Attribut qui spécifie la stabilité des valeurs de propriété entre les opérations d'actualisation.<br /><br /> Cet attribut n'est pas défini par les utilisateurs, mais est émis par l'environnement de conception uniquement pour les valeurs instables. Il est toujours appliqué aux colonnes qui contiennent un numéro de ligne, et aux colonnes qui contiennent des formules qui génèrent des résultats indéterminés, tels que NOW() ou RAND().<br /><br /> Les valeurs de cet attribut sont répertoriées dans le tableau ci-dessous, qui décrit le type Stabilitysimple.|  
  
## <a name="groupingbehavior"></a>GroupingBehavior  
 Le tableau suivant répertorie les valeurs du type simple GroupingBehavior.  
  
|Valeur|Description|  
|-----------|-----------------|  
|GroupOnValue|Regroupement selon la valeur de l'attribut.|  
|GroupOnEntityKey|Regroupement selon la clé d'entité.|  
  
 L'exemple ci-dessous illustre l'utilisation de ces deux valeurs. Supposons que la requête a été conçue pour retourner les retenues à la source d'un utilisateur donné, indiqué par nom. En supposant que la base de données contient plusieurs utilisateurs avec le même nom mais des identificateurs de base de données différents, les résultats de la requête sont différents en fonction de la valeur d'attribut appliquée à la colonne :  
  
-   `GroupOnValue` : les résultats de la requête incluent les retenues sur salaire des deux utilisateurs, totalisées ensemble.  
  
-   `GroupOnEntityKey` : les résultats de la requête incluent les retenues sur salaire pour chaque utilisateur, mais répertoriées individuellement.  
  
## <a name="stability"></a>Stability  
 Le tableau suivant répertorie les valeurs du type simple `Stability`.  
  
|Valeur|Description|  
|-----------|-----------------|  
|Stable|La propriété reste constante entre les opérations d'actualisation.|  
|RowNumber|La propriété contient un nombre de lignes.|  
|Volatile|Il est possible que la propriété ne reste pas constante entre les opérations d'actualisation.|  
  
## <a name="example"></a>Exemple  
 **Tabulaire**  
  
 L'exemple XML suivant illustre la représentation, en CSDLBI version 1.1, de certaines propriétés de l'exemple de modèle tabulaire AdventureWorks.  
  
```  
  
<EntityType   
   Name="DimEmployee">  
   <Key>  
      <PropertyRef   
      Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber" />  
   </Property>  
  
   <Property   
      Name="EmployeeKey"   
      Type="Int64">  
   <bi:Property />  
   </Property>  
….  
</bi:EntityType>  
</EntityType>  
  
```  
  
## <a name="example"></a>Exemple  
 **(Multidimensionnel)**  
  
 L'exemple suivant, en CSDLBI version 1.1, illustre certaines propriétés des colonnes du modèle de données représentant le cube Contoso Operations. Notez que les annotations BI ne sont pas requises ou ne sont pas appliquées à la plupart des colonnes, uniquement à celles qui nécessitent une gestion spéciale dans la couche présentation.  
  
```  
  
<EntityType   
   Name="Bike">  
  
   <Key>  
      <PropertyRef Name="RowNumber" />  
   </Key>  
  
   <Property   
      Name="RowNumber"   
      Type="Int64"   
      Nullable="false">  
   <bi:Property   
      Hidden="true"   
      Contents="RowNumber"   
      Stability="RowNumber"   
   />  
   </Property>  
  
   <Property   
      Name="ProductAlternateKey"   
      Type="String"   
      MaxLength="Max"   
      Unicode="true"   
      FixedLength="false">  
   <bi:Property />  
   </Property>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations techniques de référence sur les annotations pour le décisionnel dans CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  
