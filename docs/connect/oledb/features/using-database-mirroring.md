---
title: Utilisation de la mise en miroir de bases de données | Microsoft Docs
description: OLE DB Driver pour SQL Server prend en charge la mise en miroir de bases de données. Les développeurs n’ont pas besoin d’effectuer d’autres actions une fois la mise en miroir configurée pour la base de données.
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- OLE DB Driver for SQL Server, database mirroring
- data access [OLE DB Driver for SQL Server], database mirroring
- database mirroring [SQL Server], connecting clients to
- MSOLEDBSQL, database mirroring
- OLE DB Driver for SQL Server, database mirroring
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b396adab98a22b0f2c38a7f3e6aa4b169f72b395
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861634"
---
# <a name="using-database-mirroring"></a>Utilisation de la mise en miroir de bases de données
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)] Utilisez [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] à la place.  
  
 La mise en miroir de bases de données, introduite dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], est une solution permettant d'accroître la disponibilité de la base de données et la redondance des données. OLE DB Driver pour SQL Server assurant une prise en charge implicite pour la mise en miroir de bases de données, le développeur n’a pas besoin d’écrire de code ni de prendre une autre mesure une fois la mise en miroir configurée pour la base de données.  
  
 La mise en miroir de bases de données, implémentée pour chaque base de données, conserve une copie d’une base de données de production [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur un serveur de secours. Ce serveur est un serveur de secours automatique ou semi-automatique, selon la configuration et l'état de la session de mise en miroir de bases de données. Un serveur de secours automatique prend en charge le basculement rapide sans perte de transactions validées et un serveur de secours semi-automatique prend en charge le service forcé (avec perte de données possible).  
  
 La base de données de production est appelée *base de données principale* et la copie de secours est appelée *base de données miroir*. La base de données principale et la base de données miroir doivent résider sur des instances distinctes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (instances de serveur) et, si possible, sur des ordinateurs différents.  
  
 L’instance de serveur de production, appelée *serveur principal*, communique avec l’instance de serveur de secours, appelée *serveur miroir*. Le serveur principal et le serveur miroir se comportent comme des partenaires au sein de la *session* de mise en miroir de bases de données. En cas d’échec du serveur principal, le serveur miroir peut créer sa base de données dans la base de données principale grâce à un processus appelé *basculement*. Par exemple, Partner_A et Partner_B sont deux serveurs partenaires, avec initialement la base de données principale sur Partner_A comme serveur principal et la base de données miroir sur Partner_B comme serveur miroir. Si Partner_A se retrouve hors connexion, la base de données sur Partner_B peut basculer pour devenir la base de données principale en cours. Lorsque Partner_A rejoint la session de mise en miroir, il devient le serveur miroir et sa base de données devient la base de données miroir.  
  
 D'autres configurations de mise en miroir de bases de données offrent des niveaux différents de performances et de sécurité des données, et prennent en charge diverses formes de basculement. Pour plus d’informations, consultez [Mise en miroir de bases de données &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Il est possible d'utiliser un alias lors de la spécification du nom d'une base de données miroir.  
  
> [!NOTE]  
>  Pour plus d'informations sur les tentatives de connexion initiale et de reconnexion à une base de données mise en miroir, consultez [Connecter des clients à une session de mise en miroir de bases de données &#40;SQL Server&#41;](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md).  
  
## <a name="programming-considerations"></a>Éléments de programmation à prendre en considération  
 Lorsque le serveur de la base de données principale échoue, l'application cliente reçoit des erreurs en réponse aux appels d'API, erreurs qui signifient que la connexion à la base de données a été perdue. Lorsque cela se produit, toutes les modifications apportées à la base de données qui n'ont pas été validées sont perdues et la transaction en cours est annulée. Si cela se produit, l'application doit fermer la connexion (ou libérer l'objet source de données) et la rouvrir. La connexion est redirigée de façon transparente vers la base de données miroir, qui fait désormais office de serveur principal.  
  
 Lorsqu'une connexion est établie, le serveur principal envoie au client l'identité de son partenaire de basculement à utiliser en cas de basculement. Si une application a essayé d'établir une connexion après un échec du serveur principal, le client ne connaît pas l'identité du partenaire de basculement. Afin que les clients puissent faire face à ce scénario, une propriété d'initialisation et un mot clé de chaîne de connexion associé permettent au client de spécifier l'identité du partenaire de basculement. L'attribut client est utilisé uniquement dans ce scénario ; si le serveur principal est disponible, il n'est pas utilisé. Si le partenaire de basculement fourni par le client ne fait pas référence à un serveur agissant comme partenaire de basculement, la connexion est refusée par le serveur. Pour permettre aux applications de s'adapter aux modifications de configuration, l'identité du partenaire de basculement peut être déterminée en examinant l'attribut après que la connexion a été établie. Si possible, mettez en cache les informations sur le serveur partenaire pour mettre à jour la chaîne de connexion ou imaginer une stratégie de nouvelle tentative au cas où la première tentative d'établissement de la connexion échouerait.  
  
> [!NOTE]  
>  Vous devez spécifier explicitement la base de données utilisée par une connexion si vous souhaitez recourir à cette fonctionnalité dans un DSN, une chaîne de connexion ou une propriété (ou un attribut) de connexion. Si vous ne le faites pas, OLE DB Driver pour SQL Server ne tente pas de basculer sur la base de données du serveur partenaire.  
>   
>  La mise en miroir est une fonctionnalité de la base de données. Il se peut que les applications qui utilisent plusieurs bases de données ne puissent pas exploiter cette fonctionnalité.  
>   
>  De plus, les noms de serveur ne respectent pas la casse, contrairement aux noms de base de données. Par conséquent, vous devez vous assurer que vous utilisez la même casse dans les DSN et les chaînes de connexion.  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver pour SQL Server  
 OLE DB Driver pour SQL Server prend en charge la mise en miroir de bases de données via les attributs de connexion et de chaîne de connexion. La propriété SSPROP_INIT_FAILOVERPARTNER a été ajoutée au jeu de propriétés DBPROPSET_SQLSERVERDBINIT et le mot clé **FailoverPartner** est un nouvel attribut de chaîne de connexion de DBPROP_INIT_PROVIDERSTRING. Pour plus d’informations, voir [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 Le cache de basculement est conservé tant que le fournisseur est chargé, autrement dit jusqu’à ce que **CoUninitialize** soit appelé, ou tant que l’application détient une référence à un objet géré par OLE DB Driver pour SQL Server (objet source de données, par exemple).  
  
 Pour plus d’informations sur la prise en charge d’OLE DB Driver pour SQL Server en vue de la mise en miroir de bases de données, consultez [Propriétés d'initialisation et d'autorisation](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md).  
 
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 [Connecter des clients à une session de mise en miroir de bases de données &#40;SQL Server&#41;](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
