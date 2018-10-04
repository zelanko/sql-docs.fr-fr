---
title: Prise en charge de UTF-16 dans SQL Server Native Client 11.0 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 81866fc9f944bd08f78c1f7a105b4286979b7ae4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47781877"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Prise en charge de UTF-16 dans SQL Server Native Client 11.0
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Depuis [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], si vous fournissez une mémoire tampon de longueur fixe lors de la liaison d'un résultat de colonne ou d'un paramètre de sortie et que le caractère **wchar** écrit dans la mémoire tampon avant le caractère de fin est un point de code de substitut étendu d'une paire de substitution, et si le caractère **wchar** suivant est un point de code de substitut faible, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client n'ajoutera pas le point de code de substitut étendu à la mémoire tampon.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
