---
title: "Définir une relation régulière et les propriétés de relation régulière | Documents Microsoft"
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
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bc2ee7a49cddc8b5d6b0ce0905e2cbcd084a8897
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2018
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>Définir une relation régulière et des propriétés de relation régulière
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Quand vous définissez une nouvelle dimension de cube ou un nouveau groupe de mesures, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente de détecter si une relation régulière existe, puis définit le paramètre d’utilisation de la dimension sur **Normal**. Vous pouvez afficher ou modifier une relation de dimension régulière sous l’onglet **Utilisation de la dimension** du Concepteur de cube.  
  
 Quand vous définissez la relation d'une dimension de cube avec un groupe de mesures, vous spécifiez également l'attribut de granularité de cette relation. L'attribut de granularité définit le niveau de détail le plus bas disponible dans le cube pour cette dimension, qui est généralement l'attribut clé de la dimension. Cependant, vous souhaitez parfois définir la granularité d'une dimension de cube particulière d'un groupe de mesures à un grain différent. Par exemple, vous souhaitez définir la granularité de la dimension Time (Temps) avec l'attribut Month (Mois) plutôt qu'avec l'attribut Day (Jour), si vous utilisez un groupe de mesures de quotas de ventes ou de budget. Si vous spécifiez que l'attribut de granularité doit être un autre attribut que l'attribut clé, vous devez vérifier que tous les autres attributs de la dimension sont directement ou indirectement liés à cet autre attribut via des relations d'attributs. Si ce n'est pas le cas, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne peut pas agréger les données correctement.  
  
  
