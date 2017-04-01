---
title: "D&#233;finir une relation de fait et des propri&#233;t&#233;s de relation de fait | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
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
  - "dimensions de faits [Analysis Services]"
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# D&#233;finir une relation de fait et des propri&#233;t&#233;s de relation de fait
  Quand vous définissez une nouvelle dimension de cube ou un nouveau groupe de mesures, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente de détecter si une relation de dimension de fait existe et attribut la valeur **Fait** au paramètre d’utilisation de la dimension. Vous pouvez afficher ou modifier une relation de dimension de fait sur l'onglet **Utilisation de la dimension** du Concepteur de cube. La relation de fait entre une dimension et un groupe de mesures a les contraintes suivantes :  
  
-   Une dimension de cube ne peut avoir qu'une seule relation de fait avec un groupe de mesures donné.  
  
-   Une dimension de cube peut avoir des relations de fait distinctes avec plusieurs groupes de mesures.  
  
-   L'attribut de granularité de la relation doit correspondre à l'attribut clé (comme le numéro de transaction) de la dimension. Cela crée une relation de type un-à-un entre les faits et la dimension de la table de faits.  
  
  