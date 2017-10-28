---
title: "Méthode SetServiceState (WMI MSReportServer_ConfigurationSetting) | Documents Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SetServiceState (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceState method
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
caps.latest.revision: 20
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8964b2b0886ffd0483e48c8e9baf91ab9b2dae3d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---setservicestate"></a>Méthode ConfigurationSetting - SetServiceState
  Active ou désactive les services Web et Windows Report Server.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetServiceState(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *EnableWindowsService*  
 Valeur **booléenne** indiquant l’état du service Windows. La valeur **true** démarre le service Windows Report Server ; la valeur **false** arrête le service Windows.  
  
 *EnableWebService*  
 Valeur **booléenne** indiquant l’état du service web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . La valeur **true** démarre le service Web Report Server ; la valeur **false** arrête le service Web.  
  
 *EnableReportManager*  
 Valeur **booléenne** indiquant l’état souhaité du Gestionnaire de rapports.
 
 > [!NOTE] 
 > Ce paramètre est déconseillé à compter de SQL Server 2016 Reporting Services Cumulative Update 2. Le portail web est toujours activé. La valeur sera ignorée.
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  

