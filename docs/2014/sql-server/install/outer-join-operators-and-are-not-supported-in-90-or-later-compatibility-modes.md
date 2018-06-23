---
title: Opérateurs de jointure externe *= et =* ne sont pas pris en charge en mode de compatibilité 90 ou ultérieur | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- outer joins
- =* join
- '*= join'
- joins [SQL Server]
ms.assetid: ca4aa11f-1048-411f-9c6c-3d0a8e319f2f
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 47a58b60ecd303b893e001663134d9b510bbabfa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154310"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a>Opérateurs de jointure externe *= et =* ne sont pas pris en charge en mode de compatibilité 90 ou ultérieur
  Conseiller de mise à niveau a détecté l’utilisation d’opérateurs de jointure externe * = et =\*. Ces opérateurs ne sont pas pris en charge en mode de compatibilité 90 ou ultérieur. Lorsque vous effectuez une mise à niveau, les bases de données utilisateur conservent leur mode de compatibilité. Les instructions qui utilisent des opérateurs vont échouer.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Avant de modifier le mode de compatibilité 90 ou ultérieur, modifiez les instructions qui utilisent les opérateurs de jointure externe * = et =\* à utiliser des mots clés OUTER JOIN équivalents. L'exemple suivant affiche une requête qui utilise l'opérateur `*=` et une requête équivalente qui utilise les mots clés `LEFT OUTER JOIN`.  
  
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
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
