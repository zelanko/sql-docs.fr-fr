---
title: SQL Server Client autochtone Microsoft Docs
ms.date: 04/14/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: native-client
ms.topic: conceptual
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 30ef404501c498fca2c722e9eb88bb13997a17b5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305020"
---
# <a name="sql-server-native-client"></a>SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

SNAC, ou SQL Server Native Client, est un terme qui a été utilisé de façon interchangeable pour désigner les conducteurs ODBC et OLE DB pour SQL Server.

> [!IMPORTANT] 
> Le SQL Server Native Client (SQLNCLI) demeure déprécié et il n’est pas recommandé de l’utiliser pour de nouveaux travaux de développement. Au lieu de cela, utilisez le nouveau [Microsoft OLE DB Driver pour SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), qui sera mis à jour avec les fonctionnalités serveur les plus récentes.

> [!NOTE]
> Pour de plus amples renseignements et pour télécharger les pilotes SNAC ou ODBC, consultez le [cycle de vie du SNAC.](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/)
> Pour plus d’informations sur ODBC Driver pour SQL Server, voir [Microsoft ODBC Driver pour SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).  

 Informations sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les fonctionnalités [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]natives du client publiées avec , la dernière version disponible de SQL Server native Client:

-   [Prise en charge de SQL Server Native Client pour LocalDB](../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)  

-   [Découverte des métadonnées](../../relational-databases/native-client/features/metadata-discovery.md)  

-   [Prise en charge de UTF-16 dans SQL Server Native Client 11.0](../../relational-databases/native-client/features/utf-16-support-in-sql-server-native-client-11-0.md)  

-   [Prise en charge des fonctionnalités de récupération d'urgence, haute disponibilité par SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  

-   [Accès aux informations de diagnostic dans le journal des événements étendus](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Native Client prend en charge trois fonctionnalités qui ont été ajoutées à ODBC standard dans le Windows 7 SDK :  

-   Exécution asynchrone sur les opérations relatives à une connexion. Pour plus d’informations, voir [Asynchrone Execution](https://go.microsoft.com/fwlink/?LinkID=191493).  

-   C. Extensibilité du type de données Pour plus d’informations, voir [C Data Types in ODBC](https://go.microsoft.com/fwlink/?LinkID=191495).  

     Pour prendre en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] charge cette fonctionnalité dans Native Client, SQLGetDescField peut retourner **SQL_C_SS_TIME2** (pour les types **de temps)** ou **SQL_C_SS_TIMESTAMPOFFSET** (pour **datetimeoffset**) au lieu de **SQL_C_BINARY**, si votre application utilise ODBC 3.8. Pour plus d’informations, consultez [data Type Support for ODBC Date and Time Improvements](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md).  

-   Appeler **SQLGetData** avec un petit tampon plusieurs fois pour récupérer une grande valeur de paramètre. Pour plus d’informations, voir [Paramètres de sortie de récupération à l’aide de SQLGetData](https://go.microsoft.com/fwlink/?LinkID=191494).  

 Les rubriques suivantes décrivent des changements de comportement de Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  

-   Lors de l’appel **ICommandWithParameters::SetParameterInfo**, la valeur transmise au paramètre *pwszName* doit être un identifiant valide. Pour plus d’informations, voir [ICommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md).  

-   **SQLDescribeParam** retournera systématiquement une valeur conforme aux spécifications ODBC. Pour plus d’informations, voir [SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md).  

-   [Changement de comportement du pilote ODBC lors de la gestion des conversions de caractères](../../relational-databases/native-client/features/odbc-driver-behavior-change-when-handling-character-conversions.md)  

## <a name="see-also"></a>Voir aussi  
[Installer SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 [Fonctionnalités de SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
