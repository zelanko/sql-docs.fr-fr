---
title: Éditeur de tâche de contrôle CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdccontroltask.config.f1
ms.assetid: 4f09d040-9ec8-4aaa-b684-f632d571f0a8
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 97d47bda8f3ceb98449392cda22d2a8152e08b7f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201299"
---
# <a name="cdc-control-task-editor"></a>Éditeur de tâche de contrôle CDC
  Utilisez la boîte de dialogue **Éditeur de tâche de contrôle CDC** pour configurer la tâche de contrôle CDC. La configuration de la tâche de contrôle CDC inclut la définition d'une connexion à la base de données CDC, l'opération de la tâche CDC et des informations de gestion d'état.  
  
 Pour en savoir plus sur la tâche de contrôle CDC, consultez [CDC Control Task](control-flow/cdc-control-task.md).  
  
 **Pour ouvrir l'Éditeur de tâche de contrôle CDC**  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] doté de la tâche de contrôle CDC.  
  
2.  Sous l’onglet **Flux de contrôle** , double-cliquez sur la tâche de contrôle CDC.  
  
## <a name="options"></a>Options  
 **Gestionnaire de connexions ADO.NET de base de données CDC SQL Server**  
 Sélectionnez un gestionnaire de connexions existant dans la liste ou cliquez sur **Nouveau** pour créer une connexion. La connexion doit être établie avec une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] activée pour la capture de données modifiées et dans laquelle la table de modifications sélectionnée est localisée.  
  
 **Opération de contrôle de capture de données modifiées**  
 Sélectionnez l'opération à exécuter pour cette tâche. Toutes les opérations utilisent la variable d'état qui est stockée dans une variable de package SSIS qui stocke l'état et le passe entre les différents composants du package.  
  
-   **Marquer le début de la charge initiale**: cette opération est utilisée en exécutant une charge initiale d'une base de données active sans instantané. Elle est invoquée au début d'un package de chargement initial pour enregistrer le numéro LSN actuel dans la base de données source avant que le package de chargement initial commence à lire les tables sources. Cela requiert une connexion à la base de données source.  
  
     Si vous sélectionnez **Marquer le début de la charge initiale** quand vous travaillez sur la capture de données modifiées [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] (autrement dit, hors d’Oracle) l’utilisateur spécifié dans le gestionnaire de connexions doit être  **db_owner** ou **sysadmin**.  
  
-   **Marquer la fin de la charge initiale**: cette opération est utilisée en exécutant une charge initiale d'une base de données active sans instantané. Elle est invoquée à la fin d'un package de chargement initial pour enregistrer le numéro LSN actuel dans la base de données source une fois que le package de chargement initial a fini de lire les tables sources. Ce numéro LSN est déterminé en enregistrant l'heure à laquelle cette opération s'est produite, puis en interrogeant la table de mappage `cdc.lsn_time_`dans la base de données CDC afin de rechercher une modification survenue après cette heure.  
  
     Si vous sélectionnez **Marquer la fin de la charge initiale** quand vous travaillez sur la capture de données modifiées [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] (autrement dit, hors d’Oracle) l’utilisateur spécifié dans le gestionnaire de connexions doit être  **db_owner** ou **sysadmin**.  
  
