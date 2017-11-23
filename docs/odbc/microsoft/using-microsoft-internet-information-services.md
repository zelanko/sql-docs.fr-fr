---
title: "À l’aide de Microsoft Internet Information Services | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8d3fafae5326b9631965ffdf7714b4de781cc5fa
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="using-microsoft-internet-information-services"></a>À l’aide de Microsoft Internet Information Services
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Si vous avez des difficultés à se connecter à partir d’un script d’IIS (en particulier si vous recevez une erreur ORA-12641), ajoutez la ligne suivante au fichier Sqlnet.ora :  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Cela désactive les Services réseau sécurisé pour pouvoir vous connecter à l’aide de l’authentification anonyme.
