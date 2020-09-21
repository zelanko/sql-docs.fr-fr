---
title: Configuration requise pour OLE DB Driver pour SQL Server
description: Découvrez les composants requis logiciels nécessaires pour utiliser les fonctionnalités d’accès aux données de SQL Server telles que MARS dans OLE DB Driver pour SQL Server.
ms.custom: ''
ms.date: 03/18/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- system requirements [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], system requirements
- OLE DB Driver for SQL Server, system requirements
- MSOLEDBSQL, system requirements
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c86f62f98e81ce3c4fdd86e1e79e8f73e1422851
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861817"
---
# <a name="system-requirements-for-ole-db-driver-for-sql-server"></a>Configuration requise pour OLE DB Driver pour SQL Server

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

Pour utiliser les fonctionnalités d'accès aux données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], par exemple MARS, les logiciels suivants doivent être installés :  

* OLE DB Driver pour SQL Server sur votre client.  
* Une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur votre serveur.

> [!NOTE]  
> Assurez-vous que vous vous connectez avec les privilèges d'administrateur avant d'installer ce logiciel.  

## <a name="operating-system-requirements"></a>Système d'exploitation requis  

Pour obtenir la liste des systèmes d’exploitation qui prennent en charge OLE DB Driver pour SQL Server, consultez [Stratégies de prise en charge d’OLE DB Driver pour SQL Server](../oledb/applications/support-policies-for-oledb-driver-for-sql-server.md).  

## <a name="azure-active-directory-authentication-requirements"></a>Conditions d’authentification d’Azure Active Directory  

Lorsque vous utilisez des méthodes d’authentification Azure Active Directory avec un pilote OLE DB pour SQL Server dont la version est ***antérieure*** à la version 18.3, vérifiez que la [bibliothèque d’authentification Active Directory pour SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) est installée (dans la version 18.3, la dépendance est comprise dans le package d’installation). ADAL n’est pas requis pour les autres méthodes d’authentification ou les opérations OLE DB. Pour plus d'informations, consultez les pages suivantes : [Utilisation d’Azure Active Directory](features/using-azure-active-directory.md).

## <a name="sql-server-requirements"></a>impératifs SQL Server  

Pour utiliser OLE DB Driver pour SQL Server afin d'accéder aux données de bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez avoir installé une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  

[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] prend en charge les connexions à partir de toutes les versions de MDAC, de Windows Data Access Components, et de toutes les versions d’OLE DB Driver for SQL Server. Lorsqu'une version cliente plus ancienne se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les types de données de serveur inconnus du client sont mappés à des types compatibles avec la version du client. Pour plus d'informations, consultez [Compatibilité des types de données pour les versions du client](#data-type-compatibility-for-client-versions).  

## <a name="cross-language-requirements"></a>Configuration multilingue  

La version anglaise d’OLE DB Driver pour SQL Server est prise en charge sur toutes les versions localisées des systèmes d'exploitation pris en charge. Les versions localisées de OLE DB Driver pour SQL Server sont prises en charge sur les systèmes d'exploitation localisés qui sont dans la même langue que la version localisée d’OLE DB Driver pour SQL Server. Les versions localisées d’OLE DB Driver for SQL Server sont également prises en charge sur les versions en anglais des systèmes d’exploitation pris en charge, sous réserve que les paramètres de langue correspondants soient installés.  

Pour les mises à niveau :  

* Les versions en anglais d’OLE DB Driver pour SQL Server peuvent être mises à niveau vers n’importe quelle version localisée d’OLE DB Driver pour SQL Server.  
* Les versions localisées d’OLE DB Driver pour SQL Server peuvent être mises à niveau vers n’importe quelle version localisée d’OLE DB Driver pour SQL Server dans la même langue.  
* Les versions localisées d’OLE DB Driver pour SQL Server peuvent être mises à niveau vers la version en anglais d’OLE DB Driver pour SQL Server.  
* Les versions localisées d’OLE DB Driver pour SQL Server ne peuvent pas être mises à niveau vers des versions localisées d’OLE DB Driver pour SQL Server dans une autre langue.  

## <a name="data-type-compatibility-for-client-versions"></a>Compatibilité des types de données pour les versions du client  

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et OLE DB Driver for SQL Server mappent les nouveaux types de données aux types de données plus anciens qui sont compatibles avec les clients de bas niveau, comme indiqué dans le tableau ci-dessous.  

Les applications OLE DB et ADO peuvent utiliser le mot clé de chaîne de connexion **DataTypeCompatibility** avec OLE DB Driver pour SQL Server pour exploiter les types de données plus anciens. Quand **DataTypeCompatibility=80**, les clients OLE DB se connectent à l’aide de la version TDS (Tabular Data Stream) de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] plutôt que de la version TDS. Cela signifie que pour [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les types de données ultérieurs, la conversion de bas niveau sera effectuée par le serveur et non par OLE DB Driver for SQL Server. Cela signifie également que les fonctionnalités disponibles sur la connexion seront limitées à l'ensemble de fonctionnalités de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Plutôt que d'essayer de transmettre des requêtes non valides au serveur, une détection des tentatives d'utilisation de nouveaux types de données ou fonctionnalités intervient dès que possible sur les appels d'API et les erreurs sont retournées à l'application appelante.  

IDBInfo::GetKeywords retourne toujours une liste de mots clés qui correspondent à la version du serveur sur la connexion et n'est pas affectée par **DataTypeCompatibility**.  

|Type de données|SQL Server Native Client<br /><br />SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|OLE DB Driver pour SQL Server|Windows Data Access Components, MDAC et<br /><br /> applications OLE DB Driver pour SQL Server avec DataTypeCompatibility=80|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|CLR UDT (\<= 8 Ko)|udt|udt|udt|Varbinary|  
|varbinary(max)|varbinary|varbinary|varbinary|Image|  
|varchar(max)|varchar|varchar|varchar|Texte|  
|nvarchar(max)|NVARCHAR|NVARCHAR|NVARCHAR|Ntext|  
|Xml|Xml|Xml|Xml|Ntext|  
|CLR UDT (> 8 Ko)|varbinary|udt|udt|Image|  
|Date|varchar|Date|Date|Varchar|  
|datetime2|varchar|datetime2|datetime2|Varchar|  
|datetimeoffset|varchar|datetimeoffset|datetimeoffset|Varchar|  
|time|varchar|time|time|Varchar|  

## <a name="see-also"></a>Voir aussi  

[OLE DB Driver pour SQL Server](../oledb/oledb-driver-for-sql-server.md)  
[Installation d’OLE DB Driver pour SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
