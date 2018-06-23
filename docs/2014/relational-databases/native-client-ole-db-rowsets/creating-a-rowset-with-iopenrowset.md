---
title: Création d’un ensemble de lignes avec IOpenRowset | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7cdce7632aa726d2992a0383d19691569ed57c0a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154374"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>Création d'un ensemble de lignes avec IOpenRowset
  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge du fournisseur OLE DB Native Client le **IOpenRowset::OpenRowset** méthode avec les restrictions suivantes :  
  
-   Une table de base ou une vue doit être spécifié dans une base de données ID (DBID) de la structure qui le *pTableID* paramètre pointe vers.  
  
-   Le DBID *eKind* membre doit indiquer DBKIND_NAME.  
  
-   Le DBID *uName* membre doit spécifier le nom d’une vue ou d’une table de base existante en tant que chaîne de caractères Unicode.  
  
-   Le *pIndexID* paramètre de **OpenRowset** doit être NULL.  
  
 Le jeu de résultats de **IOpenRowset::OpenRowset** contient un ensemble de lignes unique. Les jeux de résultats qui contiennent un ensemble de lignes unique peuvent être pris en charge par [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] curseurs. La prise en charge des curseurs permet au développeur d'utiliser les mécanismes d'accès concurrentiel de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](rowsets.md)  
  
  