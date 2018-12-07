---
title: RSWindowsExtendedProtectionLevel, propriété | Microsoft Docs
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 91f3e68d165ab288fd3329b2335797b6323e0e46
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52407456"
---
# <a name="rswindowsextendedprotectionlevel-property"></a>Propriété RSWindowsExtendedProtectionLevel
  Retourne une valeur de chaîne indiquant le niveau de protection configuré pour le serveur de rapports. Cette propriété est en lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## <a name="remarks"></a>Notes   
 Retourne une valeur de chaîne indiquant le niveau de protection configuré pour le serveur de rapports. Si le serveur de rapports auquel le fournisseur WMI est connecté ne prend pas en charge la protection étendue, "" (chaîne vide) est retourné. La liste suivante affiche les valeurs valides :  
  
 `"Off" | "Allow" | "Require"`  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="see-also"></a> Voir aussi  
 [Propriété RSWindowsExtendedProtectionScenario &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionscenario-property.md)   
 [Méthode SetExtendedProtectionSettings &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-setextendedprotectionsettings.md)   
 [Protection étendue de l’authentification avec Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [Fichier de configuration RSReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  
