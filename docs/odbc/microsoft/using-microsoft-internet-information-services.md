---
title: À l’aide de Microsoft Internet Information Services | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], IIS
- internet information services [ODBC]
- IIS [ODBC]
ms.assetid: 3328f2f1-b34a-472f-82cf-ad49768ff061
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9e531149af21facd80e9e6ddab19a76c3bdc0fa6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68088142"
---
# <a name="using-microsoft-internet-information-services"></a>Utilisation de Microsoft Internet Information Services
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Si vous avez des difficultés à se connecter à partir d’un script d’IIS (en particulier si vous recevez une erreur ORA-12641), ajoutez la ligne suivante au fichier Sqlnet.ora :  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Cela désactive les Services de réseau sécurisé pour pouvoir vous connecter à l’aide de l’authentification anonyme.
