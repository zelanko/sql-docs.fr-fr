---
title: "Dimensions parent-enfant | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "hiérarchies [Analysis Services], parent-enfant"
  - "dimensions [Analysis Services], parent-enfant"
  - "attributs parents [Analysis Services]"
  - "membres de données [Analysis Services]"
  - "hiérarchies [Analysis Services], sur plusieurs niveaux"
  - "jointures réflexives"
  - "relations, référence circulaire"
  - "membres [Analysis Services], données"
  - "dimensions parent-enfant [Analysis Services]"
ms.assetid: 4657f5dc-d88e-48d2-a448-08f79bc89546
caps.latest.revision: 42
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Dimensions parent-enfant
  Une hiérarchie parent-enfant est une hiérarchie dans une dimension standard qui contient un attribut parent. Un attribut parent décrit une *relation d’auto-référencement*, ou *jointure réflexive*, dans une table de dimension principale. Les hiérarchies parent-enfant sont construites à partir d'un seul attribut parent. Un seul niveau est affecté à une hiérarchie parent-enfant parce que les niveaux présents dans la hiérarchie sont constitués à partir des relations parent-enfant entre les membres associés à l'attribut parent. La position d’un membre au sein d’une hiérarchie parent-enfant est déterminée par les propriétés **KeyColumns** et **RootMemberIf** de l’attribut parent, tandis que la position d’un membre au sein d’un niveau est déterminée par la propriété **OrderBy** de l’attribut parent. Pour plus d’informations sur les propriétés d’attributs, consultez [Attributs et hiérarchies d’attributs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).  
  
 À cause des relations parent-enfant existant entre les niveaux d'une hiérarchie parent-enfant, certains membres non-feuilles peuvent également avoir des données dérivées des sources de données sous-jacentes en plus des données agrégées des membres enfants.  
  
## Schéma de dimension  
 Le schéma de dimension d'une hiérarchie parent-enfant dépend de la présence d'une relation d'auto-référencement dans la table principale de la dimension. Par exemple, le diagramme suivant montre la table de dimension principale **DimOrganization** de l’exemple de base de données [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)].  
  
 ![Jointure auto-référencée dans la table DimOrganization](../../analysis-services/multidimensional-models/media/dimorganization.png "Jointure auto-référencée dans la table DimOrganization")  
  
 Dans cette table de dimension, la colonne **ParentOrganizationKey** a une relation de clé étrangère avec la colonne clé primaire **OrganizationKey**. En d'autres termes, chaque enregistrement dans cette table peut être associé à un autre enregistrement de la table par une relation parent-enfant. Ce type de jointure réflexive est généralement utilisé pour représenter les données d'une entité d'une organisation, telles que la structure de gestion des employés dans un service.  
  
## Hiérarchies et niveaux  
 Les dimensions qui n'ont pas de relations de type parent-enfant construisent les hiérarchies en regroupant et en organisant les attributs. Les noms de niveaux des hiérarchies de ces dimensions sont issus des noms d'attributs.  
  
 Toutefois, les dimensions de type parent-enfant construisent les hiérarchies de type parent-enfant en analysant les données de la table de dimension principale et en évaluant les relations de type parent-enfant entre les enregistrements dans la table. Pour plus d’informations sur les hiérarchies parent-enfant, consultez [Hiérarchies utilisateur](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md).  
  
 Les hiérarchies parent-enfant ne dérivent pas les noms de leurs niveaux des attributs utilisés pour créer la hiérarchie. En effet, ces dimensions créent les noms de niveaux automatiquement en utilisant un modèle de nom, une expression de chaîne que vous pouvez spécifier au niveau de l'attribut parent qui contrôle la manière dont l'attribut génère la hiérarchie d'attribut. Pour plus d’informations sur la façon de définir le modèle de nom d’un attribut parent, consultez [Attributs et hiérarchies d’attributs](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md).  
  
## Données membres  
 En général, les membres feuilles d'une dimension contiennent des données directement dérivées des sources de données sous-jacentes, tandis que les membres non-feuilles contiennent des données dérivées d'agrégations effectuées sur les membres enfants.  
  
 Toutefois, les hiérarchies parent-enfant peuvent avoir certains membres non-feuilles dont les données sont dérivées des sources de données sous-jacentes, en plus des données agrégées des membres enfants. Pour ces membres non-feuilles d'une hiérarchie parent-enfant, il est possible de créer des membres enfants spéciaux générés par le système qui contiennent les données de la table de faits sous-jacente. Appelés *données membres*, ces membres enfants spéciaux contiennent une valeur directement associée à un membre non feuille et indépendante de la valeur résumée calculée à partir des descendants du membre non feuille. Pour plus d’informations sur les membres de données, consultez [Attributs dans des hiérarchies de type parent-enfant](../../analysis-services/multidimensional-models/attributes-in-parent-child-hierarchies.md).  
  
## Voir aussi  
 [Attributs dans des hiérarchies de type parent-enfant](../../analysis-services/multidimensional-models/attributes-in-parent-child-hierarchies.md)   
 [Propriétés de dimension d'une base de données](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties.md)  
  
  