---
title: "M&#233;thode SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "méthode SetUnattendedExecutionAccount"
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# M&#233;thode SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting)
  Spécifie le compte utilisé pour exécuter des rapports sans assistance.  
  
## Syntaxe  
  
```vb  
Public Sub SetUnattendedExecutionAccount(UserName as String, _  
    Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetUnattendedExecutionAccount (string UserName,   
    string Password, out Int32 HRESULT);  
```  
  
## Paramètres  
 *UserName*  
 Compte Windows à utiliser pour les exécutions sans assistance.  
  
 *Mot de passe*  
 Mot de passe du compte spécifié.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## Notes  
 La méthode SetUnattendedExecutionAccount ne vérifie pas si le serveur de rapports peut se connecter en tant que l’utilisateur spécifié.  
  
 Il est impossible d’utiliser la méthode SetUnattendedExecutionAccount pour exécuter des exécutions sans assistance dans le contexte du service Windows de serveur de rapports.  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  