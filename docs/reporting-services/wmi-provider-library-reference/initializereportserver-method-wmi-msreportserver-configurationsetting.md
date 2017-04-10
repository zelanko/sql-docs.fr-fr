---
title: "InitializeReportServer Method (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "InitializeReportServer method"
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
caps.latest.revision: 21
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# InitializeReportServer Method (WMI MSReportServer_ConfigurationSetting)
  Initialise l'instance du service de rapports spécifiée.  
  
## Syntaxe  
  
```vb  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## Paramètres  
 *InstallationID*  
 Chaîne utilisée pour chiffrer la clé de chiffrement avant qu'elle soit retournée.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
 *ExtendedErrors[]*  
 [out] Tableau de chaînes contenant les erreurs supplémentaires retournées par l'appel.  
  
## Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## Notes  
 Lorsque cette méthode est appelée, la clé de chiffrement qui accède aux informations sécurisées de la base de données du serveur de rapports est chiffrée à l'aide de la clé publique du serveur de rapports identifiée par *InstallationID*.  
  
 La clé publique du serveur de rapports spécifiée doit au préalable avoir été écrite dans la base de données du serveur de rapports.  
  
 La méthode *InitializeReportServer* doit être appelée contre un serveur de rapports qui a déjà accès aux informations sécurisées, afin qu'il puisse déchiffrer la clé de chiffrement. La clé de chiffrement chiffrée résultante est ensuite stockée dans la base de données du serveur de rapports.  
  
 Si la propriété [IsInitialized](../../reporting-services/wmi-provider-library-reference/isinitialized-property-wmi-msreportserver-configurationsetting.md) du serveur de rapports a la valeur **true** quand la méthode InitializeReportServer est appelée, la méthode aboutit sans essayer de chiffrer la clé de chiffrement.  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  