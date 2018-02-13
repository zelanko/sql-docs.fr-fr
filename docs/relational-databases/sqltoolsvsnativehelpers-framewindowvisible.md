---
title: FrameWindowVisible | Microsoft Docs
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: relational-databases-misc
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9091d714-98bc-43ec-b8d1-9c892cb57f19
caps.latest.revision: 
author: JennieHubbard
ms.author: jhubbard
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b04e1fee4c50b9ac61a9cd44166c2410bd43e5e9
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2018
---
# <a name="sqltoolsvsnativehelpers---framewindowvisible"></a>SqlToolsVSNativeHelpers - FrameWindowVisible
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Propriété qui spécifie si un cadre de fenêtre donné est visible. La méthode implémentée par l'application auxiliaire est utilisée à partir du code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL WINAPI IsFrameWindowVisible(IVsWindowFrame* frame)  
{  
    if (NULL == frame)  
    {  
        return FALSE;  
    }  
  
    return S_OK == frame->IsVisible();  
}  
```  
  
#### <a name="parameters"></a>Paramètres  
 *frame*  
  
 Pointeur IVsWindowFrame* vers un WindowFrame Visual Studio.  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Valeur booléenne qui spécifie si le cadre de la fenêtre spécifié par *frame* est visible.  
  
## <a name="see-also"></a> Voir aussi  
 [SqlToolsVSNativeHelpers](../relational-databases/sqltoolsvsnativehelpers.md)  
  
  
