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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7232a921027246c3ceb7d0ae1ffd5efbd3672895
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85019986"
---
# <a name="native-error-numbers"></a>Numéros des erreurs natives
  Pour les erreurs qui se produisent dans la source de données (retournée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ), le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client retourne le numéro d’erreur natif retourné par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour les erreurs détectées par le pilote, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client retourne le numéro d’erreur natif 0. Pour plus d’informations sur la liste des numéros d’erreur natifs, consultez la colonne erreur de la table système **sysmessages** dans la base de données **Master** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Pour plus d’informations sur les codes d’erreur d’État, consultez [SQLSTATE &#40;codes d’erreur ODBC&#41;](sqlstate-odbc-error-codes.md). Pour les erreurs retournées par le Net-Library, le numéro d'erreur natif provient du logiciel réseau sous-jacent.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](handling-errors-and-messages.md)  
  
  
