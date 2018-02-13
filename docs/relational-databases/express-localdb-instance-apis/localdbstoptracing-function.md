---
title: Fonction LocalDBStopTracing | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- LocalDBStopTracing
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: 1d50e040-8602-4ffa-be8f-b8633fdfa7ff
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fc1dffb89ed6d2e299c79a1b4d1bdf33b0ad58ae
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2018
---
# <a name="localdbstoptracing-function"></a>Fonction LocalDBStopTracing
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Désactive le suivi des appels d'API pour toutes les instances SQL Server Express LocalDB détenues par l'utilisateur Windows actuel.  
  
 **Fichier d'en-tête :** sqlncli.h  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LocalDBStopTracing();  
```  
  
## <a name="returns"></a>Valeur renvoyée  
 Cette méthode signale les erreurs en attribuant à la propriété Nombre de l'objet Err global l'une des valeurs du tableau suivant.  
 La fonction a réussi.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Une erreur inattendue s'est produite. Pour plus d'informations, consultez le journal des événements.  
  
## <a name="remarks"></a>Notes  
 Pour un exemple de code qui utilise l'API LocalDB, consultez [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [En-tête et informations de version de la base de données locale SQL Server Express](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
