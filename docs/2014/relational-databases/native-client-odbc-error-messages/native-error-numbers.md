---
title: Numéros des erreurs natives | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC error handling, native error numbers
- SQL Server Native Client ODBC driver, errors
- native error numbers [SQL Server Native Client]
- messages [ODBC], native error numbers
- errors [ODBC], native error numbers
ms.assetid: 77cbc826-f47f-4803-8e7a-223d6df069b1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e7cd24a3eb1ccdeea1b6e6cbb97e2d0f222193f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63223498"
---
# <a name="native-error-numbers"></a>Numéros des erreurs natives
  Pour les erreurs qui se produisent dans la source de données (retournées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]), la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client retourne le numéro d’erreur natif qui lui retourné par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour les erreurs détectées par le pilote, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client retourne un numéro d’erreur native de 0. Pour plus d’informations sur une liste de numéros d’erreur natif, consultez la colonne d’erreur de la **sysmessages** (table système) dans le **master** dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour plus d’informations sur les codes d’erreur état, consultez [SQLSTATE &#40;Codes d’erreur ODBC&#41;](sqlstate-odbc-error-codes.md). Pour les erreurs retournées par le Net-Library, le numéro d'erreur natif provient du logiciel réseau sous-jacent.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](handling-errors-and-messages.md)  
  
  