-   **Marquer le début CDC**: cette opération est utilisée lorsque la charge initiale est effectuée à partir d'un fichier de base de données d'instantanés ou d'une base de données d'arrêt inactive. Elle est appelée à n'importe quel stade du package de charge initiale. L'opération accepte un paramètre qui peut être un numéro LSN d'instantané, un nom de base de données d'instantanés (de laquelle le numéro LSN d'instantané dérive automatiquement) ou qui peut être laissé vide, auquel cas le numéro LSN de la base de données actuelle est utilisé comme dernier numéro LSN pour le package de traitement des modifications.  
  
     Cette opération est utilisée à la place des opérations Marquer le début/la fin de la charge initiale.  
  
     Si vous sélectionnez **Marquer le début CDC** quand vous travaillez sur la capture de données modifiées [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] (autrement dit, hors d’Oracle) l’utilisateur spécifié dans le gestionnaire de connexions doit être  **db_owner** ou **sysadmin**.  
  
-   **Get processing range**: cette opération est utilisée dans un package de traitement des modifications avant d'appeler le flux de données qui utilise le flux de données source CDC. Elle établit une plage de numéros LSN que le flux de données de la source CDC lit lorsqu'il est appelé. La plage est stockée dans une variable de package SSIS qui est utilisée par la source CDC pendant le traitement du flux de données.  
  
     Pour plus d’informations sur les états CDC stockés, consultez [Définir une variable d’état](data-flow/define-a-state-variable.md).  
  
-   **Marquer la plage traitée**: cette opération est utilisée dans un package de traitement des modifications à la fin d’une exécution CDC (après que le flux de données CDC s’est terminé correctement) pour inscrire le dernier numéro LSN qui était complètement traité dans l’exécution CDC. Lors de la prochaine exécution de `GetProcessingRange` , cette position détermine le début de la prochaine plage de traitement.  
  
-   **Réinitialiser l'état CDC**: cette opération est utilisée pour réinitialiser l'état de capture de données modifiées (CDC) permanent associé au contexte CDC actuel. Une fois cette opération effectuée, le numéro LSN maximal actuel de la table d’horodatage des LSN `sys.fn_cdc_get_max_lsn` devient le début de la plage de traitement suivante. Cette opération requiert une connexion à la base de données source.  
  
     Cette opération est notamment utilisée lorsque vous souhaitez traiter uniquement les enregistrements de modifications récents et ignorer tous les anciens enregistrements de modifications.  
  
 **Variable contenant l'état CDC**  
 Sélectionnez la variable de package SSIS qui stocke les informations d'état de l'opération de tâche. Vous devez définir une variable avant de commencer. Si vous sélectionnez **Persistance d'état automatique**, la variable d'état est chargée et enregistrée automatiquement.  
  
 Pour plus d’informations sur la définition de la variable d’état, consultez [Définir une variable d’état](data-flow/define-a-state-variable.md).  
  
 **Numéro séquentiel dans le journal (LSN) SQL Server pour démarrer le nom CDC/instantané :**  
 Entrez le numéro LSN de la base de données source ou de la base de données d'instantanés à partir de laquelle la charge initiale est effectuée pour déterminer le début de la capture de données modifiées. Le numéro est disponible uniquement si **Opération de contrôle CDC** est défini sur **Marquer le début CDC**.  
  
 Pour plus d'informations sur ces opérations, consultez [CDC Control Task](control-flow/cdc-control-task.md).  
  
 **Stockage automatique de l'état dans une table de base de données**  
 Activez cette case à cocher pour que la tâche de contrôle CDC gère automatiquement le chargement et le stockage de l'état CDC dans une table d'états contenue dans la base de données spécifiée. Si cette case n'est pas sélectionnée, le développeur doit charger l'état CDC au démarrage du package et l'enregistrer dès qu'il change.  
  
 **Gestionnaire de connexions de la base de données où l'état est stocké**  
 Sélectionnez un gestionnaire de connexions ADO.NET existant dans la liste ou cliquez sur Nouveau pour créer une nouvelle connexion. La connexion concerne une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui contient la table State. La table State contient les informations d'état.  
  
 Ces informations sont disponibles uniquement si vous avez sélectionné **Persistance d'état automatique** et il s'agit d'un paramètre obligatoire.  
  
 **Table à utiliser pour stocker l'état**  
 Tapez le nom de la table d'état à utiliser pour stocker l'état CDC. La table spécifiée doit être composée de deux colonnes appelées **name** et **state** avec le type de données **varchar (256)**.  
  
 Vous pouvez éventuellement sélectionner **Nouveau** pour obtenir un script SQL qui génère une nouvelle table d'état avec les colonnes requises. Lorsque **Persistance d'état automatique** est sélectionné, le développeur doit créer une table d'état en fonction des spécifications ci-dessus.  
  
 Ces informations sont disponibles uniquement si vous avez sélectionné **Persistance d'état automatique** et il s'agit d'un paramètre obligatoire.  
  
 **Nom d'état**  
 Entrez le nom à associer à l'état CDC persistant. La charge complète et les packages CDC qui fonctionnent avec le même contexte CDC auront un nom d'état commun. Ce nom est utilisé pour surveiller la ligne d'état dans la table d'état.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés personnalisées de la tâche de contrôle de capture de données modifiées](control-flow/cdc-control-task-custom-properties.md)  
  
  
