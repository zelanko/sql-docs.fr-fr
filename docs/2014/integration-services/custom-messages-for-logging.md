---
title: Custom Messages for Logging | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], custom
- writing log entries
- SSIS packages, logs
- custom messages for logging [Integration Services]
ms.assetid: 3c74bba9-02b7-4bf5-bad5-19278b680730
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f55c99ad60dd449a3f5b591adf09f325127258b6
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53366571"
---
# <a name="custom-messages-for-logging"></a>Messages personnalisés pour la journalisation
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit un ensemble complet d'événements personnalisés permettant d'écrire des entrées de journal pour des packages et bon nombre de tâches. Vous pouvez utiliser ces entrées pour enregistrer des informations détaillées sur l'avancement, les résultats et les problèmes d'exécution en enregistrant des événements prédéfinis ou des messages définis par l'utilisateur en vue d'une analyse ultérieure. Vous pouvez ainsi enregistrer l'heure de début et de fin d'une insertion en bloc pour identifier des problèmes de performances lors de l'exécution du package.  
  
 Les entrées de journal personnalisées constituent un ensemble qui se distingue de l'ensemble des événements de journalisation standard, disponibles pour les packages et tous les conteneurs et tâches. Ces entrées sont conçues pour capturer des informations utiles sur une tâche spécifique d'un package. Par exemple, l'une des entrées de journal personnalisées pour la tâche d'exécution de requêtes SQL consigne l'instruction SQL que la tâche exécute dans le journal.  
  
 Toutes les entrées de journal contiennent des informations de date et d'heure, y compris les entrées qui sont écrites automatiquement au début et à la fin d'un package. La plupart des événements de journal écrivent plusieurs entrées dans le journal. C'est généralement le cas lorsque l'événement comprend plusieurs phases. Par exemple, l'événement du journal `ExecuteSQLExecutingQuery` consigne trois entrées : la première après que la tâche acquiert une connexion à la base de données, la seconde après que la tâche commence à préparer l'instruction SQL et la troisième à la fin de l'exécution de l'instruction SQL.  
  
 Les objets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] suivants possèdent des entrées de journal personnalisées :  
  
 [Package](#Package)  
  
 [Tâche d'insertion en bloc](#BulkInsert)  
  
 [tâche de flux de données](#DataFlow)  
  
 [Tâche d'exécution DTS 2000](#ExecuteDTS200)  
  
 [Tâche d'exécution de processus](#ExecuteProcess)  
  
 [Tache d'exécution de requêtes SQL](#ExecuteSQL)  
  
 [Tâches du système de fichiers](#FileSystem)  
  
 [Tâche FTP](#FTP)  
  
 [Tâche MSMQ](#MessageQueue)  
  
 [Tâche de script](#Script)  
  
 [Tâche Envoyer un message](#SendMail)  
  
 [Tâche de transfert de bases de données](#TransferDatabase)  
  
 [Tâche de transfert de messages d'erreur](#TransferErrorMessages)  
  
 [Tâche de transfert de travaux](#TransferJobs)  
  
 [Tâche de transfert de connexions](#TransferLogins)  
  
 [Tâche de transfert de procédures stockées de master](#TransferMasterStoredProcedures)  
  
 [Tâche de transfert d'objets SQL Server](#TransferSQLServerObjects)  
  
 [Tâche de services Web](#WebServices)  
  
 [Tâche Lecteur de données WMI](#WMIDataReader)  
  
 [Tâche Observateur d'événement WMI](#WMIEventWatcher)  
  
 [Tâche XML](#XML)  
  
## <a name="log-entries"></a>Entrées du journal  
  
###  <a name="Package"></a> Package  
 Le tableau suivant répertorie les entrées de journal personnalisées pour les packages.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`PackageStart`|Indique que le package a commencé à s'exécuter.<br /><br /> Remarque : Cette entrée de journal est automatiquement écrite au journal. Vous ne pouvez pas l'exclure.|  
|`PackageEnd`|Indique que le package est terminé.<br /><br /> Remarque : Cette entrée de journal est automatiquement écrite au journal. Vous ne pouvez pas l'exclure.|  
|`Diagnostic`|Fournit des informations sur la configuration système qui affecte l'exécution du package, notamment le nombre d'exécutables pouvant s'exécuter simultanément.<br /><br /> L'entrée de journal `Diagnostic` inclut également des entrées avant et après les appels effectués auprès des fournisseurs de données externes. Pour plus d’informations, voir [Outils de dépannage de la connectivité des packages](troubleshooting/troubleshooting-tools-for-package-connectivity.md).|  
  
###  <a name="BulkInsert"></a> Tâche d'insertion en bloc  
 Le tableau suivant répertorie les entrées de journal personnalisées de la tâche d'insertion en bloc.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`DTSBulkInsertTaskBegin`|Indique que l'insertion en bloc a commencé.|  
|`DTSBulkInsertTaskEnd`|Indique que l'insertion en bloc est terminée.|  
|`DTSBulkInsertTaskInfos`|Fournit des informations détaillées concernant la tâche.|  
  
###  <a name="DataFlow"></a> tâche de flux de données  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche de flux de données.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`BufferSizeTuning`|Indique que la tâche de flux de données a modifié la taille du tampon. L'entrée de journal décrit les raisons de cette modification de taille et indique la nouvelle taille temporaire du tampon.|  
|`OnPipelinePostEndOfRowset`|Indique qu'un composant a reçu son signal de fin d'ensemble de lignes, défini par le dernier appel de la méthode `ProcessInput`. Une entrée est écrite pour chaque composant du flux de données qui traite l'entrée. L'entrée inclut le nom du composant.|  
|`OnPipelinePostPrimeOutput`|Indique que le composant a terminé son dernier appel de la méthode `PrimeOutput`. Selon le flux de données, plusieurs entrées de journal peuvent être écrites. Si le composant est une source, cela signifie que le composant a terminé le traitement des lignes.|  
|`OnPipelinePreEndOfRowset`|Indique qu'un composant est sur le point de recevoir son signal de fin d'ensemble de lignes, défini par le dernier appel de la méthode `ProcessInput`. Une entrée est écrite pour chaque composant du flux de données qui traite l'entrée. L'entrée inclut le nom du composant.|  
|`OnPipelinePrePrimeOutput`|Indique que le composant est sur le point de recevoir son appel de la méthode `PrimeOutput`. Selon le flux de données, plusieurs entrées de journal peuvent être écrites.|  
|`OnPipelineRowsSent`|Indique le nombre de lignes fournies à une entrée de composant par un appel de la méthode `ProcessInput`. L'entrée du journal inclut le nom du composant.|  
|`PipelineBufferLeak`|Donne des informations sur tout composant qui maintient l'activité des tampons après la fermeture du gestionnaire de tampons. Cela signifie que des ressources des tampons n'ont pas été libérées et qu'elles peuvent provoquer des fuites de mémoire. L'entrée du journal fournit le nom du composant et l'ID du tampon.|  
|`PipelineExecutionPlan`|Indique le plan d'exécution du flux de données. L'entrée du journal donne des informations sur la façon dont les tampons sont envoyés aux composants. Ces informations, conjuguées à l'entrée PipelineExecutionTrees, décrivent ce qui se passe dans la tâche.|  
|`PipelineExecutionTrees`|Indique les arborescences d'exécution de la disposition du flux de données. Le planificateur du moteur du flux de données utilise les arborescences pour construire le plan d’exécution du flux de données.|  
|`PipelineInitialization`|Donne des informations d'initialisation relatives à la tâche. Ces informations incluent les répertoires à utiliser pour le stockage temporaire des données blob, la taille par défaut de la mémoire tampon, ainsi que le nombre de lignes contenues dans une mémoire tampon. Selon la configuration de la tâche de flux de données, plusieurs entrées de journal peuvent être écrites.|  
  
###  <a name="ExecuteDTS200"></a> Tâche d'exécution DTS 2000  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche d'exécution DTS 2000.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`ExecuteDTS80PackageTaskBegin`|Indique que la tâche a commencé l'exécution d'un package DTS 2000.|  
|`ExecuteDTS80PackageTaskEnd`|Indique que la tâche est terminée.<br /><br /> Remarque : Il est possible que le package DTS 2000 continue à s'exécuter à la fin de la tâche.|  
|`ExecuteDTS80PackageTaskTaskInfo`|Fournit des informations détaillées concernant la tâche.|  
|`ExecuteDTS80PackageTaskTaskResult`|Indique le résultat d'exécution du package DTS 2000 que la tâche a exécuté.|  
  
###  <a name="ExecuteProcess"></a> Tâche d'exécution de processus  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche d'exécution de processus.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`ExecuteProcessExecutingProcess`|Donne des informations sur le processus d'exécution de l'exécutable dont est chargé la tâche.<br /><br /> Deux entrées de journal sont écrites. La première contient des informations sur le nom et l'emplacement de l'exécutable que la tâche exécute, tandis que la seconde enregistre la sortie de l'exécutable.|  
|`ExecuteProcessVariableRouting`|Fournit des informations sur les variables qui doivent être acheminées vers l'entrée et les sorties de l'exécutable. Les entrées du journal sont écrites pour stdin (l'entrée), stdout (la sortie) et stderr (la sortie des erreurs).|  
  
###  <a name="ExecuteSQL"></a> Tache d'exécution de requêtes SQL  
 Le tableau suivant décrit les entrées de journal personnalisées pour la tâche d'exécution SQL.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`ExecuteSQLExecutingQuery`|Fournit des informations sur les phases d'exécution de l'instruction SQL. Des entrées de journal sont écrites lorsque la tâche acquiert la connexion à la base de données, lorsqu'elle commence à préparer l'instruction SQL et à la fin de l'exécution de l'instruction SQL. L'entrée de journal concernant la phase de préparation inclut l'instruction SQL que la tâche utilise.|  
  
###  <a name="FileSystem"></a> Tâches du système de fichiers  
 Le tableau suivant décrit l'entrée de journal personnalisée pour la tâche de système de fichiers.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`FileSystemOperation`|Indique l'opération que la tâche effectue. L'entrée de journal est écrite au démarrage de l'opération du système de fichiers et inclut des informations sur la source et la destination.|  
  
###  <a name="FTP"></a> Tâche FTP  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche FTP.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`FTPConnectingToServer`|Indique que la tâche a lancé une connexion au serveur FTP.|  
|`FTPOperation`|Indique le démarrage et le type d'une opération FTP effectuée par la tâche.|  
  
###  <a name="MessageQueue"></a> Tâche MSMQ  
 Le tableau suivant répertorie les entrées de journal personnalisées de la tâche MSMQ.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`MSMQAfterOpen`|Indique que la tâche a fini d'ouvrir la file d'attente des messages.|  
|`MSMQBeforeOpen`|Indique que la tâche a commencé l'ouverture de la file d'attente des messages.|  
|`MSMQBeginReceive`|Indique que la tâche a commencé la réception d'un message.|  
|`MSMQBeginSend`|Indique que la tâche a commencé l'envoi d'un message.|  
|`MSMQEndReceive`|Indique que la tâche a terminé la réception d'un message.|  
|`MSMQEndSend`|Indique que la tâche a terminé l’envoi d’un message.|  
|`MSMQTaskInfo`|Fournit des informations détaillées concernant la tâche.|  
|`MSMQTaskTimeOut`|Indique que le délai de la tâche a expiré.|  
  
###  <a name="Script"></a> Tâche de script  
 Le tableau suivant décrit l'entrée de journal personnalisée pour la tâche de script.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|Indique les résultats de l'implémentation de la journalisation dans le script. Une entrée de journal est écrite pour chaque appel de la méthode `Log` de l'objet `Dts`. L'entrée est écrite à l'exécution du code. Pour plus d’informations, consultez [Journalisation dans la tâche de script](extending-packages-scripting/task/logging-in-the-script-task.md).|  
  
###  <a name="SendMail"></a> Tâche Envoyer un message  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche Envoyer un message.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`SendMailTaskBegin`|Indique que la tâche a commencé l'envoi d'un message électronique.|  
|`SendMailTaskEnd`|Indique que la tâche a terminé l'envoi d'un message électronique.|  
|`SendMailTaskInfo`|Fournit des informations détaillées concernant la tâche.|  
  
###  <a name="TransferDatabase"></a> Tâche de transfert de bases de données  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche de transfert de bases de données.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`SourceDB`|Spécifie la base de données que la tâche a copiée.|  
|`SourceSQLServer`|Spécifie l'ordinateur à partir duquel la base de données a été copiée.|  
  
###  <a name="TransferErrorMessages"></a> Tâche de transfert de messages d'erreur  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche de transfert de messages d'erreur.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`TransferErrorMessagesTaskFinishedTransferringObjects`|Indique que la tâche a terminé le transfert des messages d'erreur.|  
|`TransferErrorMessagesTaskStartTransferringObjects`|Indique que la tâche a commencé le transfert des messages d'erreur.|  
  
###  <a name="TransferJobs"></a> Tâche de transfert de travaux  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche de transfert de travaux.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`TransferJobsTaskFinishedTransferringObjects`|Indique que la tâche a terminé le transfert des travaux de l’Agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|`TransferJobsTaskStartTransferringObjects`|Indique que la tâche a commencé le transfert des travaux de l'Agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
  
###  <a name="TransferLogins"></a> Tâche de transfert de connexions  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche de transfert de connexions.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`TransferLoginsTaskFinishedTransferringObjects`|Indique que la tâche a terminé le transfert des connexions.|  
|`TransferLoginsTaskStartTransferringObjects`|Indique que la tâche a commencé le transfert des connexions.|  
  
###  <a name="TransferMasterStoredProcedures"></a> Tâche de transfert de procédures stockées de master  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche de transfert de procédures stockées de master.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`TransferStoredProceduresTaskFinishedTransferringObjects`|Indique que la tâche a terminé le transfert des procédures stockées définies par l’utilisateur qui existent dans la base de données **master** .|  
|`TransferStoredProceduresTaskStartTransferringObjects`|Indique que la tâche a commencé le transfert des procédures stockées définies par l’utilisateur qui existent dans la base de données **master** .|  
  
###  <a name="TransferSQLServerObjects"></a> Tâche de transfert d'objets SQL Server  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche de transfert d'objets [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`TransferSqlServerObjectsTaskFinishedTransferringObjects`|Indique que la tâche a terminé le transfert des objets de base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
|`TransferSqlServerObjectsTaskStartTransferringObjects`|Indique que la tâche a commencé le transfert des objets de base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|  
  
###  <a name="WebServices"></a> Tâche de services Web  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche de services Web.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`WSTaskBegin`|La tâche a commencé à accéder à un service Web.|  
|`WSTaskEnd`|La tâche a terminé une méthode de service Web.|  
|`WSTaskInfo`|Donne des informations détaillées relatives à la tâche.|  
  
###  <a name="WMIDataReader"></a> Tâche Lecteur de données WMI  
 Le tableau suivant répertorie les entrées de journal personnalisées de la tâche Lecteur de données WMI.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`WMIDataReaderGettingWMIData`|Indique que la tâche a commencé la lecture des données WMI.|  
|`WMIDataReaderOperation`|Indique la requête WQL que la tâche a exécutée.|  
  
###  <a name="WMIEventWatcher"></a> Tâche Observateur d'événement WMI  
 Le tableau suivant répertorie les entrées de journal personnalisées de la tâche Observateur d'événement WMI.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`WMIEventWatcherEventOccurred`|Indique que l'événement surveillé par la tâche s'est produit.|  
|`WMIEventWatcherTimedout`|Indique que le délai de la tâche a expiré.|  
|`WMIEventWatcherWatchingForWMIEvents`|Indique que la tâche a commencé l'exécution de la requête WQL. L'entrée inclut la requête.|  
  
###  <a name="XML"></a> Tâche XML  
 Le tableau suivant décrit l'entrée de journal personnalisée de la tâche XML.  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`XMLOperation`|Fournit des informations sur l'opération que la tâche effectue.|  
  
## <a name="related-content"></a>Contenu associé  
 Entrée de blog, [Logging custom events for Integration Services tasks](https://go.microsoft.com/fwlink/?LinkId=150580) (Journalisation d’événements personnalisés pour les tâches Integration Services), sur dougbert.com.  
  
## <a name="see-also"></a>Voir aussi  
 [Journalisation Integration Services &#40;SSIS&#41;](performance/integration-services-ssis-logging.md)  
  
  
