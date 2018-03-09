---
title: Prise en charge de UTF-16 dans SQL Server Native Client 11.0 | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7b613d38b0d7896fa1d553a46a9ccb19854956bb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Prise en charge de UTF-16 dans SQL Server Native Client 11.0
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Depuis [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], si vous fournissez une mémoire tampon de longueur fixe lors de la liaison d'un résultat de colonne ou d'un paramètre de sortie et que le caractère **wchar** écrit dans la mémoire tampon avant le caractère de fin est un point de code de substitut étendu d'une paire de substitution, et si le caractère **wchar** suivant est un point de code de substitut faible, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client n'ajoutera pas le point de code de substitut étendu à la mémoire tampon.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
