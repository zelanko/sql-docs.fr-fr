---
title: "D&#233;finir des groupes de membres | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
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
  - "groupes de membres [Analysis Services]"
  - "regroupement de membres"
  - "DiscretizationMethod, propriété"
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
caps.latest.revision: 36
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# D&#233;finir des groupes de membres
  Si un attribut possède un grand nombre de membres, vous pouvez décider de grouper ces membres dans des compartiments afin de réduire le nombre de membres visibles lorsque les utilisateurs parcourent les données d'une hiérarchie. Vous pouvez également déterminer le nombre de compartiments dans lesquels sont groupés les membres et définir un schéma d'attribution de noms pour les compartiments. Pour plus d’informations, consultez [Regrouper des membres d’un attribut &#40;discrétisation&#41;](../../analysis-services/multidimensional-models/group-attribute-members-discretization.md).  
  
 Pour grouper les membres, vous devez configurer la propriété **DiscretizationMethod** à laquelle vous pouvez accéder par le biais de la fenêtre **Propriétés** dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Lorsque vous créez des groupes de membres, vos modifications ne sont pas mises à la disposition des utilisateurs avant le traitement de la dimension. Pour plus d’informations, consultez [Traitement d’un modèle multidimensionnel &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
### Pour créer des groupes de membres  
  
1.  Ouvrez la dimension que vous voulez utiliser. L’onglet **Structure de dimension** s’ouvre par défaut.  
  
2.  Dans **Attributs**, cliquez avec le bouton droit sur l’attribut dont vous voulez grouper les membres, puis cliquez sur **Propriétés**.  
  
3.  Dans la liste déroulante à côté de **DiscretizationMethod**, sélectionnez la méthode à utiliser pour grouper les membres. Pour plus d’informations sur les paramètres de la propriété **DiscretizationMethod**, consultez [Regrouper des membres d’un attribut &#40;discrétisation&#41;](../../analysis-services/multidimensional-models/group-attribute-members-discretization.md).  
  
  