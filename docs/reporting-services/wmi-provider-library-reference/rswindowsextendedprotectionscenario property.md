---
title: "Propri&#233;t&#233; RSWindowsExtendedProtectionScenario (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
caps.latest.revision: 6
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Propri&#233;t&#233; RSWindowsExtendedProtectionScenario (WMI MSReportServer_ConfigurationSetting)
  Retourne une valeur de chaîne indiquant le scénario de protection étendue que le serveur de rapports est configuré à autoriser.  
  
## Syntaxe  
  
```vb  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```csharp  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## Notes  
 Retourne une valeur de chaîne indiquant le scénario de protection étendue que le serveur de rapports est configuré à autoriser. Si le serveur de rapports auquel le fournisseur WMI est connecté ne prend pas en charge la protection étendue, “” (chaîne vide) est retourné.  
  
 La liste suivante affiche les valeurs valides :  
  
 `”Any | Proxy | Direct”`  
  
## Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## Voir aussi  
 [Propriété RSWindowsExtendedProtectionLevel &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/rswindowsextendedprotectionlevel-property.md)   
 [Méthode SetExtendedProtectionSettings &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/setextendedprotectionsettings-method-wmi-msreportserver-configurationsetting.md)   
 [Protection étendue de l'authentification avec Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md)   
 [Fichier de configuration RSReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)  
  
  