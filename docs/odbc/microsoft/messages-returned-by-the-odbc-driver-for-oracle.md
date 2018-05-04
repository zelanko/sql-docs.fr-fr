---
title: Messages renvoyés par le pilote ODBC pour Oracle | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- error messages [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], error messages
ms.assetid: 150bde1d-adb6-4e77-90e9-4dc93499a746
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3bcf1e257d075d2202b1096f0d497e41d7fe79f1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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
