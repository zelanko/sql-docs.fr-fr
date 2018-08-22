---
title: Prise en charge de UTF-16 dans SQL Server Native Client 11.0 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: edfcd65c62e8d8d86f55fb48f23df3831383e9d8
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394909"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Prise en charge de UTF-16 dans SQL Server Native Client 11.0
  À compter de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], si vous fournissez une mémoire tampon de longueur fixe lors de la liaison d’un paramètre de résultat ou de sortie de colonne et si le `wchar` caractère écrit dans la mémoire tampon avant le caractère de fin est un point de code de substitut étendu d’une paire de substitution et si la prochaine `wchar` caractère est un point de code de substitution faible, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client n’ajoutera pas le point de code de substitut étendu à la mémoire tampon.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](sql-server-native-client-features.md)  
  
  
