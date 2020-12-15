---
description: SqlToolsVSNativeHelpers - FrameWindowVisible
title: FrameWindowVisible | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 9091d714-98bc-43ec-b8d1-9c892cb57f19
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b411a72494c4c691c7f5899d021e38a7f48fec02
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97415947"
---
# <a name="sqltoolsvsnativehelpers---framewindowvisible"></a>SqlToolsVSNativeHelpers - FrameWindowVisible
[!INCLUDE [SQL Server Azure SQL Database](../includes/applies-to-version/sql-asdb.md)]
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
  
## <a name="see-also"></a>Voir aussi  
 [SqlToolsVSNativeHelpers](../relational-databases/sqltoolsvsnativehelpers.md)  
  
  
