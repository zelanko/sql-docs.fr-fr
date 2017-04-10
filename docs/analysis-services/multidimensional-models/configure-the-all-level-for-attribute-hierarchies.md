---
title: "Configurer le niveau (Tous) des hi&#233;rarchies d&#39;attributs | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
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
  - "Tous les membres"
  - "IsAggregatable (propriété)"
  - "niveaux les plus élevés [Analysis Services]"
  - "niveaux (Tous)"
  - "AttributeAllMemberName (propriété)"
  - "niveaux [Analysis Services]"
  - "membres [Analysis Services], tous"
  - "AllMemberName (propriété)"
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
caps.latest.revision: 33
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Configurer le niveau (Tous) des hi&#233;rarchies d&#39;attributs
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le niveau (Tous) est un niveau facultatif, généré par le système. Il contient un seul membre dont la valeur est l'agrégation des valeurs de tous les membres du niveau situé juste en dessous. Ce membre est appelé membre Tous. Ce membre est créé par le système et il ne figure pas dans la table de dimension. Étant donné que le membre du niveau (Tous) se trouve au sommet d'une hiérarchie, sa valeur est l'agrégation consolidée des valeurs de tous les membres de la hiérarchie. Le membre Tous sert souvent de membre par défaut d'une hiérarchie.  
  
 La présence d’un niveau (Tous) dans une hiérarchie d’attributs dépend de la valeur de la propriété **IsAggregatable** de l’attribut, et la présence d’un niveau (Tous) dans une hiérarchie définie par l’utilisateur dépend de la propriété **IsAggregatable** de l’attribut au niveau le plus élevé de la hiérarchie définie par l’utilisateur. Si la propriété **IsAggregatable** a la valeur **True**, il existera un niveau (Tous). Au contraire, une hiérarchie n’a pas de niveau (Tous) si sa propriété **IsAggregatable** a la valeur **False**.  
  
## Établissement du niveau le plus élevé  
 Si la propriété **IsAggregatable** de l’attribut source d’un niveau d’une hiérarchie a la valeur **False**, aucun niveau agrégeable ne peut apparaître dans la hiérarchie au-dessus de ce niveau. Un niveau non agrégeable doit être le niveau le plus élevé d’une hiérarchie, ou la propriété **IsAggregatable** des attributs sources des niveaux qui sont au-dessus de lui doit aussi avoir la valeur **False**.  
  
## Membre Tous et niveau (Tous)  
 Le membre unique du niveau (Tous) est appelé membre Tous. La propriété **AttributeAllMemberName** d’une dimension spécifie le nom du membre Tous pour les attributs d’une dimension. La propriété **AllMemberName** d’une hiérarchie spécifie le nom du membre Tous de cette hiérarchie.  
  
## Voir aussi  
 [Définir un membre par défaut](../../analysis-services/multidimensional-models/define-a-default-member.md)  
  
  