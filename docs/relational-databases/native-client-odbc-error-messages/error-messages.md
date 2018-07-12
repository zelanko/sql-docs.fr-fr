---
title: Messages d’erreur | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4daf1b37e8e86654015886d67daa011b3046d731
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37422878"
---
# <a name="error-messages"></a>Messages d'erreur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le texte de messages renvoyés par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client est placé dans le *MessageText* paramètre de **SQLGetDiagRec**. La source d'une erreur est indiquée par l'en-tête du message :  
  
 [Microsoft][Gestionnaire de pilotes ODBC]  
 Ces erreurs sont déclenchées par le gestionnaire de pilotes ODBC.  
  
 [Microsoft][Bibliothèque de curseurs ODBC]  
 Ces erreurs sont déclenchées par la bibliothèque de curseurs ODBC.  
  
 [Microsoft][SQL Server Native Client]  
 Ces erreurs sont déclenchées par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client. S'il n'y a pas d'autres nœuds avec le nom d'une Net-Library ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'erreur s'est produite dans le pilote.  
  
 [Microsoft] [SQL Server Native Client] [*Net-Transportname*]  
 Ces erreurs sont déclenchées par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Net-Library, où *Net-Transportname* est le nom complet d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transport du réseau client (par exemple, canaux nommés, mémoire partagée, Sockets TCP/IP ou VIA). Le reste du message d'erreur contient la fonction Net-Library appelée et la fonction appelée dans l'API du réseau sous-jacent par la fonction TDS. Le *pfNative* code d’erreur retourné avec ces erreurs est le code d’erreur à partir de la pile de protocole réseau sous-jacent.  
  
 [Microsoft][SQL Server Native Client][[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 Ces erreurs sont déclenchées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le reste du message d'erreur est le texte du message d'erreur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le *pfNative* code retourné avec ces erreurs est le numéro d’erreur à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la liste des messages d’erreur (et leurs numéros) qui peut être retournée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez les colonnes de description et d’erreur de la **sysmessages** (table système) dans le **master** dans la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
