---
title: "Définir une relation de faits et les propriétés de relation de faits | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 46cf5d6b942751fb0ca76942e8762cec271a5b4c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a>Définir une relation de fait et des propriétés de relation de fait
  Quand vous définissez une nouvelle dimension de cube ou un nouveau groupe de mesures, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente de détecter si une relation de dimension de fait existe et attribut la valeur **Fait**au paramètre d’utilisation de la dimension. Vous pouvez afficher ou modifier une relation de dimension de fait sur l'onglet **Utilisation de la dimension** du Concepteur de cube. La relation de fait entre une dimension et un groupe de mesures a les contraintes suivantes :  
  
-   Une dimension de cube ne peut avoir qu'une seule relation de fait avec un groupe de mesures donné.  
  
-   Une dimension de cube peut avoir des relations de fait distinctes avec plusieurs groupes de mesures.  
  
-   L'attribut de granularité de la relation doit correspondre à l'attribut clé (comme le numéro de transaction) de la dimension. Cela crée une relation de type un-à-un entre les faits et la dimension de la table de faits.  
  
  
