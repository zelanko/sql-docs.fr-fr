---
title: Messages renvoyés par le pilote ODBC pour Oracle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], error messages
ms.assetid: 150bde1d-adb6-4e77-90e9-4dc93499a746
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8bdaf4238bd220987364a77aaa1af837885c6e6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298859"
---
# <a name="messages-returned-by-the-odbc-driver-for-oracle"></a>Messages retournés par le pilote ODBC pour Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Si un message d’erreur Oracle est disponible, il est retourné précédé des balises [Microsoft], [ODBC Driver for Oracle] et [Oracle]. dans le cas contraire, le message est retourné sans la balise [Oracle], comme dans les exemples suivants :  
  
## <a name="oracle-error-message"></a>Message d’erreur Oracle :  
  
```  
[Microsoft][ODBC driver for Oracle][Oracle]ORA-nnnnn message-text  
```  
  
## <a name="odbc-driver-for-oracle-error-message"></a>Message d’erreur du pilote ODBC pour Oracle :  
  
```  
[Microsoft][ODBC driver for Oracle]  
```
