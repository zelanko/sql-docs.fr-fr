---
title: Objets (OLE DB) Source de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b602695720e0d6567e44e4fbe8fd06b6d496a6e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084291"
---
# <a name="data-source-objects-ole-db"></a>Objets source de données (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client utilise la terme source de données pour l’ensemble des interfaces OLE DB utilisé pour établir un lien vers un magasin de données, tel que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Création d’une instance de l’objet de source de données du fournisseur est la première tâche d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur de Native Client.  
  
 Chaque fournisseur OLE DB déclare un identificateur de classe (CLSID) pour lui-même. Le CLSID de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif est le GUID CLSID_SQLNCLI10 de C/C++ (le symbole SQLNCLI_CLSID est converti correct progid dans le fichier sqlncli.h que vous référencez). Avec le CLSID, le consommateur utilise la fonction OLE **CoCreateInstance** pour fabriquer une instance de l’objet source de données.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est un serveur in-process. Instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objets de fournisseur OLE DB Native Client sont créés à l’aide de la macro CLSCTX_INPROC_SERVER de manière à indiquer le contexte exécutable.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objet de source de données de fournisseur OLE DB Native Client expose les interfaces d’initialisation OLE DB qui permettent au consommateur de se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bases de données.  
  
 Chaque connexion établie via la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif définit automatiquement les options suivantes :  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 Cet exemple utilise la macro d’identificateur de classe pour créer un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objet source de données du fournisseur OLE DB Native Client et obtenir une référence à son **IDBInitialize** interface.  
  
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
  
 Avec la création réussie d’une instance d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] objet de source de données de fournisseur de Native Client OLE DB, l’application de consommateur peut continuer en initialisant la source de données et de création de sessions. Les sessions OLE DB présentent des interfaces qui permettent d'accéder à des données et de les manipuler.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif établit sa première connexion à une instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant que partie d’une initialisation de source de données réussie. La connexion est maintenue tant qu’une référence est conservée dans toutes les interfaces d’initialisation de source de données, ou jusqu’à l’appel de la méthode **IDBInitialize::Uninitialize**.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Propriétés de la source de données &#40;OLE DB&#41;](data-source-properties-ole-db.md)  
  
-   [Propriétés des informations de la source de données](data-source-information-properties.md)  
  
-   [Propriétés d’initialisation et d’autorisation](initialization-and-authorization-properties.md)  
  
-   [Sessions](sessions.md)  
  
-   [Propriétés de session](session-properties-sql-server-native-client-ole-db-provider.md)  
  
-   [Objets source de données persistants](persisted-data-source-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
