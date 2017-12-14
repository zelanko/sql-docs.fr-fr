---
title: SQL Server Integration Services (SSIS) Scale Out Master | Microsoft Docs
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 07cd19a5e7a53e824d2bed3a2e2943efd7ef867b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="integration-services-ssis-scale-out-master"></a>Integration Services (SSIS) Scale Out Master
Scale Out Master gère le système Scale Out par le biais du catalogue SSISDB et du service Scale Out Master. 

Le catalogue SSISDB stocke toutes les informations sur les Scale Out Workers, les packages et les exécutions. Il fournit l’interface pour activer un Scale Out Worker et exécuter des packages dans Scale Out. Pour plus d’informations, consultez [Procédure pas à pas : Configurer Integration Services Scale Out](walkthrough-set-up-integration-services-scale-out.md) et [Exécuter des packages dans Integration Services](run-packages-in-integration-services-ssis-scale-out.md).

Le service Scale Out Master est un service Windows responsable de la communication avec les Scale Out Workers. Il échange l’état d’exécution des packages avec les Scale Out Workers par le biais du protocole HTTPS et opère sur les données dans SSISDB. 

## <a name="scale-out-related-sql-views-and-stored-procedures-in-ssisdb"></a>Procédures stockées et vues SQL liées à Scale Out dans SSISDB

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
SqlServerName|Nom du serveur [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] qui contient le catalogue SSISDB. Par ex. nom_serveur\\\\nom_instance.|Nom du serveur SQL Server installé avec Scale Out Master.         
CleanupCompletedJobsIntervalInMs|Intervalle de nettoyage des tâches d’exécution terminées, en millisecondes.|43200000         
DealWithExpiredTasksIntervalInMs|Intervalle de traitement des tâches d’exécution ayant expiré, en millisecondes.|300000
MasterHeartbeatIntervalInMs|Intervalle de pulsation de Scale Out Master, en millisecondes. Spécifie l’intervalle auquel Scale Out Master met à jour son état de connexion dans le catalogue SSISDB.|30 000
SqlConnectionTimeoutInSecs|Délai en secondes de la connexion SQL à SSISDB.|15        

## <a name="view-scale-out-master-service-log"></a>Afficher le journal du service Scale Out Master
Le fichier journal du service Scale Out Master se trouve dans le dossier \<lecteur\>:\Users\\*[compte]*\AppData\Local\SSIS\ScaleOut\Master. 

*[compte]* fait référence au compte exécutant le service Scale Out Master. Par défaut, ce compte est SSISScaleOutMaster140.
