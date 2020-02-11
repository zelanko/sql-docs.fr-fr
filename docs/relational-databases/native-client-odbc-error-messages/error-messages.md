---
title: Messages d’erreur | Microsoft Docs
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 10308509004493ba68d23870a70bf878ae05b4a1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "73783455"
---
# <a name="error-messages"></a>Messages d'erreur
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le texte des messages renvoyés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le pilote ODBC Native Client est placé dans le paramètre *MessageText* de **SQLGetDiagRec**. La source d'une erreur est indiquée par l'en-tête du message :  
  
 [Microsoft][Gestionnaire de pilotes ODBC]  
 Ces erreurs sont déclenchées par le gestionnaire de pilotes ODBC.  
  
 [Microsoft][Bibliothèque de curseurs ODBC]  
 Ces erreurs sont déclenchées par la bibliothèque de curseurs ODBC.  
  
 [Microsoft][SQL Server Native Client]  
 Ces erreurs sont déclenchées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le pilote ODBC Native Client. S'il n'y a pas d'autres nœuds avec le nom d'une Net-Library ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'erreur s'est produite dans le pilote.  
  
 Librairie [SQL Server Native Client] [*Net-Transportname*]  
 Ces erreurs sont générées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la Net-Library, où *net-Transportname* est le nom d’affichage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’un transport réseau client (par exemple, canaux nommés, mémoire partagée, Sockets TCP/IP ou via). Le reste du message d'erreur contient la fonction Net-Library appelée et la fonction appelée dans l'API du réseau sous-jacent par la fonction TDS. Le code d’erreur *pfNative* retourné avec ces erreurs est le code d’erreur de la pile de protocoles réseau sous-jacente.  
  
 Librairie [SQL Server Native Client] [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]]  
 Ces erreurs sont déclenchées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le reste du message d'erreur est le texte du message d'erreur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le code *pfNative* retourné avec ces erreurs est le numéro d’erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de. Pour plus d’informations sur la liste des messages d’erreur (et leurs numéros) qui peuvent être [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]retournés par, consultez les colonnes Description et erreur de la table système **sysmessages** dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]la base de données **Master** dans.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des erreurs et des messages](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
