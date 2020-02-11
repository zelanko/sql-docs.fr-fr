---
title: Commandes générant des résultats à plusieurs ensembles de lignes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 04a7db670171f6f890f55a89e2da987ef2309f0e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62657679"
---
# <a name="commands-generating-multiple-rowset-results"></a>Commandes générant des résultats dans plusieurs ensembles de lignes
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client peut retourner plusieurs ensembles de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lignes à partir d’instructions. Les instructions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retournent des résultats dans plusieurs ensembles de lignes dans les conditions suivantes :  
  
-   des instructions SQL groupées sont soumises en tant que commande unique ;  
  
-   des procédures stockées implémentent un lot d'instructions SQL ;  
  
## <a name="batches"></a>Lots  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client reconnaît le point-virgule comme délimiteur de lot pour les instructions SQL :  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 Il est plus efficace d'envoyer plusieurs instructions SQL dans un lot que d'exécuter chaque instruction SQL séparément. L'envoi d'un lot réduit les allers-retours sur le réseau entre le client et le serveur.  
  
## <a name="stored-procedures"></a>Procédures stockées  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne un jeu de résultats pour chaque instruction dans une procédure stockée ; ainsi, la plupart des procédures stockées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retournent plusieurs jeux de résultats.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation d'IMultipleResults pour traiter plusieurs jeux de résultats](using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes](commands.md)  
  
  
