---
title: Afficher les cibles d’événements étendus pour les Packages enregistrés | Documents Microsoft
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
- targets [SQL Server extended events]
- viewing event targets
- extended events [SQL Server], viewing targets
ms.assetid: 4985aa5f-ac99-49f6-852c-9d25916549e9
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1c5552ca54f3297226fad6a15de2d5c80bc49067
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039160"
---
# <a name="view-the-extended-events-targets-for-registered-packages"></a>Afficher les cibles d'événements étendus pour les packages enregistrés
  Avant de créer une session d’événements étendus [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , il est utile de déterminer quelles sont les cibles d’événements étendus présentes. Cette tâche implique l'utilisation de l'Éditeur de requête dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] pour effectuer la procédure suivante.  
  
 Une fois que les instructions de cette procédure sont exécutées, l’onglet **Résultats** de l’éditeur de requête affiche les deux colonnes suivantes :  
  
-   package_name  
  
-   target_name  
  
## <a name="to-view-the-extended-events-targets-for-registered-packages-using-query-editor"></a>Pour afficher les cibles d'événements étendus pour les packages enregistrés à l'aide de l'éditeur de requête  
  
-   Dans l'éditeur de requêtes, émettez les instructions suivantes.  
  
    ```  
    USE msdb  
    SELECT p.name package_name, o.name target_name  
    FROM sys.dm_xe_objects o  
    JOIN sys.dm_xe_packages p  
         ON o.package_guid = p.guid  
    WHERE o.object_type = 'target'  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Cibles des Événements étendus SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
