---
title: Analyse du workflow de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5654cb30-cad2-470c-97b3-59cb331033e5
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 5723ba6fcbcd8e5b2280fc977aa5f405d461b805
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84925560"
---
# <a name="analysis-of-data-flow"></a>Analyse des flux de données
  Vous pouvez utiliser la [catalog.execution_data_statistics](../relational-databases/statistics/statistics.md) `SSISDB` vue de base de donnéescatalog.execution_data_statistics pour analyser le workflow des packages. Cette vue affiche une ligne à chaque fois qu'un composant de flux de données envoie des données à un composant en aval. Les informations peuvent être utilisées pour mieux comprendre les lignes envoyées à chaque composant.  
  
> [!NOTE]  
>  Le niveau de journalisation doit avoir la valeur **Commentaires** afin de capturer des informations avec la vue catalog.execution_data_statistics.  
  
 L'exemple suivant affiche le nombre de lignes transmises entre les composants d'un package.  
  
```  
use SSISDB  
select package_name, task_name, source_component_name, destination_component_name, rows_sent  
from catalog.execution_data_statistics  
where execution_id = 132  
order by source_component_name, destination_component_name  
  
```  
  
 L'exemple suivant calcule le nombre de lignes par milliseconde envoyées par chaque composant pour une exécution spécifique. Les valeurs calculées sont les suivantes :  
  
-   **total_rows** - Somme de toutes les lignes envoyées par le composant  
  
-   **wall_clock_time_ms** - Durée d’exécution écoulée totale en millisecondes pour chaque composant  
  
-   **num_rows_per_millisecond** - Nombre de lignes par milliseconde envoyées par chaque composant  
  
 La `HAVING` clause est utilisée pour empêcher une erreur de division par zéro dans les calculs.  
  
```  
use SSISDB  
select source_component_name, destination_component_name,  
    sum(rows_sent) as total_rows,  
    DATEDIFF(ms,min(created_time),max(created_time)) as wall_clock_time_ms,  
    ((0.0+sum(rows_sent)) / (datediff(ms,min(created_time),max(created_time)))) as [num_rows_per_millisecond]  
from [catalog].[execution_data_statistics]  
where execution_id = 132  
group by source_component_name, destination_component_name  
having (datediff(ms,min(created_time),max(created_time))) > 0  
order by source_component_name desc  
  
```  
  
## <a name="related-tasks"></a>Tâches associées  
 [Débogage d’un flux de données](troubleshooting/debugging-data-flow.md)  
  
 [Outils de dépannage pour l'exécution des packages](troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Données dans des flux de données](data-flow/data-in-data-flows.md)  
  
  
