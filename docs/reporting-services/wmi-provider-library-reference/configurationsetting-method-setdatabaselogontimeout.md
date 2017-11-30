---
title: "SetDatabaseLogonTimeout, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
apiname: SetDatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting Class)
apilocation: reportingservices.mof
apitype: MOFDef
helpviewer_keywords: SetDatabaseLogonTimeout method
ms.assetid: b8773596-5b98-4355-a4ab-4412e1317c67
caps.latest.revision: "19"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 6362913c89187ba66ede8ee15c578ffe7d5d69e2
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="configurationsetting-method---setdatabaselogontimeout"></a>Méthode ConfigurationSetting - SetDatabaseLogonTimeout
  Spécifie la valeur de délai par défaut pour l'établissement d'une connexion à la base de données du serveur de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetDatabaseLogonTimeout(LogonTimeout as Int32, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetDatabaseLogonTimeout(Int32 LogonTimeout,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *LogonTimeout*  
 Valeur de délai par défaut, en secondes, pour l'établissement d'une connexion à la base de données du serveur de rapports.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
