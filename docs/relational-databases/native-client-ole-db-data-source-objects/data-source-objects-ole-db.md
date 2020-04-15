---
title: Objets de la source de données (OLE DB) | Microsoft Docs
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
ms.openlocfilehash: d8bb984c789f759eb764ad580f971ab71c9fc946
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297635"
---
# <a name="data-source-objects-ole-db"></a>Objets source de données (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client utilise le terme source de données pour l’ensemble des interfaces OLE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]DB utilisées pour établir un lien vers un magasin de données, tels que . La création d’une instance de l’objet source [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données du fournisseur est la première tâche d’un consommateur de client autochtone.  
  
 Chaque fournisseur OLE DB déclare un identificateur de classe (CLSID) pour lui-même. Le CLSID [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le fournisseur de DB OLE de client autochtone est le CLSID_SQLNCLI10 GUID C/CMD (le symbole SQLNCLI_CLSID se résoudra au progid correct dans le fichier sqlncli.h que vous faites référence). Avec le CLSID, le consommateur utilise la fonction OLE **CoCreateInstance** pour fabriquer une instance de l’objet source de données.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client est un serveur en cours. Les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cas d’objets fournisseurs de fournisseurs OLE DB de native Client sont créés à l’aide de la macro CLSCTX_INPROC_SERVER pour indiquer le contexte exécutable.  
  
 L’objet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source de données fournisseur de fournisseur OLE DB native Client expose les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interfaces de initialisation OLE DB qui permettent au consommateur de se connecter aux bases de données existantes.  
  
 Chaque connexion effectuée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par l’intermédiaire du fournisseur de DB OLE de client autochtone définit automatiquement ces options :  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 Cet exemple utilise la macro [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’identification de classe pour créer un objet de source de données fournisseur de fournisseur OLE DB de client autochtone et obtenir une référence à son interface **IDBInitialize.**  
  
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
  
 Avec la création réussie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’un exemple d’un objet de source de données fournisseur de fournisseur OLE DB de client autochtone, l’application du consommateur peut continuer en initialisant la source de données et en créant des sessions. Les sessions OLE DB présentent des interfaces qui permettent d'accéder à des données et de les manipuler.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client effectue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sa première connexion à une instance spécifiée dans le cadre d’une initialisation réussie de source de données. La connexion est maintenue tant qu’une référence est conservée dans toutes les interfaces d’initialisation de source de données, ou jusqu’à l’appel de la méthode **IDBInitialize::Uninitialize**.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Propriétés de la source de données &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [Propriétés des informations de la source de données](../../relational-databases/native-client-ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [Propriétés d'initialisation et d'autorisation](../../relational-databases/native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [Sessions](../../relational-databases/native-client-ole-db-data-source-objects/sessions.md)  
  
-   [Propriétés de la session - Fournisseur OLE DB de SQL Server Native Client](../../relational-databases/native-client-ole-db-data-source-objects/session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Objets source de données persistants](../../relational-databases/native-client-ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
