---
title: Index de recherche en texte intégral sur les colonnes calculées non persistantes ne sont pas autorisés. | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 417ca3c2e5e477960c4c905543f3a712a5ec7453
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66095170"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a>Les index de recherche en texte intégral sur des colonnes calculées non persistantes ne sont pas autorisés
  Vous ne pouvez pas créer des index de recherche en texte intégral sur des colonnes calculées non déterministes et imprécises. Ces colonnes ne peuvent pas être utilisées en tant que colonnes de type ou en colonnes clés de texte intégral.  
  
## <a name="description"></a>Description  
 Dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], un index de recherche en texte intégral peut être créé à l'aide d'une colonne calculée non déterministe et imprécise comme colonne de type ou colonne clé de texte intégral. Cette fonctionnalité n'est pas prise en charge. Lorsque vous effectuez une mise à niveau, les index de recherche en texte intégral plus anciens, incompatibles ou non pris en charge sont désactivés.  
  
## <a name="corrective-action"></a>Action corrective  
 Pour activer ces index de recherche en texte intégral, modifiez les définitions de colonnes afin que les colonnes soient déterministes et précises.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
