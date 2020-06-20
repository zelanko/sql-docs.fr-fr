---
title: Prise en charge d’UTF-16 dans SQL Server Native Client 11,0 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: rothja
ms.author: jroth
ms.openlocfilehash: af8581071400db888fb508b88f8e8ae93bc71f70
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039003"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>Prise en charge de UTF-16 dans SQL Server Native Client 11.0
  À compter de [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] , si vous fournissez une mémoire tampon de longueur fixe lors de la liaison d’un paramètre de sortie ou de résultat de colonne et si le `wchar` caractère écrit dans la mémoire tampon avant le caractère de fin est un point de code de substitution étendu d’une paire de substitution, et si le `wchar` caractère suivant est un point de code de substitution faible, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client n’ajoute pas le point de code de  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](sql-server-native-client-features.md)  
  
  
