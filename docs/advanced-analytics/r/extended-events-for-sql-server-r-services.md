---
title: "Événements étendus pour SQL Server R Services | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e90e057-aacb-4adc-8da6-64861f4e87df
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 814dacf2dbc7f3be05ad163c8c7162acf53fe404
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="extended-events-for-sql-server-r-services"></a>Événements étendus pour SQL Server R Services
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] fournit un ensemble d'événements étendus pour résoudre les opérations liées à la [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] ou aux travaux R envoyés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour afficher une liste des événements liés à SQL Server, exécutez la requête suivante à partir de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
```  
select o.name as event_name, o.description  
  from sys.dm_xe_objects o  
  join sys.dm_xe_packages p  
    on o.package_guid = p.guid  
 where o.object_type = 'event'  
   and p.name = 'SQLSatellite';  
```  
  
 Cependant, certains événements étendus pour [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sont déclenchés uniquement à partir de processus externes, notamment [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]et BXLServer, le processus satellite qui démarre le runtime R. Pour plus d'informations sur la capture de ces événements, consultez [Collecting Events from External Processes](#bkmk_externalevents).  
  
 Pour des informations générales sur l’utilisation des événements étendus, consultez [SQL Server Extended Events Sessions](../../relational-databases/extended-events/sql-server-extended-events-sessions.md).  

  
##  <a name="bkmk_xeventtable"></a> Tableau des événements étendus  
  
|Événement|Description|Utiliser|  
|-----------|-----------------|---------|  
|connection_accept|Se produit lorsqu’une nouvelle connexion est acceptée. Cet événement permet de journaliser toutes les tentatives de connexion.||  
|failed_launching|Le lancement a échoué.|Indique une erreur.|  
|satellite_abort_connection|Enregistrement d’abandon de connexion||  
|satellite_abort_received|Se déclenche lorsqu’un message d’abandon est reçu sur une connexion satellite.||  
|satellite_abort_sent|Se déclenche lorsqu’un message d’abandon est envoyé sur une connexion satellite.||  
|satellite_authentication_completion|Se déclenche lorsque l'authentification est terminée pour une connexion sur TCP ou Namedpipe.||  
|satellite_authorization_completion|Se déclenche lorsque l'autorisation est effectuée pour une connexion sur TCP ou Namedpipe.||  
|satellite_cleanup|Se déclenche lorsque le satellite appelle la fonction de nettoyage.|Déclenché uniquement à partir de processus externes. Consultez les instructions sur la collecte d'événements à partir de processus externes.|  
|satellite_data_chunk_sent|Se déclenche lorsque la connexion satellite termine l'envoi d'un bloc de données unique.|L’événement indique le nombre de lignes envoyées, le nombre de colonnes, le nombre de paquets SNI utilisés et le temps écoulé en millisecondes pendant l’envoi du bloc. Ces informations peuvent vous aider à comprendre le temps nécessaire à la transmission des différents types de données, ainsi que le nombre de paquets utilisés.|  
|satellite_data_receive_completion|Se déclenche lorsque toutes les données requises par une requête sont reçues sur la connexion satellite.|Déclenché uniquement à partir de processus externes. Consultez les instructions sur la collecte d'événements à partir de processus externes.|  
|satellite_data_send_completion|Se déclenche lorsque toutes les données requises pour une session sont envoyées sur la connexion satellite.||  
|satellite_data_send_start|Se déclenche lorsque la transmission de données démarre (juste avant l’envoi du premier bloc de données).||  
|satellite_error|Utilisé pour le traçage des erreurs de satellite sql||  
|satellite_invalid_sized_message|La taille du message n’est pas valide||  
|satellite_message_coalesced|Utilisé pour fusionner les messages de traçage sur la couche réseau||  
|satellite_message_ring_buffer_record|Enregistrement de la mémoire tampon en anneau du message||  
|satellite_message_summary|Informations récapitulatives de la messagerie||  
|satellite_message_version_mismatch|Le champ de version du message ne correspond pas||  
|satellite_messaging|Utilisé pour le traçage des événements de messagerie (lier, dissocier etc.)||  
|satellite_partial_message|Utilisé pour le traçage des messages partiels sur la couche réseau||  
|satellite_schema_received|Se déclenche lorsque le message de schéma est reçu et lu par SQL.||  
|satellite_schema_sent|Se déclenche lorsque le message de schéma est envoyé par le satellite.|Déclenché uniquement à partir de processus externes. Consultez les instructions sur la collecte d'événements à partir de processus externes.|  
|satellite_service_start_posted|Se déclenche lorsque le message de démarrage de service est envoyé à Launchpad.|Ce message indique à Launchpad de démarrer le processus externe, et contient un ID pour la nouvelle session.|  
|satellite_unexpected_message_received|Se déclenche lors de la réception d'un message inattendu.|Indique une erreur.|  
|stack_trace|Se produit lors d'une demande de vidage mémoire pour le processus.|Indique une erreur.|  
|trace_event|Utilisé à des fins de traçage|Ces événements peuvent contenir des messages de trace de SQL Server, de Launchpad et de processus externes. Cela comprend la sortie vers stdout et stderr à partir de R.|  
|launchpad_launch_start|Se déclenche lorsque Launchpad démarre le lancement d’un satellite.|Déclenché uniquement à partir de Launchpad. Consultez les instructions sur la collecte d'événements à partir de launchpad.exe.|  
|launchpad_resume_sent|Se déclenche lorsque launchpad a lancé le satellite et envoyé un message de reprise à SQL Server.|Déclenché uniquement à partir de Launchpad. Consultez les instructions sur la collecte d'événements à partir de launchpad.exe.|  
|satellite_data_chunk_sent|Se déclenche lorsque la connexion satellite termine l'envoi d'un bloc de données unique.|Contient des informations sur le nombre de colonnes, le nombre de lignes, le nombre de paquets et le temps écoulé pour l’envoi du bloc.|  
|satellite_sessionId_mismatch|L’ID de session du message n’était pas attendu||  
  
###  <a name="bkmk_externalevents"></a> Collecting Events from External Processes  
 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] lance des services s’exécutant à l’extérieur du processus SQL Server. Pour capturer les événements liés à ces processus externes, vous devez créer un fichier de configuration de traçage des événements et placer le fichier dans le même répertoire que l'exécutable du processus.  
  
