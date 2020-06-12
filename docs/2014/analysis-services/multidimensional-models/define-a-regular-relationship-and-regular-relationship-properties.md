---
title: Définir une relation régulière et des propriétés de relation régulière | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b4f49e219a85d5577fb1acddfe14e7afd3b105d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547071"
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>Définir une relation régulière et des propriétés de relation régulière
  Quand vous définissez une nouvelle dimension de cube ou un nouveau groupe de mesures, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente de détecter si une relation régulière existe et affecte le paramètre d'utilisation de la dimension de la valeur `Regular`. Vous pouvez afficher ou modifier une relation de dimension régulière sous l’onglet **Utilisation de la dimension** du Concepteur de cube.  
  
 Quand vous définissez la relation d'une dimension de cube avec un groupe de mesures, vous spécifiez également l'attribut de granularité de cette relation. L'attribut de granularité définit le niveau de détail le plus bas disponible dans le cube pour cette dimension, qui est généralement l'attribut clé de la dimension. Cependant, vous souhaitez parfois définir la granularité d'une dimension de cube particulière d'un groupe de mesures à un grain différent. Par exemple, vous souhaitez définir la granularité de la dimension Time (Temps) avec l'attribut Month (Mois) plutôt qu'avec l'attribut Day (Jour), si vous utilisez un groupe de mesures de quotas de ventes ou de budget. Si vous spécifiez que l'attribut de granularité doit être un autre attribut que l'attribut clé, vous devez vérifier que tous les autres attributs de la dimension sont directement ou indirectement liés à cet autre attribut via des relations d'attributs. Si ce n'est pas le cas, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne peut pas agréger les données correctement.  
  
  
