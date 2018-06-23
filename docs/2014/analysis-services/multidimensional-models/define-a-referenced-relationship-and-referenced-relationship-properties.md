---
title: Définir une relation référencée et propriétés de relation référencée | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- referenced dimension relationship
- relationships [Analysis Services], referenced dimensions
ms.assetid: 5bb44b41-635b-4398-8fe9-0bfbb142553e
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 845ec8020ece6d253d4c025b960081a801123a0c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153588"
---
# <a name="define-a-referenced-relationship-and-referenced-relationship-properties"></a>Définir une relation référencée et des propriétés de relation référencée
  Vous pouvez définir une relation de dimension de référence sous l’onglet **Utilisation de la dimension** du Concepteur de cube. Pour définir la relation de dimension de référence, spécifiez les éléments suivants :  
  
-   La dimension intermédiaire à joindre. Il peut s'agir d'une dimension régulière ou d'une autre dimension de référence.  
  
-   Attribut de dimension de référence qui définit le niveau le plus bas où la dimension est disponible pour l'agrégation par rapport au groupe de mesures.  
  
-   L'attribut (clé étrangère) dans la dimension intermédiaire qui correspond à l'attribut de dimension de référence.  
  
 Notez que la colonne qui lie la dimension de référence à la table de faits, qui est généralement l'attribut clé dans la dimension de référence, doit aussi être définie en tant qu'attribut dans la dimension intermédiaire. Lorsque vous créez une chaîne de dimensions de référence, commencez par créer la relation régulière entre la première dimension de la chaîne et le groupe de mesures. Créez ensuite chaque relation référencée additionnelle dans l'ordre. Une relation référencée ne peut être créée qu'avec une dimension ayant une relation existante avec le groupe de mesures.  
  
 Quand vous créez une relation de dimension de référence, le lien d'attribut de dimension est matérialisé par défaut. La matérialisation d'un lien d'attribut de dimension fait que la valeur du lien entre la table de faits et la dimension de référence pour chaque ligne est matérialisée, ou stockée, dans la structure MOLAP de la dimension lors du traitement. Ceci a un effet mineur sur les performances du traitement et sur l'espace de stockage nécessaire, mais permet d'accroître les performances des requêtes.  
  
 Dans une dimension de référence, la granularité est spécifiée en identifiant l'attribut qui définit la relation entre une dimension de référence et le groupe de mesures correspondant à la table principale de la dimension. Lorsque plusieurs dimensions de référence sont chaînées ensemble, les références définissent la relation entre la dimension la plus éloignée et le groupe de mesures.  
  
  