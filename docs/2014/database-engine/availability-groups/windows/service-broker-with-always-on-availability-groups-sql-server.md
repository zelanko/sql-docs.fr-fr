---
title: Service Broker avec groupes de disponibilité AlwaysOn (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Service Broker, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 881c20e5-1c99-44eb-b393-09fc5ea0f122
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da179219363422c4ec242d29be61f35dd1609823
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936470"
---
# <a name="service-broker-with-alwayson-availability-groups-sql-server"></a>Service Broker avec les groupes de disponibilité AlwaysOn (SQL Server)
  Cette rubrique contient des informations sur la configuration de Service Broker afin d'utiliser [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 **Dans cette rubrique :**  
  
-   [Spécifications pour qu'un service dans un groupe de disponibilité reçoive les messages distants](#ReceiveRemoteMessages)  
  
-   [Spécifications pour l'envoi de messages à un service distant dans un groupe de disponibilité](#SendRemoteMessages)  
  
##  <a name="requirements-for-a-service-in-an-availability-group-to-receive-remote-messages"></a><a name="ReceiveRemoteMessages"></a>Conditions requises pour qu’un service d’un groupe de disponibilité reçoive des messages distants  
  
1.  **Assurez-vous que le groupe de disponibilité possède un écouteur.**  
  
     Pour plus d'informations, consultez [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).  
  
2.  **Vérifiez que le point de terminaison Service Broker existe et est configuré correctement.**  
  
     Sur chaque instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui héberge un réplica de disponibilité pour le groupe de disponibilité, configurez le point de terminaison Service Broker, comme suit :  
  
    -   Définissez LISTENER_IP sur « ALL ». Ce paramètre permet les connexions à une adresse IP valide liée à l'écouteur du groupe de disponibilité.  
  
    -   Définissez le PORT de Service Broker sur le même numéro de port pour toutes les instances de serveur hôte.  
  
        > [!TIP]  
        >  Pour afficher le numéro de port du point de terminaison Service Broker sur une instance de serveur donnée, interrogez la colonne **port** de l’affichage catalogue [sys.tcp_endpoints](/sql/relational-databases/system-catalog-views/sys-tcp-endpoints-transact-sql) , où **type_desc** = 'SERVICE_BROKER'.  
  
     L'exemple suivant crée un point de terminaison Service Broker authentifié par Windows qui utilise le port par défaut de Service Broker (4022) et écoute toutes les adresses IP valides.  
  
    ```  
    CREATE ENDPOINT [SSBEndpoint]  
        STATE = STARTED  
        AS TCP  (LISTENER_PORT = 4022, LISTENER_IP = ALL )  
        FOR SERVICE_BROKER (AUTHENTICATION = WINDOWS)  
    ```  
  
     Pour plus d’informations, consultez [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).  
  
3.  **Accordez l'autorisation CONNECT sur le point de terminaison.**  
  
     Accordez l'autorisation CONNECT sur le point de terminaison Service Broker sur PUBLIC ou sur une connexion.  
  
     L'exemple suivant accorde la connexion sur un point de terminaison Service Broker nommé `broker_endpoint` sur PUBLIC.  
  
    ```  
    GRANT CONNECT ON ENDPOINT::[broker_endpoint] TO [PUBLIC]  
    ```  
  
     Pour plus d’informations, consultez [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql).  
  
4.  **Vérifiez que msdb contient un itinéraire AutoCreatedLocal ou un itinéraire vers le service spécifique.**  
  
    > [!NOTE]  
    >  Chaque base de données utilisateur qui englobe **msdb**contient par défaut l'itinéraire **AutoCreatedLocal**. Cet itinéraire, qui correspond à tous les noms de services et instances de broker, spécifie que le message doit être remis dans l'instance active. **AutoCreatedLocal** a une priorité plus faible que les itinéraires qui spécifient explicitement un service spécifique qui communique avec une instance distante.  
  
     Pour plus d’informations sur la création des itinéraires, consultez [Exemples de routage Service Broker](https://msdn.microsoft.com/library/ms166090\(SQL.105\).aspx) (dans la version [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] de la documentation en ligne) et [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql).  
  
##  <a name="requirements-for-sending-messages-to-a-remote-service-in-an-availability-group"></a><a name="SendRemoteMessages"></a>Conditions requises pour l’envoi de messages à un service distant dans un groupe de disponibilité  
  
1.  **Créez un itinéraire vers le service cible.**  
  
     Configurez l'itinéraire comme suit :  
  
    -   Définissez ADDRESS sur l'adresse IP de l'écouteur du groupe de disponibilité qui héberge la base de données de service.  
  
    -   Définissez PORT sur le port que vous avez spécifié dans le point de terminaison Service Broker de chacune des instances distantes de SQL Server.  
  
     L'exemple suivant crée un itinéraire nommé `RouteToTargetService` pour le service `ISBNLookupRequestService` . L'itinéraire cible l'écouteur du groupe de disponibilité, `MyAgListener`, qui utilise le port 4022.  
  
    ```  
    CREATE ROUTE [RouteToTargetService] WITH   
    SERVICE_NAME = 'ISBNLookupRequestService',   
    ADDRESS = 'TCP://MyAgListener:4022';  
  
    ```  
  
     Pour plus d’informations, consultez [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql).  
  
2.  **Vérifiez que msdb contient un itinéraire AutoCreatedLocal ou un itinéraire vers le service spécifique.** (Pour plus d’informations, consultez [Spécifications pour qu’un service dans un groupe de disponibilité reçoive les messages distants](#ReceiveRemoteMessages), plus haut dans cette rubrique.)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
-   [CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql)  
  
-   [GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql)  
  
-   [Créez ou configurez un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).  
  
-   [Création et configuration des groupes de disponibilité &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [Configurer des comptes de connexion pour la mise en miroir de bases de données ou groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../../database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [SQL Server Service Broker](../../configure-windows/sql-server-service-broker.md)  
  
  
