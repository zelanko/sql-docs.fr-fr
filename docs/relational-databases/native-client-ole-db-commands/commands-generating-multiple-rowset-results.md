---
title: Commandes générant des résultats dans plusieurs ensembles de lignes | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- SQL Server Native Client OLE DB provider, commands
- SQL Server Native Client OLE DB provider, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
ms.assetid: 4567668d-35fd-4162-b61f-f7536862cdcb
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2cbdba7e16240b5adfd14c43a5916aaaf8cf0400
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304480"
---
# <a name="commands-generating-multiple-rowset-results"></a>Commandes générant des résultats dans plusieurs ensembles de lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autochtone peut retourner plusieurs rames des relevés. Les instructions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retournent des résultats dans plusieurs ensembles de lignes dans les conditions suivantes :  
  
-   des instructions SQL groupées sont soumises en tant que commande unique ;  
  
-   des procédures stockées implémentent un lot d'instructions SQL ;  
  
## <a name="batches"></a>Lots  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client reconnaît le caractère de point-virgule comme délimitant de lots pour les déclarations SQL :  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 Il est plus efficace d'envoyer plusieurs instructions SQL dans un lot que d'exécuter chaque instruction SQL séparément. L'envoi d'un lot réduit les allers-retours sur le réseau entre le client et le serveur.  
  
## <a name="stored-procedures"></a>Procédures stockées  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne un jeu de résultats pour chaque instruction dans une procédure stockée ; ainsi, la plupart des procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retournent plusieurs jeux de résultats.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation d'IMultipleResults pour traiter plusieurs jeux de résultats](../../relational-databases/native-client-ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
