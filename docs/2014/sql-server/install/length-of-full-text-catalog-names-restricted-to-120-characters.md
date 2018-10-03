---
title: Longueur des noms de catalogues de texte intégral limités à 120 caractères | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs names
ms.assetid: 50633373-83f6-4ed9-99b9-71f92479a14f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1ca564fd81a1363f9866a0a8eaf067fc67a1f1f0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128349"
---
# <a name="length-of-full-text-catalog-names-restricted-to-120-characters"></a>Les noms de catalogues de texte intégral sont limités à 120 caractères
  La longueur des noms de catalogues de texte intégral est limitée à 120 caractères, et non plus à 128 comme dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="description"></a>Description  
 Cette modification n'affecte pas les noms de catalogues existants ; toutefois, les scripts qui créent des catalogues de texte intégral avec des noms dépassant 120 caractères provoquent une erreur. Les noms de catalogues servent à générer des noms de fichiers logiques correspondant aux catalogues.  
  
## <a name="corrective-action"></a>Action corrective  
 Modifiez tous les scripts qui créent des catalogues de texte intégral afin de vous assurer qu'ils limitent les noms de catalogues à 120 caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
