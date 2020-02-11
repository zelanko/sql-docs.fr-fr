---
title: Modèles de SQL Server Profiler | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- default SQL Server Profiler templates
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- predefined templates [SQL Server Profiler]
- SQL Server Profiler, templates
ms.assetid: b674e491-dc58-47a1-acdd-7028e9a201fc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5cac924e926d03dffb9116e5ce7194bb784d45fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68186145"
---
# <a name="sql-server-profiler-templates"></a>Modèles du Générateur de profils SQL Server
  Vous pouvez utiliser le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour créer des modèles qui définissent les classes d'événements et les colonnes de données à inclure dans les traces. Après avoir défini et enregistré le modèle, vous pouvez exécuter une trace qui enregistre les données de chaque classe d'événements sélectionnée. Vous pouvez utiliser un modèle sur de nombreuses traces ; le modèle lui-même n'est pas exécuté.  
  
 
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] fournit des modèles de traces prédéfinis qui permettent de configurer aisément les classes d’événements dont vous aurez vraisemblablement besoin pour des traces spécifiques. Le modèle standard, par exemple, permet de créer une trace générique pour enregistrer les connexions, les déconnexions, les traitements terminés et les informations de connexion. Vous pouvez utiliser ce modèle pour exécuter des traces sans modification ou comme point de départ pour d'autres modèles avec des configurations d'événements différents.  
  
> [!NOTE]  
>  Outre les traces des modèles prédéfinis, le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] permet de créer des traces depuis un modèle vierge qui ne contient aucune classe d'événements par défaut. Ce modèle peut s'avérer utile lorsqu'une trace planifiée ne ressemble à aucune des configurations des modèles prédéfinis.  
  
 
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] peut tracer divers types de serveurs. Par exemple, tracez [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Toutefois, les classes d'événements qui peuvent être incluses ne sont pas les mêmes pour chaque type de serveur. Par conséquent, le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] gère différents modèles pour différents serveurs et rend disponible le modèle spécifique qui correspond au type de serveur sélectionné.  
  
## <a name="predefined-templates"></a>Modèles prédéfinis  
 Outre le modèle standard (celui par défaut), le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] contient divers modèles prédéfinis permettant de surveiller certains types d'événements. Le tableau ci-dessous répertorie les modèles prédéfinis, leur fonction et les classes d'événements pour lesquelles ils capturent des informations.  
  
