---
title: "M&#233;thode ListIPAddresses (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "méthode ListIPAddresses"
ms.assetid: 7e7cf182-fba0-4604-a474-098461e23e9d
caps.latest.revision: 12
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# M&#233;thode ListIPAddresses (WMI MSReportServer_ConfigurationSetting)
  Répertorie les adresses IP de l'ordinateur serveur de rapports.  
  
## Syntaxe  
  
```vb  
Public Sub ListIPAddresses (ByRef IPAddress() as String, _  
    ByRef IPVersion()as String, ByRef IsDhcpEnabled () as Boolean, _   
    ByRef Length as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListIPAddresses (out string[] IPAddress,   
    out string[] IPVersion, out bool[] isDhcpEnabled, out int length,   
    out int HRESULT);  
```  
  
## Paramètres  
 *IPAddress[]*  
 [out] La liste d'adresses IP de l'ordinateur.  
  
 *IPVersion[]*  
 [out] La version des adresses IP.  
  
 *IsDhcpEnabled[]*  
 [out] Indique si les adresses IP sont compatibles DHCP.  
  
 *Longueur*  
 [out] Longueur du tableau retourné par la méthode.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. La valeur 0 indique que l'appel de la méthode a abouti ; un code d'erreur indique que l'appel n'a pas abouti.  
  
## Notes  
 Les chaînes*IPVersion* sont V4, V6.  
  
 Si *IsDhcpEnabled* a la valeur **True**, l' *IPAddress* est dynamique. Elle ne doit pas être utilisée pour les liaisons SSL.  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  