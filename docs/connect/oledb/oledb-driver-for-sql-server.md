---
title: Microsoft OLE DB Driver for SQL Server | Microsoft Docs
description: Microsoft OLE DB Driver pour SQL Server fournit la connectivité à SQL Server et Azure SQL Database via les API OLE DB standard.
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server
- MSOLEDBSQL
- native data access [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 52877846ab573b146c148dab681cd45aec0a083c
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488509"
---
# <a name="microsoft-ole-db-driver-for-sql-server"></a>Microsoft OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

OLE DB Driver for SQL Server est une interface de programmation d’applications (API, Application Programming Interface) autonome d’accès aux données, utilisée pour OLE DB. Elle a été introduite avec [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. OLE DB Driver for SQL Server fournit le pilote OLE DB SQL dans une bibliothèque de liens dynamiques (DLL). Il fournit également de nouvelles fonctionnalités au-delà de celles fournies par Windows Data Access Components (Windows DAC, anciennement MDAC (Microsoft Data Access Components), ou MDAC). OLE DB Driver for SQL Server permet de créer de nouvelles applications et d’améliorer les applications existantes qui doivent tirer profit des fonctionnalités de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], telles que MARS (Multiple Active Result Sets), les types définis par l’utilisateur (UDT), les notifications de requêtes, l’isolation de capture instantanée et la prise en charge des types de données XML.  
  
> [!NOTE]  
> Pour obtenir la liste des différences entre OLE DB Driver for SQL Server et Windows DAC, ainsi que des informations sur les problèmes à prendre en compte avant la mise à jour d’une application Windows DAC avec OLE DB Driver for SQL Server, consultez [Mise à jour d’une application vers OLE DB Driver pour SQL Server à partir de MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  

> [!IMPORTANT]
> Le [Fournisseur Microsoft OLE DB pour SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) et le fournisseur [SQL Server Native Client](../../relational-databases/native-client/sql-server-native-client.md) (SQLNCLI) précédents restent dépréciés, et nous vous déconseillons d’utiliser l’un ou l’autre pour les nouveaux travaux de développement.
  
 Le pilote OLE DB pour SQL Server peut être utilisé conjointement à OLE DB Core Services, qui est fourni avec Windows DAC, mais cela n’est pas obligatoire. Ce choix dépend des spécifications de l’application individuelle (par exemple, si le regroupement de connexions est nécessaire).  
  
 Les applications ADO (ActiveX Data Object) peuvent utiliser OLE DB Driver for SQL Server, mais nous vous recommandons d’utiliser ADO conjointement avec le mot clé de chaîne de connexion **DataTypeCompatibility** (ou sa propriété **DataSource** correspondante). Lors de l’utilisation d’OLE DB Driver for SQL Server, les applications ADO peuvent exploiter ces nouvelles fonctionnalités introduites dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] disponibles via OLE DB Driver for SQL Server par le biais de mots clés de chaîne de connexion, de propriétés OLE DB ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Pour plus d’informations sur l’utilisation de ces fonctionnalités avec ADO, consultez [Utilisation d’ADO avec OLE DB Driver pour SQL Server](../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md).  
  
 Le pilote OLE DB pour SQL Server a été conçu en vue de fournir à SQL Server une méthode simplifiée d’accès aux données natives avec OLE DB. Il permet d’améliorer et de faire évoluer les nouvelles fonctionnalités d’accès aux données sans modifier pour autant les composants Windows DAC actuels, qui font désormais partie de la plateforme Microsoft Windows.  
  
 Bien que le pilote OLE DB pour SQL Server utilise des composants de Windows DAC, il ne dépend pas de manière explicite d’une version particulière de Windows DAC. Vous pouvez utiliser OLE DB Driver for SQL Server avec la version de Windows DAC installée avec tout système d’exploitation pris en charge par OLE DB Driver for SQL Server.  

 ## <a name="different-generations-of-ole-db-drivers"></a>Différentes générations de pilotes OLE DB

Il existe trois générations distinctes de fournisseurs OLE DB Microsoft pour SQL Server.

### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1. Fournisseur Microsoft OLE DB pour SQL Server (SQLOLEDB)
Le [Fournisseur Microsoft OLE DB pour SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) est toujours fourni dans le cadre de [Windows Data Access Components](https://msdn.microsoft.com/library/ms692897.aspx). Il n’est plus tenu à jour et nous vous déconseillons d’utiliser ce pilote pour un nouveau développement.

### <a name="2-sql-server-native-client-snac"></a>2. SQL Server Native Client (SNAC)
À compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) inclut une interface de fournisseur OLE DB (SQLNCLI) et est le fournisseur OLE DB fourni avec les versions comprises entre [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].

Sa [dépréciation a été annoncée en 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/), et nous vous déconseillons d’utiliser ce pilote pour un nouveau développement. Pour plus d’informations sur le cycle de vie SNAC et les téléchargements disponibles, consultez [SNAC lifecycle explained](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/) (Explication concernant le cycle de vie SNAC).

### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3. Microsoft OLE DB Driver for SQL Server (MSOLEDBSQL)
L’[annulation de la dépréciation](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) et la publication d’OLE DB ont eu lieu en 2018.

Le nouveau fournisseur OLE DB se nomme Microsoft OLE DB Driver for SQL Server (MSOLEDBSQL). Le nouveau fournisseur sera mis à jour avec les fonctionnalités de serveur les plus récentes à l’avenir.

> [!NOTE]
> Pour utiliser le nouveau Microsoft OLE DB Driver for SQL Server dans les applications existantes, vous devez planifier la conversion de vos chaînes de connexion SQLOLEDB ou SQLNCLI vers MSOLEDBSQL.
  
## <a name="in-this-section"></a>Contenu de cette section  
[Quand utiliser OLE DB Driver pour SQL Server](../oledb/when-to-use-oledb-driver-for-sql-server.md)  
 Traite de la façon dont le pilote OLE DB pour SQL Server s’intègre aux technologies d’accès aux données de Microsoft, le compare à Windows DAC et ADO.NET et fournit des pointeurs pour vous aider à déterminer la technologie d’accès aux données à utiliser.  
  
 [Fonctionnalités OLE DB Driver pour SQL Server](../oledb/features/oledb-driver-for-sql-server-features.md )  
 Décrit les fonctionnalités prises en charge par OLE DB Driver for SQL Server.  
  
 [Création d’applications avec OLE DB Driver pour SQL Server](../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
 Fournit une présentation du développement à l’aide du pilote OLE DB pour SQL Server, y compris la façon dont il diffère de Windows DAC, les composants qu’il utilise et la manière dont ADO peut être utilisé conjointement à lui.  
  
 Cette section décrit également l’installation et le déploiement d’OLE DB Driver for SQL Server, notamment comment redistribuer la bibliothèque OLE DB Driver for SQL Server.  
  
 [Configuration requise pour OLE DB Driver pour SQL Server](../oledb/system-requirements-for-oledb-driver-for-sql-server.md)  
 Traite des ressources système nécessaires pour utiliser OLE DB Driver for SQL Server.  
  
 [OLE DB Driver pour la programmation de SQL Server](../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
 Fournit des informations sur l’utilisation d’OLE DB Driver for SQL Server.  
  
 [Recherche d’informations supplémentaires sur OLE DB Driver pour SQL Server](../oledb/finding-more-oledb-driver-for-sql-server-information.md)  
 Fournit des ressources supplémentaires au sujet d’OLE DB Driver for SQL Server, notamment des liens vers des ressources externes et permettant d’obtenir une assistance.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour d’une application à partir de SQL Server 2005 Native Client](../oledb/applications/updating-an-application-from-sql-server-2005-native-client.md)    
 [Rubriques de procédures OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
