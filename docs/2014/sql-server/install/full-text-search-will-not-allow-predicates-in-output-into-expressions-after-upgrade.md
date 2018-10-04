---
title: Après la mise à niveau, recherche en texte intégral n’autorise pas les prédicats d’expression OUTPUT INTO | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: f6473409-121a-414d-8fe9-ea9aea6cb7eb
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 77d26b41bdb848d487f144b40e86f1c00ad60880
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210739"
---
# <a name="after-upgrade-full-text-search-will-not-allow-predicates-in-output-into-expression"></a>Après la mise à niveau, la recherche en texte intégral n'autorise pas les prédicats dans l'expression OUTPUT INTO
  Les prédicats de texte intégral ne sont pas autorisés dans la clause OUTPUT lorsque le niveau de compatibilité de la base de données a la valeur 100 ou une valeur supérieure.  
  
## <a name="description"></a>Description  
 Pour plus d’informations sur la clause OUTPUT, consultez [Clause OUTPUT &#40;Transact-SQL&#41;](/sql/t-sql/queries/output-clause-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de l’Assistant Mise à niveau](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Problèmes de mise à niveau de la fonction de recherche en texte intégral](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
  
