---
title: Les opérateurs de jointure externe *= et =* ne sont pas pris en charge dans les modes de compatibilité 90 ou ultérieur | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66093685"
---
# <a name="outer-join-operators--and--are-not-supported-in-90-or-later-compatibility-modes"></a>Les opérateurs de jointure externe \*= et =\* ne sont pas pris en charge en mode de compatibilité 90 ou ultérieur
  Le conseiller de mise à niveau a détecté l' \*utilisation des opérateurs\*de jointure externe = et =. Ces opérateurs ne sont pas pris en charge en mode de compatibilité 90 ou ultérieur. Lorsque vous effectuez une mise à niveau, les bases de données utilisateur conservent leur mode de compatibilité. Les instructions qui utilisent des opérateurs vont échouer.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Avant de modifier le mode de compatibilité de la base de données en 90 ou une version ultérieure, modifiez \*les instructions qui\* utilisent les opérateurs de jointure externe = et = pour utiliser des mots clés de jointure externe équivalents. L'exemple suivant affiche une requête qui utilise l'opérateur `\*=` et une requête équivalente qui utilise les mots clés `LEFT OUTER JOIN`.  
  
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
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
