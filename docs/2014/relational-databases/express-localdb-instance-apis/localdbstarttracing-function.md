---
title: LocalDBStartTracing fonction) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_name:
- LocalDBStartTracing
api_location:
- sqluserinstance.dll
topic_type:
- apiref
ms.assetid: c7b83833-6d2a-4a06-9cb7-42767bed52c6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: aed6261312414d114fdf9ed92b111d44fbb0f93c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050988"
---
# <a name="localdbstarttracing-function"></a>Fonction LocalDBStartTracing
  Active le suivi des appels d'API pour toutes les instances SQL Server Express LocalDB détenues par l'utilisateur Windows actuel.  
  
 **Fichier d'en-tête :** sqlncli.h  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LocalDBStartTracing();  
```  
  
## <a name="returns"></a>Retours  
 S_OK  
 La fonction a réussi.  
  
 [LOCALDB_ERROR_XEVENT_FAILED](../express-localdb-error-messages/localdb-error-xevent-failed.md)  
 Échec du démarrage du moteur XEvent dans l'API de l'instance de LocalDB.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../express-localdb-error-messages/localdb-error-internal-error.md)  
 Une erreur inattendue s’est produite. Pour plus d'informations, consultez le journal des événements.  
  
## <a name="remarks"></a>Remarques  
 Pour un exemple de code qui utilise l'API LocalDB, consultez [SQL Server Express LocalDB Reference](../sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [En-tête et informations de version SQL Server Express LocalDB](sql-server-express-localdb-header-and-version-information.md)  
  
  
