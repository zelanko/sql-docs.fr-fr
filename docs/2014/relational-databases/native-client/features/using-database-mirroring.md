---
title: À l’aide de la mise en miroir de base de données | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- SQL Server Native Client, database mirroring
- data access [SQL Server Native Client], database mirroring
- database mirroring [SQL Server], connecting clients to
- SQLNCLI, database mirroring
- SQL Server Native Client ODBC driver, database mirroring
- SQL Server Native Client OLE DB provider, database mirroring
ms.assetid: 71b15712-7972-4465-9274-e0ddc271eedc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d7db93bdbe00b6aa1bc2525c0e8ed47e45aaf15
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225328"
---
# <a name="using-database-mirroring"></a>Utilisation de la mise en miroir de bases de données
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].  
  
 La mise en miroir de bases de données, introduite dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], est une solution permettant d'accroître la disponibilité de la base de données et la redondance des données. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client fournit la prise en charge implicite pour la mise en miroir de base de données, donc le développeur n’a pas besoin d’écrire du code ou de prendre toute autre action une fois qu’il a été configuré pour la base de données.  
  
 La mise en miroir de bases de données, implémentée pour chaque base de données, conserve une copie d’une base de données de production [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur un serveur de secours. Ce serveur est un serveur de secours automatique ou semi-automatique, selon la configuration et l'état de la session de mise en miroir de bases de données. Un serveur de secours automatique prend en charge le basculement rapide sans perte de transactions validées et un serveur de secours semi-automatique prend en charge le service forcé (avec perte de données possible).  
  
 La base de données de production est appelée *base de données principale* et la copie de secours est appelée *base de données miroir*. La base de données principale et la base de données miroir doivent résider sur des instances distinctes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (instances de serveur) et, si possible, sur des ordinateurs différents.  
  
 L’instance de serveur de production, appelée *serveur principal*, communique avec l’instance de serveur de secours, appelée *serveur miroir*. Le serveur principal et le serveur miroir se comportent comme des partenaires au sein de la *session* de mise en miroir de bases de données. En cas d’échec du serveur principal, le serveur miroir peut créer sa base de données dans la base de données principale grâce à un processus appelé *basculement*. Par exemple, Partner_A et Partner_B sont deux serveurs partenaires, avec initialement la base de données principale sur Partner_A comme serveur principal et la base de données miroir sur Partner_B comme serveur miroir. Si Partner_A se retrouve hors connexion, la base de données sur Partner_B peut basculer pour devenir la base de données principale en cours. Lorsque Partner_A rejoint la session de mise en miroir, il devient le serveur miroir et sa base de données devient la base de données miroir.  
  
 D'autres configurations de mise en miroir de bases de données offrent des niveaux différents de performances et de sécurité des données, et prennent en charge diverses formes de basculement. Pour plus d’informations, consultez [Mise en miroir de bases de données &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Il est possible d'utiliser un alias lors de la spécification du nom d'une base de données miroir.  
  
> [!NOTE]  
>  Pour plus d’informations sur les tentatives de connexion initiale et les tentatives de reconnexion à une base de données mise en miroir, consultez [connecter des Clients à une Session de mise en miroir de base de données &#40;SQL Server&#41;](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md).  
  
## <a name="programming-considerations"></a>Éléments de programmation à prendre en considération  
 Lorsque le serveur de la base de données principale échoue, l'application cliente reçoit des erreurs en réponse aux appels d'API, erreurs qui signifient que la connexion à la base de données a été perdue. Lorsque cela se produit, toutes les modifications apportées à la base de données qui n'ont pas été validées sont perdues et la transaction en cours est annulée. Si cela se produit, l'application doit fermer la connexion (ou libérer l'objet source de données) et la rouvrir. La connexion est redirigée de façon transparente vers la base de données miroir, qui fait désormais office de serveur principal.  
  
 Lorsqu'une connexion est établie, le serveur principal envoie au client l'identité de son partenaire de basculement à utiliser en cas de basculement. Si une application a essayé d'établir une connexion après un échec du serveur principal, le client ne connaît pas l'identité du partenaire de basculement. Afin que les clients puissent faire face à ce scénario, une propriété d'initialisation et un mot clé de chaîne de connexion associé permettent au client de spécifier l'identité du partenaire de basculement. L'attribut client est utilisé uniquement dans ce scénario ; si le serveur principal est disponible, il n'est pas utilisé. Si le partenaire de basculement fourni par le client ne fait pas référence à un serveur agissant comme partenaire de basculement, la connexion est refusée par le serveur. Pour permettre aux applications de s'adapter aux modifications de configuration, l'identité du partenaire de basculement peut être déterminée en examinant l'attribut après que la connexion a été établie. Si possible, mettez en cache les informations sur le serveur partenaire pour mettre à jour la chaîne de connexion ou imaginer une stratégie de nouvelle tentative au cas où la première tentative d'établissement de la connexion échouerait.  
  
> [!NOTE]  
>  Vous devez spécifier explicitement la base de données utilisée par une connexion si vous souhaitez recourir à cette fonctionnalité dans un DSN, une chaîne de connexion ou une propriété (ou un attribut) de connexion. Si vous ne le faites pas, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ne tente pas de basculer sur la base de données du serveur partenaire.  
>   
>  La mise en miroir est une fonctionnalité de la base de données. Il se peut que les applications qui utilisent plusieurs bases de données ne puissent pas exploiter cette fonctionnalité.  
>   
>  De plus, les noms de serveur ne respectent pas la casse, contrairement aux noms de base de données. Par conséquent, vous devez vous assurer que vous utilisez la même casse dans les DSN et les chaînes de connexion.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Fournisseur OLE DB SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge la mise en miroir de base de données via la connexion et les attributs de chaîne de connexion. La propriété SSPROP_INIT_FAILOVERPARTNER a été ajoutée à la propriété DBPROPSET_SQLSERVERDBINIT définie et le mot clé `FailoverPartner` est un nouvel attribut de chaîne de connexion de DBPROP_INIT_PROVIDERSTRING. Pour plus d’informations, consultez [Using Connection String Keywords with SQL Server Native Client](../applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Le cache de basculement est conservé tant que le fournisseur est chargé, autrement dit jusqu'à ce que **CoUninitialize** est appelée ou tant que l’application a une référence à un objet géré par le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client comme un objet de source de données.  
  
 Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prise en charge du fournisseur OLE DB Native Client pour la mise en miroir de base de données, consultez [propriétés d’initialisation et d’autorisation](../../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>Pilote ODBC SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge la mise en miroir de base de données via la connexion et les attributs de chaîne de connexion. Plus précisément, l’attribut SQL_COPT_SS_FAILOVER_PARTNER a été ajoutée pour une utilisation avec le [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) et [SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md) fonctions ; et le `Failover_Partner` mot clé a été ajouté comme un nouvel attribut de chaîne de connexion.  
  
 Le cache de basculement est conservé tant que l'application possède au moins un handle d'environnement alloué. En revanche, il est perdu lorsque le dernier handle d'environnement est libéré.  
  
> [!NOTE]  
>  Le Gestionnaire de pilotes ODBC a été amélioré pour prendre en charge la spécification du nom du serveur de basculement.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](sql-server-native-client-features.md)   
 [Connecter des clients à une session de mise en miroir de bases de données &#40;SQL Server&#41;](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
