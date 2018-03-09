---
title: "À l’aide de Microsoft Internet Information Services | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
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
ms.openlocfilehash: d96eca0961a472d252eb909387bb281e78952228
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="using-microsoft-internet-information-services"></a>À l’aide de Microsoft Internet Information Services
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Si vous avez des difficultés à se connecter à partir d’un script d’IIS (en particulier si vous recevez une erreur ORA-12641), ajoutez la ligne suivante au fichier Sqlnet.ora :  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Cela désactive les Services réseau sécurisé pour pouvoir vous connecter à l’aide de l’authentification anonyme.
