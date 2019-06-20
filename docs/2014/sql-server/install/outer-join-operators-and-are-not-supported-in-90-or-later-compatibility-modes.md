---
title: Opérateurs de jointure externe *= et =* ne sont pas pris en charge en mode de compatibilité 90 ou ultérieur | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- outer joins
- =* join
- '*= join'
- joins [SQL Server]
ms.assetid: ca4aa11f-1048-411f-9c6c-3d0a8e319f2f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 62a6f9e016abf24f28660b04e7a6242fdd6606ce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66093685"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a>Les opérateurs de jointure externe \*= et =\* ne sont pas pris en charge en mode de compatibilité 90 ou ultérieur
  Conseiller de mise à niveau a détecté l’utilisation d’opérateurs de jointure externe \*= et =\*. Ces opérateurs ne sont pas pris en charge en mode de compatibilité 90 ou ultérieur. Lorsque vous effectuez une mise à niveau, les bases de données utilisateur conservent leur mode de compatibilité. Les instructions qui utilisent des opérateurs vont échouer.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Avant de définir le mode de compatibilité de base de données à 90 ou ultérieur, modifiez les instructions qui utilisent les opérateurs de jointure externe \*= et =\* à utiliser les mots clés OUTER JOIN équivalents. L'exemple suivant affiche une requête qui utilise l'opérateur `\*=` et une requête équivalente qui utilise les mots clés `LEFT OUTER JOIN`.  
  
```  
-- This query uses an old-style outer join operator.  
USE pubs  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee, jobs   
WHERE employee.job_id *= jobs.job_id  
ORDER BY employee.job_id  
  
-- This query uses the ANSI standard keywords LEFT OUTER JOIN.  
USE pubs;  
SELECT employee.job_id, employee.emp_id,  
   employee.fname, employee.minit, jobs.job_desc  
FROM employee LEFT OUTER JOIN jobs ON   
    employee.job_id = jobs.job_id  
ORDER BY employee.job_id  
```  
  
 Pour plus d'informations sur les jointures externes, consultez « Utilisation de jointures externes » dans la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
