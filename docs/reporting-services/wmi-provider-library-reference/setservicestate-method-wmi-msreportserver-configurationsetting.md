---
title: "M&#233;thode SetServiceState (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
apiname: 
  - "SetServiceState (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "méthode SetServiceState"
ms.assetid: 9e1ee42d-b388-4929-89c7-8741b956c3be
caps.latest.revision: 20
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# M&#233;thode SetServiceState (WMI MSReportServer_ConfigurationSetting)
  Active ou désactive les services Web et Windows Report Server.  
  
## Syntaxe  
  
```vb  
Public Sub SetServiceState(ByVal EnableWindowsService As Boolean, _  
    ByVal EnableWebService As Boolean, ByVal EnableReportManager As Boolean, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Boolean EnableWindowsService,  
    Boolean EnableWebService, Boolean EnableReportManager, out Int32 HRESULT);  
```  
  
## Paramètres  
 *EnableWindowsService*  
 Valeur **booléenne** indiquant l’état du service Windows. La valeur **true** démarre le service Windows Report Server ; la valeur **false** arrête le service Windows.  
  
 *EnableWebService*  
 Valeur **booléenne** indiquant l’état du service web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. La valeur **true** démarre le service Web Report Server ; la valeur **false** arrête le service Web.  
  
 *EnableReportManager*  
 Valeur **booléenne** indiquant l’état souhaité du Gestionnaire de rapports.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## Notes  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  