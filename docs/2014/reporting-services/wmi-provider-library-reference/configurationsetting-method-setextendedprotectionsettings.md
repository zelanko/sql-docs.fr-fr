---
title: SetExtendedProtectionSettings, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 95e65172d70b13591afbc84b0433c372ab64be7e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36044672"
---
# <a name="setextendedprotectionsettings-method-wmi-msreportserverconfigurationsetting"></a>Méthode SetExtendedProtectionSettings (WMI MSReportServer_ConfigurationSetting)
  La méthode SetExtendedProtectionSettings sert à définir les propriétés RSWindowsExtendedProtectionLevel et RSWindowsExtendedProtectionScenario dans le fichier de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (RSReportServer.config).  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *ExtendedProtectionLevel*  
 Définit RSWindowsExtendedProtectionLevel dans le fichier RSRreportserver.config. La valeur est obligatoire et ne respecte pas la casse.  
  
 La liste suivante affiche les valeurs valides :  
  
 `”Off | Allow | Require”`  
  
 *ExtendedProtectionScenario*  
 Définit RSWindowsExtendedProtectionScenario dans le fichier RSReportserver.config. La valeur est obligatoire et ne respecte pas la casse.  
  
 La liste suivante affiche les valeurs valides :  
  
 `”Any” | “Proxy” | “Direct”`  
  
## <a name="remarks"></a>Notes  
 Les propriétés RSWindowsExtendedProtectionLevel et RSWindowsExtendedProtectionScenario s'appliquent lorsque AuthenticationTypes dans le fichier RSReportServer.config inclut RSWindowNTLM, RSWindowsNegotiate ou RSWindowsKerberos. La définition de ces propriétés change la manière dont les utilisateurs et le logiciel client sont authentifiés au niveau du serveur de rapports. Il est recommandé de lire la documentation pour la protection étendue avant de définir la propriété ExtendedProtectionLevel sur `Allow` ou `Require`.  
  
 Pour définir la propriété ExtendedProtectionLevel, l'utilisateur doit être un membre du groupe BUILTIN\Administrators sur le serveur de rapports.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Propriété RSWindowsExtendedProtectionScenario &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionscenario-property.md)   
 [Propriété RSWindowsExtendedProtectionLevel &#40;WMI MSReportServer_ConfigurationSetting&#41;](rswindowsextendedprotectionlevel-property.md)   
 [Protection étendue de l’authentification avec Reporting Services](../security/extended-protection-for-authentication-with-reporting-services.md)   
 [Fichier de Configuration RSReportServer](../report-server/rsreportserver-config-configuration-file.md)  
  
  