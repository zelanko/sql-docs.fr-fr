---
title: Objets de la source de données (OLE DB) | Microsoft Docs
description: Objets source de données (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], data source objects
- OLE DB Driver for SQL Server, data source objects
- MSOLEDBSQL, data source objects
- OLE DB Driver for SQL Server, data source objects
- OLE DB data source objects [OLE DB Driver for SQL Server]
- data source objects [OLE DB]
- CLSID
author: pmasl
ms.author: pelopes
ms.openlocfilehash: e0394c5fd3b72c538904c9b8cf946316e76e6650
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015925"
---
# <a name="data-source-objects-ole-db"></a>Objets source de données (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server utilise le terme « source de données » pour l’ensemble des interfaces OLE DB utilisées pour établir un lien vers une banque de données, comme [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La création d'une instance de l'objet source de données du fournisseur est la première tâche d'un consommateur OLE DB Driver pour SQL Server.  
  
 Chaque fournisseur OLE DB déclare un identificateur de classe (CLSID) pour lui-même. Le CLSID de l’OLE DB Driver for SQL Server est le GUID CLSID_MSOLEDBSQL de C/C++ (le symbole MSOLEDBSQL_CLSID est converti en ProgID correct dans le fichier msoledbsql.h que vous référencez). Avec le CLSID, le consommateur utilise la fonction OLE **CoCreateInstance** pour fabriquer une instance de l’objet source de données.  
  
 OLE DB Driver pour SQL Server est un serveur in-process. Les instances du pilote OLE DB pour SQL Server sont créées avec la macro CLSCTX_INPROC_SERVER pour indiquer le contexte exécutable.  
  
 L’objet source de données du pilote OLE DB pour SQL Server expose les interfaces d’initialisation OLE DB qui permettent au consommateur de se connecter à des bases de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] existantes.  
  
 Chaque connexion établie via OLE DB Driver pour SQL Server définit automatiquement les options suivantes :  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 Cet exemple utilise la macro d’identificateur de classe pour créer un objet source de données pour le pilote OLE DB pour SQL Server et obtenir une référence à son interface **IDBInitialize**.  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_MSOLEDBSQL, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 S’il réussit à créer une instance d’un objet source de données du pilote OLE DB pour SQL Server, l’application du consommateur peut continuer en initialisant la source de données et en créant des sessions. Les sessions OLE DB présentent des interfaces qui permettent d'accéder à des données et de les manipuler.  
  
 Le pilote OLE DB pour SQL Server établit sa première connexion à une instance spécifique de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans le cadre d’une initialisation réussie d’une source de données. La connexion est maintenue tant qu’une référence est conservée dans toutes les interfaces d’initialisation de source de données, ou jusqu’à l’appel de la méthode **IDBInitialize::Uninitialize**.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Propriétés de la source de données &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Propriétés des informations de la source de données](../../oledb/ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Propriétés d’initialisation et d’autorisation](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Sessions](../../oledb/ole-db-data-source-objects/sessions.md)  
  
-   [Propriétés de session - OLE DB Driver pour SQL Server](../../oledb/ole-db-data-source-objects/session-properties-oledb-driver-for-sql-server.md)  
  
-   [Objets source de données persistants](../../oledb/ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB Driver pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