-   **[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]**   
  
     Pour capturer les événements liés à Launchpad, placez le fichier *.config* dans le répertoire Binn de l’instance SQL Server.  Dans une installation par défaut, il s’agit de `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\MSSQL\Binn`.  
  
-   **BXLServer** est le processus satellite qui prend en charge l’extensibilité SQL avec R et d’autres langages de script externes.  
  
     Pour capturer les événements liés à BXLServer, placez le fichier *.config* dans le répertoire d’installation de R.  Dans une installation par défaut, il s’agit de `C:\Program Files\Microsoft SQL Server\MSSQL_version_number.MSSQLSERVER\R_SERVICES\library\RevoScaleR\rxLibs\x64`.  
  
> [!IMPORTANT]
>   Le fichier de configuration doit porter le même que le fichier exécutable, avec le format « [nom].xevents.xml ». En d'autres termes, les fichiers doivent être nommés comme suit :  
>   
> - LaunchPad.xevents.Xml  
> - bxlserver.xevents.Xml  
  
 Le fichier de configuration lui-même a le format suivant :  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="[session name]" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="you">Xevent for launchpad or bxl server.</description>  
    <event package="SQLSatellite" name="[XEvent Name 1]" />  
    <event package="SQLSatellite" name="[XEvent Name 2]" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="[SessionName].xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
  
```  
  
 **Remarques :**  
  
-   Pour configurer la trace, modifiez l’espace réservé *nom de session*, l’espace réservé pour le nom de fichier (`[SessionName].xel`) et les noms des événements que vous voulez capturer (par exemple `[XEvent Name 1]`, `[XEvent Name 1]`).  
  
-   Un certain nombre de balises `event package` peut apparaître. Elles seront collectées tant que l’attribut « name » est correct.  
  
### <a name="example-capturing-launchpad-events"></a>Exemple : Capture des événements de Launchpad  
 L'exemple suivant montre la définition d'une trace d'événements pour le service Launchpad.  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
<event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="launchpad_launch_start" />  
    <event package="SQLSatellite" name="launchpad_resume_sent" />  
    <target package="package0" name="event_file">  
      <parameter name="filename" value="launchpad_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
  
```  
  
 **Remarques :**  
  
-   Placez le fichier *.config* dans le répertoire Binn de l’instance SQL Server.  
  
-   Ce fichier doit être nommé *Launchpad.xevents.xml*.  
  
### <a name="example-capturing-bxlserver-events"></a>Exemple : Capture des événements de BXLServer  
 L'exemple suivant montre la définition d'une trace d'événements pour le service BXLServer.  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<event_sessions>  
 <event_session name="sqlsatelliteut" maxMemory="1" dispatchLatency="1" MaxDispatchLatency="2 SECONDS">  
    <description owner="hay">Xevent for sql tdd runner.</description>  
    <event package="SQLSatellite" name="satellite_abort_received" />  
    <event package="SQLSatellite" name="satellite_authentication_completion" />  
    <event package="SQLSatellite" name="satellite_cleanup" />  
    <event package="SQLSatellite" name="satellite_data_receive_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_completion" />  
    <event package="SQLSatellite" name="satellite_data_send_start" />  
    <event package="SQLSatellite" name="satellite_schema_sent" />   
    <event package="SQLSatellite" name="satellite_unexpected_message_received" />    
    <event package="SQLSatellite" name="satellite_data_chunk_sent" />   
    <target package="package0" name="event_file">  
      <parameter name="filename" value="satellite_session.xel" />  
      <parameter name="max_file_size" value="10" />  
      <parameter name="max_rollover_files" value="10" />  
    </target>  
  </event_session>  
</event_sessions>  
  
```  
  
 **Remarques :**  
  
-   Placez le fichier *.config* dans le même répertoire que l’exécutable BXLServer.  
  
-   Ce fichier doit être nommé *bxlserver.xevents.xml*.  
  
## <a name="see-also"></a>Voir aussi
[Rapports personnalisés Management Studio pour R Services](../../advanced-analytics/r-services/monitor-r-services-using-custom-reports-in-management-studio.md)  
 [SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Gestion et surveillance des solutions R](../../advanced-analytics/r-services/managing-and-monitoring-r-solutions.md)  
  
  

