---
title: Longueur des noms de catalogues de texte intégral est limitée à 120 caractères | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- full-text catalogs names
ms.assetid: 50633373-83f6-4ed9-99b9-71f92479a14f
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f11c8b5a0698c83846f1570946a551f82a09ab48
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143816"
---
# <a name="length-of-full-text-catalog-names-restricted-to-120-characters"></a>Les noms de catalogues de texte intégral sont limités à 120 caractères
  La longueur des noms de catalogues de texte intégral est limitée à 120 caractères, et non plus à 128 comme dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="description"></a>Description  
 Cette modification n'affecte pas les noms de catalogues existants ; toutefois, les scripts qui créent des catalogues de texte intégral avec des noms dépassant 120 caractères provoquent une erreur. Les noms de catalogues servent à générer des noms de fichiers logiques correspondant aux catalogues.  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez tous les scripts qui créent des catalogues de texte intégral afin de vous assurer qu'ils limitent les noms de catalogues à 120 caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation avec le Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  