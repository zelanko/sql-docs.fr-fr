---
title: Microsoft OLE DB Driver for SQL Server | Microsoft Docs
description: Microsoft OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
manager: craigg
ms.openlocfilehash: 3e1764fdd2a96fcf1d0da218ef86b2e4cb62fd8c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43025910"
---
# <a name="microsoft-ole-db-driver-for-sql-server"></a>Microsoft OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB Driver pour SQL Server est une données autonome accès application interface de programmation (API), utilisée pour OLE DB, qui a été introduite dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. OLE DB Driver pour SQL Server offre le pilote OLE DB SQL dans une bibliothèque de liens dynamiques (DLL). Il fournit également de nouvelles fonctionnalités au-delà de celles fournies par Windows Data Access Components (Windows DAC, anciennement MDAC (Microsoft Data Access Components), ou MDAC). Le pilote OLE DB pour SQL Server permet de créer de nouvelles applications et d’améliorer les applications existantes qui doivent tirer profit des fonctionnalités de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], telles que MARS (Multiple Active Result Sets), les types définis par l’utilisateur (UDT), les notifications de requêtes et la prise en charge des types de données XML.  
  
> [!NOTE]  
>  Pour obtenir la liste des différences entre le pilote OLE DB pour SQL Server et Windows DAC, ainsi que des informations sur les problèmes à prendre en compte avant la mise à jour d’une application Windows DAC à OLE DB Driver pour SQL Server, consultez [la mise à jour d’une Application vers OLE DB Driver pour SQL Serveur à partir de MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
 Le pilote OLE DB pour SQL Server peut être utilisé conjointement à OLE DB Core Services, qui est fourni avec Windows DAC, mais cela n’est pas obligatoire. Ce choix dépend des spécifications de l’application individuelle (par exemple, si le regroupement de connexions est nécessaire).  
  
 Les applications ActiveX Data Object (ADO) peuvent utiliser le pilote OLE DB pour SQL Server, mais il est recommandé d’utiliser ADO conjointement avec le **DataTypeCompatibility** mot clé de chaîne de connexion (ou son correspondant  **Source de données** propriété). Lorsque vous utilisez le pilote OLE DB pour SQL Server, les applications ADO peuvent exploiter ces nouvelles fonctionnalités introduites dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] qui sont disponibles via le pilote OLE DB pour SQL Server par le biais de mots clés de chaîne de connexion ou de propriétés OLE DB ou [!INCLUDE[tsql](../../includes/tsql-md.md)]. Pour plus d’informations sur l’utilisation de ces fonctionnalités avec ADO, consultez [à l’aide d’ADO avec OLE DB Driver pour SQL Server](../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md).  
  
 Le pilote OLE DB pour SQL Server a été conçu en vue de fournir à SQL Server une méthode simplifiée d’accès aux données natives avec OLE DB. Il fournit un moyen d’innover et de faire évoluer les nouvelles fonctionnalités d’accès aux données sans modifier les composants de Windows DAC actuels, font maintenant partie de la plateforme Microsoft Windows.  
  
 Bien que le pilote OLE DB pour SQL Server utilise des composants de Windows DAC, il ne dépend pas de manière explicite d’une version particulière de Windows DAC. Vous pouvez utiliser le pilote OLE DB pour SQL Server avec la version de Windows DAC qui est installé avec n’importe quel système d’exploitation pris en charge par OLE DB Driver pour SQL Server.  

 ## <a name="different-generations-of-ole-db-drivers"></a>Différentes générations de pilotes OLE DB

Il existe trois générations distinctes des fournisseurs OLE DB Microsoft pour SQL Server.

### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1. Fournisseur Microsoft OLE DB pour SQL Server (SQLOLEDB)
Le [fournisseur Microsoft OLE DB pour SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB) est toujours fourni dans le cadre de [Windows Data Access Components](https://msdn.microsoft.com/library/ms692897.aspx). Il n’est pas conservé plus et il n’est pas recommandé d’utiliser ce pilote pour un nouveau développement.

### <a name="2-sql-server-native-client-snac"></a>2. SQL Server Native Client (SNAC)
À compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], le [SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) inclut une interface de fournisseur OLE DB (SQLNCLI) et est le fournisseur OLE DB qui accompagnent [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] via [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].

Il a été [annoncées comme déconseillées dans 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) et il n’est pas recommandé d’utiliser ce pilote pour un nouveau développement. Pour plus d’informations sur le cycle de vie SNAC et les téléchargements disponibles, reportez-vous à [SNAC le cycle de vie expliqué](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).

### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3. Microsoft OLE DB Driver for SQL Server (MSOLEDBSQL)
OLE DB a été [annuler la dépréciation](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) et publiée en 2018.

Le nouveau fournisseur OLE DB est appelé le pilote Microsoft OLE DB pour SQL Server (MSOLEDBSQL). Le nouveau fournisseur mettra à jour avec les fonctionnalités du serveur les plus récentes à l’avenir.

> [!NOTE]
> Pour utiliser le nouveau Microsoft OLE DB Driver pour SQL Server dans les applications existantes, vous devez planifier convertir vos chaînes de connexion SQLOLEDB ou SQLNCLI, MSOLEDBSQL.
  
## <a name="in-this-section"></a>Dans cette section  
[Quand utiliser OLE DB Driver pour SQL Server](../oledb/when-to-use-oledb-driver-for-sql-server.md)  
 Traite de la façon dont le pilote OLE DB pour SQL Server s’intègre aux technologies d’accès aux données de Microsoft, le compare à Windows DAC et ADO.NET et fournit des pointeurs pour vous aider à déterminer la technologie d’accès aux données à utiliser.  
  
 [Fonctionnalités OLE DB Driver pour SQL Server](../oledb/features/oledb-driver-for-sql-server-features.md )  
 Décrit les fonctionnalités prises en charge par OLE DB Driver pour SQL Server.  
  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
 Fournit une présentation du développement à l’aide du pilote OLE DB pour SQL Server, y compris la façon dont il diffère de Windows DAC, les composants qu’il utilise et la manière dont ADO peut être utilisé conjointement à lui.  
  
 Cette section décrit également le pilote OLE DB pour l’installation de SQL Server et de déploiement, y compris comment redistribuer le pilote OLE DB pour la bibliothèque de SQL Server.  
  
 [Configuration requise pour OLE DB Driver pour SQL Server](../oledb/system-requirements-for-oledb-driver-for-sql-server.md)  
 Discute des ressources système nécessaires à l’utilisation d’OLE DB Driver pour SQL Server.  
  
 [Programmation OLE DB Driver pour SQL Server](../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
 Fournit des informations sur l’utilisation d’OLE DB Driver pour SQL Server.  
  
 [Recherche d’informations supplémentaires sur OLE DB Driver pour SQL Server](../oledb/finding-more-oledb-driver-for-sql-server-information.md)  
 Fournit des ressources supplémentaires sur OLE DB Driver pour SQL Server, notamment des liens vers des ressources externes et permettant d’obtenir une assistance.  
  
  
## <a name="see-also"></a> Voir aussi  
 [Mise à jour d’une application à partir de SQL Server 2005 Native Client](../oledb/applications/updating-an-application-from-sql-server-2005-native-client.md)    
 [Rubriques de procédures liées à OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  
