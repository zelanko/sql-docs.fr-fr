---
title: Prise en charge d’UTF-16 dans SQL Server Native Client 11,0 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 415cb2fe8a3295770cfc8bd2d5c6e56750adb6d9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63205113"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Prise en charge de UTF-16 dans SQL Server Native Client 11.0
  À compter [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]de, si vous fournissez une mémoire tampon de longueur fixe lors de la liaison d’un paramètre de `wchar` sortie ou de résultat de colonne et si le caractère écrit dans la mémoire tampon avant le caractère de fin est un point de code `wchar` de substitution étendu d’une paire de substitution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , et si le caractère suivant est un point de code de substitution faible, Native Client n’ajoute pas le point de code de  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](sql-server-native-client-features.md)  
  
  
