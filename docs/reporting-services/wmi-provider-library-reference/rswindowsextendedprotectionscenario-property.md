---
title: "RSWindowsExtendedProtectionScenario, propriété | Microsoft Docs"
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
caps.latest.revision: "6"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 06257c6bc32ba8ae073eb78518c4298c724834b0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
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
 [Propriété RSWindowsExtendedProtectionLevel &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionlevel-property.md)   
 [Méthode SetExtendedProtectionSettings &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md)   
 [Protection étendue de l’authentification avec Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [Fichier de configuration RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
