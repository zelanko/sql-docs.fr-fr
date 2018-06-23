---
title: Prise en charge de UTF-16 dans SQL Server Native Client 11.0 | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 66198f42676944967a2d655f14a27470922fd318
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143702"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Prise en charge de UTF-16 dans SQL Server Native Client 11.0
  À compter de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], si vous fournissez une mémoire tampon de longueur fixe lors de la liaison d’un paramètre de résultat ou de la sortie de colonne et si les `wchar` caractères écrits dans la mémoire tampon avant le caractère de fin est un point de code de substitut étendu d’une paire de substitution et si la prochaine `wchar` caractère est un point de code de substitution faible [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client n’ajoutera pas le point de code de substitut pour la mémoire tampon.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](sql-server-native-client-features.md)  
  
  