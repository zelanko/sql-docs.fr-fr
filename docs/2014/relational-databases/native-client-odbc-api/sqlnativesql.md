---
title: SQLNativeSql | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLNativeSql function
ms.assetid: 2d999fec-9e22-4514-ad5f-22a64b82f95b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0556d4e3b06c68e70513d68a5c2616bf47fc299c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046734"
---
# <a name="sqlnativesql"></a>SQLNativeSql
  Le pilote ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client répond aux demandes **SQLNativeSql** sans visiter le serveur. La fonction teste efficacement la syntaxe d'instructions SQL. La vérification de la syntaxe ne détermine pas si des identificateurs ou les résultats d'expressions dans les instructions SQL sont valides, et l'exécution du code SQL natif [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourné par **SQLNativeSql** peut échouer.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLNativeSql fonction)](https://go.microsoft.com/fwlink/?LinkID=59358)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
