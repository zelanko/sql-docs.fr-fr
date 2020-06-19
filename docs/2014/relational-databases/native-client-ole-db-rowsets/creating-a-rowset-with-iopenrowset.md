---
title: Création d'un ensemble de lignes avec IOpenRowset | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
author: rothja
ms.author: jroth
ms.openlocfilehash: bf74466a698d39f74b9531adaa54c79c75e50ef2
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85055989"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Création d'un ensemble de lignes avec IOpenRowset
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client prend en charge la méthode **IOpenRowset :: OpenRowset** avec les restrictions suivantes :  
  
-   Une vue ou une table de base doit être spécifiée dans une structure d’ID de base de données (DBID) vers laquelle pointe le paramètre *pTableID*.  
  
-   Le membre *eKind* DBID doit indiquer DBKIND_NAME.  
  
-   Le membre *uName* DBID doit spécifier le nom d’une vue ou d’une table de base existante sous forme de chaîne de caractères Unicode.  
  
-   Le paramètre *pIndexID* de **OpenRowset** doit être Null.  
  
 Le jeu de résultats de **IOpenRowset::OpenRowset** contient un seul ensemble de lignes. Les jeux de résultats qui contiennent un seul ensemble de lignes peuvent être pris en charge par les [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] curseurs. La prise en charge des curseurs permet au développeur d'utiliser les mécanismes d'accès concurrentiel de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](rowsets.md)  
  
  
