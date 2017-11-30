---
title: "SetDatabaseQueryTimeout, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname: SetDatabaseQueryTimeout (WMI MSReportServer_ConfigurationSetting Class)
apilocation: reportingservices.mof
apitype: MOFDef
helpviewer_keywords: SetDatabaseQueryTimeout method
ms.assetid: bd2809e5-7848-45b3-a502-b04fc698b646
caps.latest.revision: "19"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 8c32088405b7b3f8573362c243b7ec8da1bf3a7a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="configurationsetting-method---setdatabasequerytimeout"></a>Méthode ConfigurationSetting - SetDatabaseQueryTimeout
  Spécifie la valeur de délai par défaut pour les requêtes sur la base de données du serveur de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetDatabaseQueryTimeout(LogonTimeout as Int32, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetDatabaseQueryTimeout (Int32 LogonTimeout,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *LogonTimeout*  
 Valeur de délai par défaut, en secondes, pour les requêtes sur la base de données du serveur de rapports.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
