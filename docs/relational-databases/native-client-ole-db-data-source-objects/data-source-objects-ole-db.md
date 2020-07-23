---
title: Objets de source de données (fournisseur OLE DB Native Client) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], data source objects
- SQL Server Native Client, data source objects
- SQLNCLI, data source objects
- SQL Server Native Client OLE DB provider, data source objects
- OLE DB data source objects [SQL Server Native Client]
- data source objects [OLE DB]
- CLSID
ms.assetid: c1d4ed20-ad3b-4e33-a26b-38d7517237b7
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3f233e0ab3db0aa28a6fb7291d34ff2a27e0e777
ms.sourcegitcommit: 08f331b6a5fe72d68ef1b2eccc5d16cb80c6ee39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86976620"
---
# <a name="data-source-objects-ole-db"></a>Objets source de données (OLE DB)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client utilise le terme source de données pour l’ensemble des interfaces de OLE DB utilisées pour établir un lien vers un magasin de données, tel que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La création d’une instance de l’objet source de données du fournisseur est la première tâche d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur Native Client.  
  
 Chaque fournisseur OLE DB déclare un identificateur de classe (CLSID) pour lui-même. Le CLSID du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client est le GUID C/C++ CLSID_SQLNCLI10 (le symbole SQLNCLI_CLSID sera résolu en ProgID correct dans le fichier sqlncli. h que vous référencez). Avec le CLSID, le consommateur utilise la fonction OLE **CoCreateInstance** pour fabriquer une instance de l’objet source de données.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client est un serveur in-process. Les instances des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets Native Client OLE DB fournisseur sont créées à l’aide de la macro CLSCTX_INPROC_SERVER pour indiquer le contexte de l’exécutable.  
  
 L' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objet de source de données du fournisseur OLE DB Native Client expose les interfaces d’initialisation OLE DB qui permettent au consommateur de se connecter aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données existantes.  
  
 Chaque connexion effectuée via le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client définit automatiquement ces options :  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 Cet exemple utilise la macro d’identificateur de classe pour créer un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objet Native Client OLE DB fournisseur de source de données et obtenir une référence à son interface **IDBInitialize** .  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL, CLSCTX_INPROC_SERVER,  
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
  
 Avec la réussite de la création d’une instance d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objet Native Client OLE DB fournisseur de source de données, l’application consommateur peut continuer en initialisant la source de données et en créant des sessions. Les sessions OLE DB présentent des interfaces qui permettent d'accéder à des données et de les manipuler.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client établit sa première connexion à une instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le cadre de l’initialisation réussie de la source de données. La connexion est maintenue tant qu’une référence est conservée dans toutes les interfaces d’initialisation de source de données, ou jusqu’à l’appel de la méthode **IDBInitialize::Uninitialize**.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Propriétés de la source de données &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Propriétés des informations de la source de données](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Propriétés d'initialisation et d'autorisation](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Sessions](../../relational-databases/native-client-ole-db-data-source-objects/sessions.md)  
  
-   [Propriétés de la session - Fournisseur OLE DB de SQL Server Native Client](../../relational-databases/native-client-ole-db-data-source-objects/session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Objets source de données persistants](../../relational-databases/native-client-ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
