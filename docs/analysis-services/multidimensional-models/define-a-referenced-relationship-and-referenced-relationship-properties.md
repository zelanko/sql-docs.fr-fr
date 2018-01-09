---
title: "Définir une relation référencée et propriétés de relation référencée | Documents Microsoft"
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
- referenced dimension relationship
- relationships [Analysis Services], referenced dimensions
ms.assetid: 5bb44b41-635b-4398-8fe9-0bfbb142553e
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 96804fae479d3332eebc07e7477a1807fa4831be
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="define-a-referenced-relationship-and-referenced-relationship-properties"></a>Définir une relation référencée et des propriétés de relation référencée
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Une relation de dimension de référence est définie sur le **utilisation de la Dimension** onglet du Concepteur de Cube. Pour définir la relation de dimension de référence, spécifiez les éléments suivants :  
  
-   La dimension intermédiaire à joindre. Il peut s'agir d'une dimension régulière ou d'une autre dimension de référence.  
  
-   Attribut de dimension de référence qui définit le niveau le plus bas où la dimension est disponible pour l'agrégation par rapport au groupe de mesures.  
  
-   L'attribut (clé étrangère) dans la dimension intermédiaire qui correspond à l'attribut de dimension de référence.  
  
 Notez que la colonne qui lie la dimension de référence à la table de faits, qui est généralement l'attribut clé dans la dimension de référence, doit aussi être définie en tant qu'attribut dans la dimension intermédiaire. Lorsque vous créez une chaîne de dimensions de référence, commencez par créer la relation régulière entre la première dimension de la chaîne et le groupe de mesures. Créez ensuite chaque relation référencée additionnelle dans l'ordre. Une relation référencée ne peut être créée qu'avec une dimension ayant une relation existante avec le groupe de mesures.  
  
 Quand vous créez une relation de dimension de référence, le lien d'attribut de dimension est matérialisé par défaut. La matérialisation d'un lien d'attribut de dimension fait que la valeur du lien entre la table de faits et la dimension de référence pour chaque ligne est matérialisée, ou stockée, dans la structure MOLAP de la dimension lors du traitement. Ceci a un effet mineur sur les performances du traitement et sur l'espace de stockage nécessaire, mais permet d'accroître les performances des requêtes.  
  
 Dans une dimension de référence, la granularité est spécifiée en identifiant l'attribut qui définit la relation entre une dimension de référence et le groupe de mesures correspondant à la table principale de la dimension. Lorsque plusieurs dimensions de référence sont chaînées ensemble, les références définissent la relation entre la dimension la plus éloignée et le groupe de mesures.  
  
  
