---
title: "M&#233;thode RemoveURL (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
helpviewer_keywords: 
  - "méthode RemoveURL"
ms.assetid: 3d98bd97-e152-48ce-ab1c-bd2c4f8b7fe9
caps.latest.revision: 13
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# M&#233;thode RemoveURL (WMI MSReportServer_ConfigurationSetting)
  Supprime une URL réservée pour le serveur de rapports. Si plusieurs URL doivent être supprimées, elles doivent l'être l'une après l'autre en appelant cette API.  
  
## Syntaxe  
  
```vb  
Public Sub RemoveURL(ByVal Application As String, _  
    ByVal UrlString As String, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveURL(string Application, string UrlString, int Lcid,   
    out string Error, out int HRESULT);  
```  
  
## Paramètres  
 *Application*  
 Nom de l'application pour laquelle supprimer la réservation.  
  
 *URLString*  
 URL pour la réservation.  
  
 *lcid*  
 Paramètres régionaux à utiliser pour les messages d'erreur retournés.  
  
 *Erreur*  
 [out] Description de l'erreur qui s'est produite.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. La valeur 0 indique que l'appel de la méthode a abouti ; un code d'erreur indique que l'appel n'a pas abouti.  
  
## Notes  
 *UrlString* n’inclut pas le nom du répertoire virtuel. La [Méthode SetVirtualDirectory &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/setvirtualdirectory-method-wmi-msreportserver-configurationsetting.md) est fournie à cet effet.  
  
 Avant d’appeler la méthode [ReserveURL](../../reporting-services/wmi-provider-library-reference/reserveurl-method-wmi-msreportserver-configurationsetting.md), vous devez fournir une valeur pour la propriété de configuration VirtualDirectory du paramètre *Application*. Utilisez la [Méthode SetVirtualDirectory &#40;WMI MSReportServer_ConfigurationSetting&#41;](../../reporting-services/wmi-provider-library-reference/setvirtualdirectory-method-wmi-msreportserver-configurationsetting.md) pour définir la propriété VirtualDirectory.  
  
 Si un certificat SSL a été fourni par [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et qu'aucune autre URL n'en a besoin, il est supprimé.  
  
 Cette méthode entraîne un recyclage et un arrêt forcés de tous les domaines d'application autres que de configuration au cours de cette opération ; les domaines d'application sont redémarrés une fois cette opération terminée.  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  