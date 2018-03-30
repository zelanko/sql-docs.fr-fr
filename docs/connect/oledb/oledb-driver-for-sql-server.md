---
title: Pilote d’OLE DB pour SQL Server | Documents Microsoft
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
description: ''
ms.custom: ''
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: article
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 89e66fe2c61ae17a43e2a58071ba04374f33ea04
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2018
---
# <a name="ole-db-driver-for-sql-server"></a>Pilote d’OLE DB pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

MSOLEDBSQL ou pilote OLE DB pour SQL Server, est un terme qui a été utilisé de façon interchangeable pour faire référence à un pilote OLE DB pour SQL Server.

## <a name="different-incarnations-of-ole-db-drivers"></a>Autres Incarnations de pilotes OLE DB

Il existe trois incarnations distinctes des fournisseurs OLE DB Microsoft pour SQL Server.


### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1. Fournisseur Microsoft OLE DB pour SQL Server (SQLOLEDB)

Le [fournisseur Microsoft OLE DB pour SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) sont toujours fournis dans le cadre de [Windows Data Access Components](https://msdn.microsoft.com/en-us/library/ms692897.aspx). Il n’est pas recommandé d’utiliser de ce pilote pour tout nouveau développement.


### <a name="2-sql-server-native-client-snac"></a>2. SQL Server Native Client (SNAC)

À compter de SQL Server 2005, le [SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) inclut une interface de fournisseur OLE DB (SQLNCLI) et est le fournisseur OLE DB fournis avec SQL Server 2005 via SQL Server 2017.

Il a été [annoncées comme déconseillées dans 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) et il n’est pas recommandé d’utiliser de ce pilote pour tout nouveau développement.


### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3. Pilote Microsoft OLE DB pour SQL Server (MSOLEDBSQL)

OLE DB a été [annoncé comme undeprecated en 2017](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/). Une nouvelle version planifiée a été annoncée pour 2018.

Le nouveau fournisseur OLE DB est appelé le pilote Microsoft OLE DB pour SQL Server (MSOLEDBSQL). Le nouveau fournisseur mettra à jour avec les fonctionnalités du serveur les plus récentes à l’avenir.

Informations sur le pilote OLE DB pour les fonctionnalités de SQL Server :

-   [Pilote OLE DB SQL Server Support for LocalDB](../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  

-   [Détection des métadonnées](../oledb/features/metadata-discovery.md)  

-   [Prise en charge de UTF-16 dans le pilote OLE DB pour SQL Server](../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  

-   [Pilote OLE DB SQL Server Support for High Availability, Disaster Recovery](../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  

-   [Accès aux informations de diagnostic dans le journal des événements étendus](../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

## <a name="see-also"></a>Voir aussi  
[Installez le pilote OLE DB pour SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
 [Pilote de base de données OLE pour les fonctionnalités SQL Server](../oledb/features/oledb-driver-for-sql-server-features.md )  
