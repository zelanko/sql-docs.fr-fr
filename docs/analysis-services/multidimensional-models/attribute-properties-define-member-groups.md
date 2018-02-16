---
title: "Définir des groupes de membres | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 36110a1967917adda6c06ca0e32d138639e1871e
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="attribute-properties---define-member-groups"></a>Propriétés d’attribut : permet de définir des groupes de membres
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Si un attribut possède un grand nombre de membres, vous pouvez décider de grouper ces membres dans des compartiments afin de réduire le nombre de membres visibles lorsque les utilisateurs parcourent les données d'une hiérarchie. Vous pouvez également déterminer le nombre de compartiments dans lesquels sont groupés les membres et définir un schéma d'attribution de noms pour les compartiments. Pour plus d’informations, consultez [Regrouper des membres d’un attribut &#40;discrétisation&#41;](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md).  
  
 Pour grouper les membres, vous devez configurer la propriété **DiscretizationMethod** à laquelle vous pouvez accéder par le biais de la fenêtre **Propriétés** dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Lorsque vous créez des groupes de membres, vos modifications ne sont pas mises à la disposition des utilisateurs avant le traitement de la dimension. Pour plus d’informations, consultez [Traitement d’un modèle multidimensionnel &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-create-member-groups"></a>Pour créer des groupes de membres  
  
1.  Ouvrez la dimension que vous voulez utiliser. L’onglet **Structure de dimension** s’ouvre par défaut.  
  
2.  Dans **Attributs**, cliquez avec le bouton droit sur l’attribut dont vous voulez grouper les membres, puis cliquez sur **Propriétés**.  
  
3.  Dans la liste déroulante à côté de **DiscretizationMethod**, sélectionnez la méthode à utiliser pour grouper les membres. Pour plus d’informations sur les paramètres de la propriété **DiscretizationMethod**, consultez [Regrouper des membres d’un attribut &#40;discrétisation&#41;](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md).  
  
  
