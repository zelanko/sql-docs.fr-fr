---
title: "SQL Server Integration Services (SSIS) de montée en charge principale | Documents Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 1672c015186998065b5d6dc95897147aa11d14ec
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-scale-out-master"></a>Integration Services (SSIS) Scale Out Master
Scale Out Master gère le système Scale Out par le biais du catalogue SSISDB et du service Scale Out Master. 

Le catalogue SSISDB stocke toutes les informations sur les Scale Out Workers, les packages et les exécutions. Il fournit l’interface pour activer un Scale Out Worker et exécuter des packages dans Scale Out. Pour plus d’informations, consultez [Procédure pas à pas : Configurer Integration Services Scale Out](walkthrough-set-up-integration-services-scale-out.md) et [Exécuter des packages dans Integration Services](run-packages-in-integration-services-ssis-scale-out.md).

Le service Scale Out Master est un service Windows responsable de la communication avec les Scale Out Workers. Il échange l’état d’exécution des packages avec les Scale Out Workers par le biais du protocole HTTPS et opère sur les données dans SSISDB. 

## <a name="scale-out-related-sql-views-and-stored-procedures-in-ssisdb"></a>Monter en charge les vues SQL et procédures stockées dans SSISDB

#### <a name="views"></a>Vues :
[[catalog].[master_properties]](../../integration-services/system-views/catalog-master-properties-ssisdb-database.md), [[catalog].[worker_agents]](../../integration-services/system-views/catalog-worker-agents-ssisdb-database.md).

#### <a name="stored-procedures"></a>Procédures stockées :

- Pour la gestion de Scale Out Worker :  
 [[catalog].[disable_worker_agent]](../../integration-services/system-stored-procedures/catalog-disable-worker-agent-ssisdb-database.md), [[catalog].[enable_worker_agent]](../../integration-services/system-stored-procedures/catalog-enable-worker-agent-ssisdb-database.md).
- Pour l’exécution des packages dans Scale Out :   
[[catalog].[create_execution]](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md), [[catalog].[add_execution_worker]](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md), [[catalog].[start_execution]](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md).   

## <a name="configure-sql-server-integration-services-scale-out-master-service"></a>Configurer le service SQL Server Integration Services Scale Out Master
Vous pouvez configurer le service Scale Out Master à l’aide du fichier \<lecteur\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config. Vous devez redémarrer le service après la mise à jour du fichier de configuration.


Configuration  |Description  |Valeur par défaut  
---------|---------|---------
PortNumber|Numéro de port réseau utilisé pour communiquer avec un Scale Out Worker.|8391         
SSLCertThumbprint|Empreinte numérique du certificat SSL utilisé pour protéger les communications avec un Scale Out Worker.|Empreinte numérique du certificat SSL spécifié pendant l’installation de Scale Out Master.         
SqlServerName|Le nom de la [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] qui contient le catalogue SSISDB. Par ex. Nom_serveur\\\\InstanceName.|Le nom du serveur SQL qui est installé avec la mise à l’échelle des maître.         
CleanupCompletedJobsIntervalInMs|Intervalle de nettoyage des tâches d’exécution terminées, en millisecondes.|43200000         
DealWithExpiredTasksIntervalInMs|Intervalle de traitement des tâches d’exécution ayant expiré, en millisecondes.|300000
MasterHeartbeatIntervalInMs|Intervalle de pulsation de Scale Out Master, en millisecondes. Spécifie l’intervalle auquel Scale Out Master met à jour son état de connexion dans le catalogue SSISDB.|30 000
SqlConnectionTimeoutInSecs|Le délai de connexion SQL en secondes lors de la connexion à SSISDB.|15        

## <a name="view-scale-out-master-service-log"></a>Afficher le journal du service Scale Out Master
Le fichier journal du service échelle Out principale se trouve dans le \<pilote\>: \Users\\*[compte]*chemin d’accès du dossier \AppData\Local\SSIS\ScaleOut\Master. 

Le *[compte]* fait référence au compte de service de mise à l’échelle des principale en cours d’exécution. Par défaut, ce compte est SSISScaleOutMaster140.

