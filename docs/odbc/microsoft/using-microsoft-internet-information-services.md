---
title: Utilisation des services d’information Internet Microsoft (en anglais seulement) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c71babf933c2615e6c2464696c1023ccaf53dd7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282463"
---
# <a name="using-microsoft-internet-information-services"></a>Utilisation de Microsoft Internet Information Services
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Si vous avez de la difficulté à vous connecter à partir d’un script IIS (en particulier si vous recevez une erreur ORA-12641), ajoutez la ligne suivante au fichier Sqlnet.ora :  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```  
  
 Cela désactivera les services de réseau sécurisé afin que vous puissiez vous connecter à l’aide d’authentification anonyme.
