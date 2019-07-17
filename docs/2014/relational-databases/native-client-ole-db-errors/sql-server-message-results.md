---
title: Résultats des messages SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff604f4c5d66a5742868e25ba05ca6b4528ddb1a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206710"
---
# <a name="sql-server-message-results"></a>Résultats des messages SQL Server
  Ce qui suit [!INCLUDE[tsql](../../includes/tsql-md.md)] ne génèrent pas d’instructions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ensembles de lignes de fournisseur OLE DB Native Client ou un nombre de lignes affectées lors exécutée :  
  
-   PRINT  
  
-   RAISERROR avec une gravité égale ou inférieure à 10  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 Ces instructions retournent un ou plusieurs messages d'information ou entraînent le renvoi par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de messages d'information au lieu de résultats sous forme d'ensemble de lignes ou de nombre. L’exécution a réussi, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne S_OK, et les messages sont disponibles pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne S_OK et possède un ou plusieurs messages d’information disponibles après l’exécution d’un grand nombre [!INCLUDE[tsql](../../includes/tsql-md.md)] instructions ou l’exécution de consommateur d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] membre du fournisseur OLE DB Native Client fonction.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consommateur du fournisseur OLE DB Native Client autorisant la spécification dynamique du texte de requête doit vérifier les interfaces d’erreur après chaque exécution de la fonction membre, quel que soit la valeur du code de retour, la présence ou l’absence d’un retourné**IRowset** ou **IMultipleResults** référence de l’interface ou un nombre de lignes affectées.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs](errors.md)  
  
  
