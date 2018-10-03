---
title: Commandes générant des résultats de plusieurs ensembles de lignes | Microsoft Docs
description: Commandes générant des résultats dans plusieurs ensembles de lignes
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- OLE DB Driver for SQL Server, commands
- OLE DB Driver for SQL Server, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: d0be8b9222d2b6ba99b913a76aa5b18c07d90f09
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47720647"
---
# <a name="commands-generating-multiple-rowset-results"></a>Commandes générant des résultats dans plusieurs ensembles de lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Le pilote OLE DB pour SQL Server peut retourner plusieurs ensembles de lignes à partir de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instructions. Les instructions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] retournent des résultats dans plusieurs ensembles de lignes dans les conditions suivantes :  
  
-   des instructions SQL groupées sont soumises en tant que commande unique ;  
  
-   des procédures stockées implémentent un lot d'instructions SQL ;  
  
## <a name="batches"></a>Lots  
 Le pilote OLE DB pour SQL Server reconnaît le point-virgule comme délimiteur de lot pour les instructions SQL :  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 Il est plus efficace d'envoyer plusieurs instructions SQL dans un lot que d'exécuter chaque instruction SQL séparément. L'envoi d'un lot réduit les allers-retours sur le réseau entre le client et le serveur.  
  
## <a name="stored-procedures"></a>Procédures stockées  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] retourne un jeu de résultats pour chaque instruction dans une procédure stockée ; ainsi, la plupart des procédures stockées [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] retournent plusieurs jeux de résultats.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation d’IMultipleResults pour traiter plusieurs jeux de résultats](../../oledb/ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Commandes](../../oledb/ole-db-commands/commands.md)  
  
  
