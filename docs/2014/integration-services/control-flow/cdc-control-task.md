---
title: Contrôle de capture de données modifiées, tâche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdccontroltask.f1
ms.assetid: 6404dc7f-550c-47cc-b901-c072742f430a
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 90d9aa5fbc864b9e5da68fbb80c9b97918bd0d80
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37199639"
---
# <a name="cdc-control-task"></a>Tâche de contrôle de capture de données modifiées
  La tâche de contrôle de capture de données modifiées permet de contrôler le cycle de vie des packages de capture de données modifiées. Elle gère la synchronisation des package de capture de données modifiées avec le package de charge initiale et la gestion des plages de numéros séquentiels dans le journal (NSE) qui sont traités lors de l'exécution d'un package de capture de données modifiées. En outre, la tâche de contrôle de capture de données modifiées traite les scénarios d'erreur et la récupération.  
  
 La tâche de contrôle de capture de données modifiées gère l'état du package de capture de données modifiées dans une variable de package SSIS et peut également le conserver de manière permanente dans une table de base de données afin qu'il soit conservé d'une activation de package à l'autre et entre plusieurs packages qui exécutent ensemble un processus de capture de données modifiées commun (par exemple, une tâche peut être responsable du chargement initial et l'autre des mises à jour du flux progressif).  
  
 La tâche de contrôle de capture de données modifiées prend en charge deux groupes d'opérations. Un groupe gère la synchronisation de la charge initiale et le traitement des modifications, tandis que l'autre gère la plage de traitement des modifications des NSE pour une exécution d'un package de source de données modifiées et garde une trace des actions correctement traitées.  
  
 Les opérations suivantes gèrent la synchronisation de la charge initiale et le traitement des modifications :  
  
|Opération|Description|  
|---------------|-----------------|  
|ResetCdcState|Cette opération est utilisée pour réinitialiser l'état permanent de capture de données modifiées associé au contexte de capture de données modifiées actuel. Une fois cette opération effectuée, le numéro LSN maximal actuel de la table d’horodatage des LSN `sys.fn_cdc_get_max_lsn` devient le début de la plage de traitement suivante. Cette opération requiert une connexion à la base de données source.|  
|MarkInitialLoadStart|Cette opération est utilisée au début d'un package de charge initiale pour enregistrer le NSE actuel dans la base de données source avant que le package de charge initiale commence à lire les tables sources. Cette opération requiert une connexion à la base de données source pour appeler `sys.fn_cdc_get_max_lsn`.<br /><br /> Si vous sélectionnez MarkInitialLoadStart quand vous travaillez sur la capture de données modifiées [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (autrement dit, hors d’Oracle), l’utilisateur spécifié dans le gestionnaire de connexions doit être db_owner ou sysadmin.|  
|MarkInitialLoadEnd|Cette opération est utilisée à la fin d'un package de charge initiale pour enregistrer le NSE actuel dans la base de données source une fois que le package de charge initiale a fini de lire les tables sources. Ce NSE est déterminé en enregistrant l'heure à laquelle cette opération s'est produite, puis en interrogeant la table de mappage `cdc.lsn_time_`dans la base de données de capture de données modifiées afin de rechercher une modification survenue après cette heure.<br /><br /> Si vous sélectionnez MarkInitialLoadEnd quand vous travaillez sur la capture de données modifiées [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (autrement dit, hors d’Oracle), l’utilisateur spécifié dans le gestionnaire de connexions doit être db_owner ou sysadmin.|  
|MarkCdcStart|Cette opération est utilisée lorsque la charge initiale est effectuée à partir d'une base de données par instantané. Dans ce cas, le traitement des modifications doit démarrer immédiatement après le NSE de l'instantané. Vous pouvez spécifier le nom de la base de données par instantané à utiliser et la tâche de contrôle de capture de données modifiées qui interroge [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] pour connaître le NSE de l'instantané. Vous avez également la possibilité de spécifier directement le NSE de l'instantané.<br /><br /> Si vous sélectionnez MarkCdcStart quand vous travaillez sur la capture de données modifiées [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (autrement dit, hors d’Oracle), l’utilisateur spécifié dans le gestionnaire de connexions doit être db_owner ou sysadmin.|  
  
 Les opérations suivantes sont utilisées pour gérer la plage de traitement :  
  
|Opération|Description|  
|---------------|-----------------|  
|GetProcessingRange|Cette opération est utilisée avant d'appeler le flux de données qui utilise le flux de données de la source CDC. Elle établit une plage de numéros LSN que le flux de données de la source CDC lit lorsqu'il est appelé. La plage est stockée dans une variable de package SSIS qui est utilisée par la source CDC pendant le traitement du flux de données.<br /><br /> Pour plus d’informations sur les états stockés, consultez [Définir une variable d’état](../data-flow/define-a-state-variable.md).|  
|MarkProcessedRange|Cette opération est exécutée après que chaque exécution de la capture de données modifiées (une fois le flux de données de capture de données modifiées terminé avec succès) pour consigner le dernier NSE qui a été entièrement traité dans le cadre de l'exécution de la capture de données modifiées. Lors de la prochaine exécution de GetProcessingRange, cette position constitue le début de la plage de traitement.|  
  
## <a name="handling-cdc-state-persistency"></a>Gestion de la permanence de l'état de capture de données modifiées  
 La tâche de contrôle de capture de données modifiées conserve un état permanent entre les activations. Les informations stockées dans l'état de capture de données modifiées sont utilisées pour déterminer et gérer la plage de traitement pour le package de capture de données modifiées et pour détecter les conditions d'erreur. L'état permanent est stocké sous forme de chaîne. Pour plus d’informations, consultez [Définir une variable d’état](../data-flow/define-a-state-variable.md).  
  
 La tâche de contrôle de capture de données modifiées prend en charge deux types de permanence d'état :  
  
-   Permanence d'état manuelle : dans ce cas, la tâche de contrôle de capture de données modifiées gère l'état stocké dans une variable de package, mais le développeur de package doit lire la variable dans un stockage permanent avant d'appeler le contrôle de capture de données modifiées, puis la réécrire dans ce stockage permanent après le dernier appel du contrôle de capture de données modifiées et une fois l'exécution de la capture de données modifiées terminée.  
  
-   Permanence d'état automatique : l'état de capture de données modifiées est stocké dans une table dans une base de données. L’état est stocké sous un nom fourni par la propriété **StateName** dans une table nommée de la propriété **Table à utiliser pour le stockage de l’état** , qui se trouve dans un gestionnaire de connexions sélectionné pour le stockage de l’état. La valeur par défaut est le gestionnaire de connexions source, mais la pratique courante consiste à utiliser le gestionnaire de connexions cible. La tâche de contrôle de capture de données modifiées met à jour la valeur d'état dans la table d'état et celle-ci est validée dans le cadre de la transaction en cours.  
  
## <a name="error-handling"></a>Gestion des erreurs  
 La tâche de contrôle de capture de données modifiées peut signaler une erreur dans les conditions suivantes :  
  
-   Elle ne parvient pas à lire l'état de capture de données modifiées permanent ou la mise à jour de l'état permanent échoue.  
  
-   Elle ne parvient pas à lire les informations du NSE actuel dans la base de données source.  
  
-   La lecture de l'état de capture de données modifiées n'est pas cohérente.  
  
 Dans toutes ces situations, la tâche de contrôle de capture de données modifiées signale une erreur qui peut être gérée de la manière dont SSIS gère habituellement les erreurs de flux de contrôle.  
  
 La tâche de contrôle de capture de données modifiées peut également signaler un avertissement lorsque l'opération Obtenir la plage de traitement est appelée directement après une autre opération Obtenir la plage de traitement sans que Marquer la plage traitée soit appelé. Ceci indique que l'exécution précédente a échoué ou qu'un autre package de capture de données modifiées s'exécute peut-être avec le même nom d'état de capture de données modifiées.  
  
## <a name="configuring-the-cdc-control-task"></a>Configuration de la tâche de contrôle de capture de données modifiées  
 Vous pouvez définir les propriétés par le biais du concepteur SSIS ou par programmation.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Éditeur de tâche de contrôle CDC](../cdc-control-task-editor.md)  
  
-   [Propriétés personnalisées de la tâche de contrôle de capture de données modifiées](cdc-control-task-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 [Définir une variable d’état](../data-flow/define-a-state-variable.md)  
  
## <a name="related-content"></a>Contenu associé  
  
-   Article technique, [Installation du service de capture de données modifiées Microsoft SQL Server 2012 pour Oracle par Attunity](http://go.microsoft.com/fwlink/?LinkId=252958), sur social.technet.microsoft.com.  
  
-   Article technique, [Résolution des problèmes de configuration dans le service de capture de données modifiées Microsoft SQL Server pour Oracle par Attunity](http://go.microsoft.com/fwlink/?LinkId=252960), sur social.technet.microsoft.com.  
  
-   Article technique, [Dépannage des erreurs d'instance du service de capture de données modifiées Microsoft SQL Server pour Oracle par Attunity](http://go.microsoft.com/fwlink/?LinkId=252961), sur social.technet.microsoft.com.  
  
  
