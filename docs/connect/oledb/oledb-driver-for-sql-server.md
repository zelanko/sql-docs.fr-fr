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
ms.openlocfilehash: fbc52a9e982da45586ce7ace5e58e8985869e552
ms.sourcegitcommit: 8f1d1363e18e0c32ff250617ab6cb2da2147bf8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2018
---
# <a name="ole-db-driver-for-sql-server"></a>Pilote d’OLE DB pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

MSOLEDBSQL ou pilote OLE DB pour SQL Server, est un terme utilisé indifféremment pour faire référence à un pilote OLE DB pour SQL Server.

## <a name="different-generations-of-ole-db-drivers"></a>Différentes générations de pilotes OLE DB

Il existe trois générations distinctes des fournisseurs OLE DB Microsoft pour SQL Server.

### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1. Fournisseur Microsoft OLE DB pour SQL Server (SQLOLEDB)
Le [fournisseur Microsoft OLE DB pour SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) sont toujours fournis dans le cadre de [Windows Data Access Components](https://msdn.microsoft.com/en-us/library/ms692897.aspx). Il n’est pas conservé plus et il n’est pas recommandé d’utiliser de ce pilote pour tout nouveau développement. 


### <a name="2-sql-server-native-client-snac"></a>2. SQL Server Native Client (SNAC)
À compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], le [SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) inclut une interface de fournisseur OLE DB (SQLNCLI) et est le fournisseur OLE DB qui accompagnent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] via [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].

Il a été [annoncées comme déconseillées dans 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) et il n’est pas recommandé d’utiliser de ce pilote pour tout nouveau développement. Pour plus d’informations sur le cycle de vie SNAC et les téléchargements disponibles, reportez-vous à [SNAC le cycle de vie expliqué](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).

### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3. Pilote Microsoft OLE DB pour SQL Server (MSOLEDBSQL)
OLE DB a été [undeprecated](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) et dans 2018 et peut être téléchargée [ici](https://go.microsoft.com/fwlink/?linkid=871294).

Le nouveau fournisseur OLE DB est appelé le pilote Microsoft OLE DB pour SQL Server (MSOLEDBSQL). Le nouveau fournisseur mettra à jour avec les fonctionnalités du serveur les plus récentes à l’avenir.

> [!NOTE]
> Pour utiliser le pilote nouveau Microsoft OLE DB pour SQL Server dans les applications existantes, vous devez planifier convertir vos chaînes de connexion SQLOLEDB ou SQLNCLI, MSOLEDBSQL.   

Informations sur le pilote OLE DB pour les fonctionnalités de SQL Server :

-   [Prise en charge de la base de données locale par OLE DB Driver pour SQL Server](../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  

-   [Détection des métadonnées](../oledb/features/metadata-discovery.md)  

-   [Prise en charge d’UTF-16 dans OLE DB Driver pour SQL Server](../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  

-   [Prise en charge de la récupération d’urgence et de la haute disponibilité par OLE DB Driver pour SQL Server](../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  

-   [Accès aux informations de diagnostic dans le journal des événements étendus](../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

## <a name="see-also"></a>Voir aussi  
[Installez le pilote OLE DB pour SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)     
[Fonctionnalités OLE DB Driver pour SQL Server](../oledb/features/oledb-driver-for-sql-server-features.md )     
