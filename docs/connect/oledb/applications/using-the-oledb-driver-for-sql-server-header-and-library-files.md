---
title: Utilisation des fichiers bibliothèques et d’en-tête OLE DB Driver pour SQL Server | Microsoft Docs
description: Utilisation des fichiers bibliothèques et d’en-tête OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- header files [OLE DB Driver for SQL Server]
- MSOLEDBSQL, header files
- OLE DB, header files
- library files [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, header files
- data access [OLE DB Driver for SQL Server], header files
- data access [OLE DB Driver for SQL Server], library files
- OLE DB Driver for SQL Server, library files
- MSOLEDBSQL, library files
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 93b906a0604772fe224b1e63eaf6eed9eb8af983
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989234"
---
# <a name="using-the-ole-db-driver-for-sql-server-header-and-library-files"></a>Utilisation des fichiers bibliothèques et d’en-tête OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server fichiers d’en-tête et de bibliothèque sont installés lorsque l’option OLE DB le pilote pour SQL Server SDK est sélectionnée pendant le processus d’installation. Lors du développement d'une application, il importe de copier et d'installer tous les fichiers requis pour le développement sur votre environnement de développement. Pour plus d’informations sur l’installation et la redistribution de OLE DB pilote pour SQL Server, consultez [installation du pilote OLE DB pour SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md).  
  
 Le pilote OLE DB pour SQL Server fichiers d’en-tête et de bibliothèque sont installés à l’emplacement suivant:  
  
 *% Program Files%* \Microsoft SQL Server\Client SDK\OLEDB\182\SDK  
  
 Le pilote OLE DB pour SQL Server fichier d’en-tête (msoledbsql. h) peut être utilisé pour ajouter OLE DB pilote pour SQL Server fonctionnalité d’accès aux données à vos applications personnalisées. Le fichier d’en-tête OLE DB Driver pour SQL Server contient l’ensemble des définitions, attributs, propriétés et interfaces nécessaires pour tirer parti des nouvelles fonctionnalités introduites dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 Outre le pilote OLE DB pour SQL Server fichier d’en-tête, il existe également un fichier bibliothèque msoledbsql. lib, qui est la bibliothèque d’exportation pour la fonctionnalité [OpenSqlFilestream](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) .  
  
 Le fichier d’en-tête OLE DB Driver pour SQL Server offre une compatibilité descendante avec le fichier d’en-tête sqloledb.h utilisé avec MDAC (Microsoft Data Access Components), mais ne contient pas les CLSID pour SQLOLEDB (le fournisseur OLE DB pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] inclus avec MDAC) ni les symboles pour la fonctionnalité XML (non prise en charge par OLE DB Driver pour SQL Server).    
  
 OLE DB applications qui utilisent le pilote OLE DB pour SQL Server doivent uniquement référencer msoledbsql. h. Si une application utilise MDAC (SQLOLEDB) et OLE DB Driver pour SQL Server, elle peut faire référence à sqloledb.h et msoledbsql.h, mais la référence à sqloledb.h doit être placée en premier.  
  
## <a name="using-the-ole-db-driver-for-sql-server-header-file"></a>Utilisation du pilote OLE DB pour le fichier d’en-tête SQL Server  
 Pour utiliser le pilote OLE DB pour SQL Server fichier d’en-tête, vous **devez** utiliser une instruction includeC++ dans votre code C/Programming. Les sections suivantes décrivent comment le faire dans des applications OLE DB.  
  
> [!NOTE]  
>  Le pilote OLE DB pour SQL Server fichiers de bibliothèque et d’en-tête ne peut être C++ compilé qu’à l’aide de Visual Studio 2012 ou version ultérieure.  
  
### <a name="ole-db"></a>OLE DB  
 Pour utiliser le pilote OLE DB pour SQL Server fichier d’en-tête dans une application OLE DB, utilisez les lignes de code de programmation suivantes:  
  
```    
include "msoledbsql.h";  
```  
  
> [!NOTE]  
>  Si l’application possède une instruction **include** pour SQLOLEDB. h, l’instruction **include** pour msoledbsql. h doit être postérieure à celle-ci.  
  
 Lors de la création d’une connexion à une source de données via OLE DB pilote pour SQL Server, utilisez «MSOLEDBSQL» comme chaîne de nom de fournisseur.  

  
## <a name="component-names-and-properties-by-version"></a>Noms et propriétés des composants par version  

|Propriété|OLE DB Driver pour SQL Server|MDAC|  
|--------|----------------------------|----|   
|PROGID pour OLE DB|MSOLEDBSQL|SQLOLEDB|  
|Nom du fichier d'en-tête OLE DB|msoledbsql.h|Sqloledb.h|  
|DLL du fournisseur OLE DB|msoledbsql.dll|Sqloledb.dll| 
  
  
## <a name="static-linking-and-bcp-functions"></a>Liaison statique et fonctions BCP  
 Lorsqu'une application utilise des fonctions BCP, il est important pour l'application de spécifier dans la chaîne de connexion le pilote de la même version fourni avec le fichier d'en-tête et la bibliothèque utilisés pour compiler l'application.  
  
 Pour plus d’informations, consultez exécution d' [opérations de copie en bloc](../../oledb/features/performing-bulk-copy-operations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