|Nom du modèle|Fonction|Classes d’événements|  
|-------------------|----------------------|-------------------|  
|SP_Counts|Capture le comportement de l'exécution des procédures stockées dans le temps.|**SP : démarrage**|  
|standard|Point de départ générique de création d'une trace. Capture toutes les procédures stockées et tous les traitements [!INCLUDE[tsql](../../includes/tsql-md.md)] exécutés. Permet de surveiller l'activité générale du serveur de base de données.|**Audit Login**<br /><br /> **Audit Logout**<br /><br /> **ExistingConnection**<br /><br /> **RPC : terminé**<br /><br /> **SQL : BatchCompleted**<br /><br /> **SQL : BatchStarting**|  
|TSQL|Capture toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] soumises à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par les clients, ainsi que l'heure de leur émission. Permet de déboguer les applications clientes.|**Audit Login**<br /><br /> **Audit Logout**<br /><br /> **ExistingConnection**<br /><br /> **RPC : démarrage en cours**<br /><br /> **SQL : BatchStarting**|  
|TSQL_Duration|Capture toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] soumises à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par les clients, leur délai d'exécution (en millisecondes) et les regroupe en fonction de leur durée. Permet d'identifier les requêtes lentes.|**RPC : terminé**<br /><br /> **SQL : BatchCompleted**|  
|TSQL_Grouped|Capture toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] soumises à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l’heure à laquelle elles ont été émises. Regroupe les informations en fonction du client ou de l'utilisateur qui a émis l'instruction. Permet d'analyser les requêtes d'un client ou d'un utilisateur.|**Audit Login**<br /><br /> **Audit Logout**<br /><br /> **ExistingConnection**<br /><br /> **RPC : démarrage en cours**<br /><br /> **SQL : BatchStarting**|  
|TSQL_Locks|Capture toutes les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] soumises à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par les clients, ainsi que les événements de verrou exceptionnels. Permet de dépanner les blocages, les délais d'expiration de verrou et les événements d'escalade de verrous.|**Rapport de processus bloqué**<br /><br /> **SP : StmtCompleted**<br /><br /> **SP : StmtStarting**<br /><br /> **SQL:StmtCompleted**<br /><br /> **SQL:StmtStarting**<br /><br /> **Graphique de blocage**<br /><br /> **Verrou : annuler**<br /><br /> **Verrou : blocage**<br /><br /> **Verrou : chaîne d’interblocage**<br /><br /> **Verrou : escalade**<br /><br /> **Verrou : Timeout (délai d’expiration>0)**|  
|TSQL_Replay|Capture des informations détaillées sur les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] , qui sont nécessaires si la trace doit être réexécutée. Permet d'effectuer un paramétrage itératif, tel qu'un test d'évaluation.|**CursorClose**<br /><br /> **CursorExecute**<br /><br /> **CursorOpen**<br /><br /> **CursorPrepare**<br /><br /> **CursorUnprepare**<br /><br /> **Audit Login**<br /><br /> **Audit Logout**<br /><br /> **Connexion existante**<br /><br /> **Paramètre de sortie RPC**<br /><br /> **RPC : terminé**<br /><br /> **RPC : démarrage en cours**<br /><br /> **Exec Prepared SQL**<br /><br /> **Préparer SQL**<br /><br /> **SQL : BatchCompleted**<br /><br /> **SQL : BatchStarting**|  
|TSQL_SPs|Capture des informations détaillées sur toutes les procédures stockées en cours d'exécution. Permet d'analyser les étapes composantes des procédures stockées. Ajoutez l’événement **SP:Recompile** si vous pensez que des procédures sont recompilées.|**Audit Login**<br /><br /> **Audit Logout**<br /><br /> **ExistingConnection**<br /><br /> **RPC : démarrage en cours**<br /><br /> **SP : terminé**<br /><br /> **SP : démarrage**<br /><br /> **SP : StmtStarting**<br /><br /> **SQL : BatchStarting**|  
|Réglage|Capture des informations sur l'exécution des procédures stockées et des traitements [!INCLUDE[tsql](../../includes/tsql-md.md)] . Permet de produire des résultats de trace que l'Assistant Paramétrage du [!INCLUDE[ssDE](../../includes/ssde-md.md)] peut utiliser comme charge de travail pour régler les bases de données.|**RPC : terminé**<br /><br /> **SP : StmtCompleted**<br /><br /> **SQL : BatchCompleted**|  
  
 Pour plus d’informations sur les classes d’événements, consultez [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
## <a name="default-template"></a>Modèle par défaut  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]désigne automatiquement le modèle **standard** comme modèle par défaut appliqué à toute nouvelle trace. Toutefois, vous pouvez remplacer le modèle par défaut par n'importe quel autre modèle prédéfini ou défini par l'utilisateur. Pour modifier le modèle par défaut, cochez la case **Utiliser comme modèle par défaut pour le type de serveur sélectionné** lorsque vous créez ou modifiez un modèle en utilisant l’onglet **Général** de la boîte de dialogue **Propriétés du modèle de trace** .  
  
 Pour accéder à la boîte de dialogue **Propriétés du modèle de trace** , dans le menu [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **de** , choisissez **Modèles**, puis cliquez sur **Nouveau modèle** ou **Modifier le modèle**.  
  
> [!NOTE]  
>  Le modèle par défaut est spécifique à un type de serveur donné. Le remplacement du modèle par défaut d'un type de serveur n'affecte pas le modèle par défaut d'un autre type de serveur. Pour plus d’informations sur le paramétrage du modèle par défaut d’un serveur, consultez [Définir les valeurs par défaut des définitions de trace &#40;SQL Server Profiler&#41;](set-trace-definition-defaults-sql-server-profiler.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un modèle de trace &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md)   
 [Modifier un modèle de trace &#40;SQL Server Profiler&#41;](../../database-engine/modify-a-trace-template-sql-server-profiler.md)   
 [Exporter un modèle de trace &#40;SQL Server Profiler&#41;](export-a-trace-template-sql-server-profiler.md)   
 [Importer un modèle de trace &#40;SQL Server Profiler&#41;](import-a-trace-template-sql-server-profiler.md)  
  
  
