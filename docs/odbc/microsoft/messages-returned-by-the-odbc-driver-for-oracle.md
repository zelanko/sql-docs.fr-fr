---
title: "Messages renvoyés par le pilote ODBC pour Oracle | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error messages [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], error messages
ms.assetid: 150bde1d-adb6-4e77-90e9-4dc93499a746
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 3245479e44892d51d51027693e1231073d11c226
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="messages-returned-by-the-odbc-driver-for-oracle"></a>Messages renvoyés par le pilote ODBC pour Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Si un message d’erreur Oracle est disponible, elle est retournée précédée par [Microsoft] [pilote ODBC pour Oracle] et les balises de [Oracle]. Sinon, le message est retourné sans la balise [Oracle] comme dans les exemples suivants :  
  
## <a name="oracle-error-message"></a>Message d’erreur Oracle :  
  
```  
[Microsoft][ODBC driver for Oracle][Oracle]ORA-nnnnn message-text  
```  
  
## <a name="odbc-driver-for-oracle-error-message"></a>Pilote ODBC Oracle message d’erreur :  
  
```  
[Microsoft][ODBC driver for Oracle]  
```
