---
title: "Propri&#233;t&#233; IsSharePointIntegrated (WMI MSReportServer_Instance) | Microsoft Docs"
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
  - "propriété IsSharePointIntegrated"
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
caps.latest.revision: 13
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Propri&#233;t&#233; IsSharePointIntegrated (WMI MSReportServer_Instance)
  Spécifie si le serveur de rapports s'exécute en mode intégré SharePoint. À compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], cette propriété retourne toujours **False**, car en mode SharePoint, les instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sont des services partagés SharePoint et elles ne sont pas contrôlées par les fournisseurs WMI.  
  
## Syntaxe  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## Valeurs de la propriété  
 Valeur **Boolean** qui indique si le serveur de rapports fonctionne en mode intégré SharePoint.  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_Instance](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-members.md)   
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  