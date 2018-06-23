---
title: Index de recherche en texte intégral sur les colonnes calculées non persistantes ne sont pas autorisés. | Documents Microsoft
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
- full-text indexes
ms.assetid: cba737f7-b187-47d0-8458-23dc18d18aca
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d51500dca40ed039816b973cb4698971996e2b01
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141237"
---
# <a name="full-text-indexes-on-nonpersisted-computed-columns-are-not-allowed"></a>Les index de recherche en texte intégral sur des colonnes calculées non persistantes ne sont pas autorisés
  Vous ne pouvez pas créer des index de recherche en texte intégral sur des colonnes calculées non déterministes et imprécises. Ces colonnes ne peuvent pas être utilisées en tant que colonnes de type ou en colonnes clés de texte intégral.  
  
## <a name="description"></a>Description  
 Dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], un index de recherche en texte intégral peut être créé à l'aide d'une colonne calculée non déterministe et imprécise comme colonne de type ou colonne clé de texte intégral. Cette fonctionnalité n'est pas prise en charge. Lorsque vous effectuez une mise à niveau, les index de recherche en texte intégral plus anciens, incompatibles ou non pris en charge sont désactivés.  
  
## <a name="corrective-action"></a>Action corrective  
 Pour activer ces index de recherche en texte intégral, modifiez les définitions de colonnes afin que les colonnes soient déterministes et précises.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation avec le Conseiller de mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  