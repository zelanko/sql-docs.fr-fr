---
title: SQLGetCursorName | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetCursorName function
ms.assetid: 3a427a23-28ef-49aa-b9ec-6cab0914bdf3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7e9161170665d421b235a3a121ab8bb761e32daf
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706067"
---
# <a name="sqlgetcursorname"></a>SQLGetCursorName
  Si l'application ne spécifie pas de nom de curseur, le pilote ODBC de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client en génère un pour l'application lors de la génération du curseur. L'application peut utiliser **SQLGetCursorName** pour récupérer le nom du curseur défini par le pilote pour les instructions UPDATE et DELETE positionnées. L'application n'a pas besoin d'appeler **SQLSetCursorName** pour tirer parti des instructions de manipulation de données positionnées.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLGetCursorName, fonction](https://go.microsoft.com/fwlink/?LinkId=59349)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
