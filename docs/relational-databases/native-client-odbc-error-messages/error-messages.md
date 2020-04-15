---
title: Messages d’erreur (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], types
- ODBC error handling, message types
- errors [ODBC], types
ms.assetid: 46c0c22e-d105-4d5b-bb9d-5694472e8651
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7d632d1d22cd8439a3d787e22301ec06ec4e0d93
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291738"
---
# <a name="error-messages"></a>Messages d'erreur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le texte des messages [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retournés par le conducteur de Native Client ODBC est placé dans le *paramètre MessageText* de **SQLGetDiagRec**. La source d'une erreur est indiquée par l'en-tête du message :  
  
 [Microsoft][Gestionnaire de pilotes ODBC]  
 Ces erreurs sont déclenchées par le gestionnaire de pilotes ODBC.  
  
 [Microsoft][Bibliothèque de curseurs ODBC]  
 Ces erreurs sont déclenchées par la bibliothèque de curseurs ODBC.  
  
 [Microsoft][SQL Server Native Client]  
 Ces erreurs sont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] soulevées par le conducteur de Native Client ODBC. S'il n'y a pas d'autres nœuds avec le nom d'une Net-Library ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'erreur s'est produite dans le pilote.  
  
 [Microsoft] [SQL Server Native Client] [*Net-Transportname*]  
 Ces erreurs sont [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] soulevées par la Bibliothèque Net, où *Net-Transportname* est le nom d’affichage d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réseau client (par exemple, Baptisé Pipes, Shared Memory, TCP/IP Sockets, ou VIA). Le reste du message d'erreur contient la fonction Net-Library appelée et la fonction appelée dans l'API du réseau sous-jacent par la fonction TDS. Le code *d’erreur pfNative* retourné avec ces erreurs est le code d’erreur de la pile de protocole réseau sous-jacent.  
  
 [Microsoft] [SQL Server Native Client] [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 Ces erreurs sont déclenchées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le reste du message d'erreur est le texte du message d'erreur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le code *pfNative* retourné avec ces [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erreurs est le numéro d’erreur de . Pour plus d’informations sur une liste de messages d’erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)](et leurs numéros) qui peuvent être retournés par , voir les colonnes de description et d’erreur de la table du système de **sysmessages** dans la base de données **principale** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
