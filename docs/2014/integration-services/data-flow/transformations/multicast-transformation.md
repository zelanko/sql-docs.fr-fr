---
title: Multidiffusion, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.multicasttrans.f1
helpviewer_keywords:
- multiple outputs
- Multicast transformation
- datasets [Integration Services], multiple outputs
- multiple transformations
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a05605ca5c2b35b0a5e35c8228a2a144f20d7905
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900186"
---
# <a name="multicast-transformation"></a>transformation de multidiffusion
  La transformation de multidiffusion distribue son entrée vers une ou plusieurs sorties. Cette transformation est similaire à la transformation de fractionnement conditionnel. Les deux transformations dirigent une entrée vers plusieurs sorties. Leur différence réside dans le fait que la transformation de multidiffusion dirige chaque ligne vers chaque sortie, tandis que la transformation de fractionnement conditionnel dirige une ligne vers une seule sortie. Pour plus d’informations, voir [Conditional Split Transformation](conditional-split-transformation.md).  
  
 Vous configurez la transformation de multidiffusion en ajoutant des sorties.  
  
 À l'aide de la transformation de multidiffusion, un package peut créer des copies logiques des données. Cette fonctionnalité est utile lorsque le package doit appliquer plusieurs ensembles de transformations aux mêmes données. Par exemple, une copie des données est agrégée et seules les informations de résumé sont chargées à leur emplacement de destination, tandis qu'une autre copie des données est enrichie de valeurs recherchées et de colonnes dérivées avant d'être chargée à son emplacement de destination.  
  
 Cette transformation a une entrée et plusieurs sorties. Elle ne prend pas en charge de sortie d'erreur.  
  
## <a name="configuration-of-the-multicast-transformation"></a>Configuration de la transformation de multidiffusion  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue **Éditeur de transformation de multidiffusion** , consultez [Éditeur de transformation de multidiffusion](../../multicast-transformation-editor.md).  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir par programmation, consultez [Propriétés communes](../../common-properties.md).  
  
## <a name="related-tasks"></a>Tâches associées  
 Pour plus d’informations sur la définition des propriétés de ce composant, consultez [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de données](../data-flow.md)   
 [Transformations Integration Services](integration-services-transformations.md)  
  
  
