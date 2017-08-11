---
title: "Propriété RSWindowsExtendedProtectionScenario | Documents Microsoft"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
caps.latest.revision: 6
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6449b0b9d9e27c860d3246b4992cac6405af731f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="rswindowsextendedprotectionscenario-property"></a>Propriété RSWindowsExtendedProtectionScenario
  Retourne une valeur de chaîne indiquant le scénario de protection étendue que le serveur de rapports est configuré à autoriser.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## <a name="remarks"></a>Notes  
 Retourne une valeur de chaîne indiquant le scénario de protection étendue que le serveur de rapports est configuré à autoriser. Si le serveur de rapports auquel le fournisseur WMI est connecté ne prend pas en charge la protection étendue, “” (chaîne vide) est retourné.  
  
 La liste suivante affiche les valeurs valides :  
  
 `”Any | Proxy | Direct”`  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété RSWindowsExtendedProtectionLevel &#40; WMI MSReportServer_ConfigurationSetting &#41;](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionlevel-property.md)   
 [Méthode SetExtendedProtectionSettings &#40; WMI MSReportServer_ConfigurationSetting &#41;](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md)   
 [Protection étendue pour l’authentification avec Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [Fichier de configuration RSReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
