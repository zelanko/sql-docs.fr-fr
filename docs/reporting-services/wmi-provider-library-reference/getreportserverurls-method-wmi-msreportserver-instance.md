---
title: "M&#233;thode GetReportServerUrls (WMI MSReportServer_Instance) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "méthode GetReportServerUrls"
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
caps.latest.revision: 12
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# M&#233;thode GetReportServerUrls (WMI MSReportServer_Instance)
  Retourne la liste des URL que les utilisateurs peuvent employer pour accéder au serveur de rapports et au [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)].  
  
## Syntaxe  
  
```vb  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## Paramètres  
 *ApplicationName[]*  
 Tableau qui contient les applications installées. Les valeurs sont **ReportServerWebService** ou **ReportServerWebApp**.  
  
 *URLs[]*  
 Tableau qui contient les URL inscrites avec succès.  
  
 *Longueur*  
 Valeur entière qui contient la longueur des tableaux retournés.  
  
 *HRESULT*  
 Valeur qui indique le succès ou un code d'erreur.  
  
## Valeurs de retour  
  
## Notes  
 Les méthodes exposées par les objets de gestion WMI sont appelées par le biais de la fonction InvokeMethod. Pour plus d’informations, consultez la section relative à l’exécution des méthodes sur des objets de gestion dans la documentation WMI du [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  