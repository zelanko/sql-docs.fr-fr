---
title: Après la mise à niveau, recherche en texte intégral n’autorise pas les prédicats d’expression OUTPUT INTO | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f6473409-121a-414d-8fe9-ea9aea6cb7eb
caps.latest.revision: 6
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 42743d1fe4d38c328ac78f3c917d83d858248e30
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37255431"
---
# <a name="after-upgrade-full-text-search-will-not-allow-predicates-in-output-into-expression"></a>Après la mise à niveau, la recherche en texte intégral n'autorise pas les prédicats dans l'expression OUTPUT INTO
  Les prédicats de texte intégral ne sont pas autorisés dans la clause OUTPUT lorsque le niveau de compatibilité de la base de données a la valeur 100 ou une valeur supérieure.  
  
## <a name="description"></a>Description  
 Pour plus d’informations sur la clause OUTPUT, consultez [Clause OUTPUT &#40;Transact-SQL&#41;](/sql/t-sql/queries/output-clause-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de l’Assistant Mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Problèmes de mise à niveau de la fonction de recherche en texte intégral](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
  
