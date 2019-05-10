---
title: SQL Server Native Client | Microsoft Docs
ms.date: 04/14/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: native-client
ms.topic: conceptual
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b39b71f65dfe9c41c3e2ea7282729691e78a5986
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65484522"
---
# <a name="sql-server-native-client"></a>SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

SNAC ou SQL Server Native Client, est un terme qui a été utilisé de façon interchangeable pour faire référence à des pilotes ODBC et OLE DB pour SQL Server.

> [!IMPORTANT] 
> Le SQL Server Native Client (SQLNCLI) reste déconseillée et il n’est pas recommandé de l’utiliser pour les nouveaux travaux de développement. Au lieu de cela, utilisez la nouvelle [Microsoft OLE DB Driver pour SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) qui seront mises à jour avec les fonctionnalités de serveur les plus récentes.

> [!NOTE]
> Pour plus d’informations et pour télécharger le SNAC ou les pilotes ODBC, consultez le [du cycle de vie SNAC expliqué le billet de blog](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).
> Pour plus d’informations sur le pilote ODBC pour SQL Server, consultez [Microsoft ODBC Driver for SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).  

 Pour plus d’informations sur la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctionnalités de Native Client fournie avec [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], la dernière version disponible de SQL Server native Client :

-   [Prise en charge de SQL Server Native Client pour la base de données locale](../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)  

-   [Détection des métadonnées](../../relational-databases/native-client/features/metadata-discovery.md)  

-   [Prise en charge de UTF-16 dans SQL Server Native Client 11.0](../../relational-databases/native-client/features/utf-16-support-in-sql-server-native-client-11-0.md)  

-   [Prise en charge des fonctionnalités de récupération d'urgence, haute disponibilité par SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  

-   [Accès aux informations de diagnostic dans le journal des événements étendus](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

ODBC dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge les trois fonctionnalités qui ont été ajoutées à ODBC standard dans le Kit de développement logiciel de Windows 7 :  

-   Exécution asynchrone sur les opérations relatives à une connexion. Pour plus d’informations, consultez [exécution asynchrone](https://go.microsoft.com/fwlink/?LinkID=191493).  

-   C. Extensibilité du type de données Pour plus d’informations, consultez [des Types de données C dans ODBC](https://go.microsoft.com/fwlink/?LinkID=191495).  

     Pour prendre en charge cette fonctionnalité dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, SQLGetDescField peut retourner **SQL_C_SS_TIME2** (pour **temps** types) ou **SQL_C_SS_TIMESTAMPOFFSET** (pour **datetimeoffset**) au lieu de **SQL_C_BINARY**, si votre application utilise ODBC 3.8. Pour plus d’informations, consultez [prise en charge du Type de données pour les améliorations ODBC Date / heure](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md).  

-   Appel **SQLGetData** avec une petite mémoire tampon plusieurs fois afin de récupérer une valeur de paramètre élevée. Pour plus d’informations, consultez [récupération des paramètres de sortie à l’aide de SQLGetData](https://go.microsoft.com/fwlink/?LinkID=191494).  

 Les rubriques suivantes décrivent des changements de comportement de Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  

-   Lors de l’appel **ICommandWithParameters::SetParameterInfo**, la valeur passée à la *pwszName* paramètre doit être un identificateur valide. Pour plus d’informations, consultez [ICommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md).  

-   **SQLDescribeParam** constamment retourne une valeur conforme de spécification ODBC. Pour plus d’informations, consultez [SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md).  

-   [Changement de comportement du pilote ODBC lors de la gestion des conversions de caractères](../../relational-databases/native-client/features/odbc-driver-behavior-change-when-handling-character-conversions.md)  

## <a name="see-also"></a>Voir aussi  
[Installez SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 [Fonctionnalités de SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
