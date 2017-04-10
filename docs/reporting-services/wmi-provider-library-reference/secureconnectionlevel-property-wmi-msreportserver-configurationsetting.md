---
title: "Propri&#233;t&#233; SecureConnectionLevel (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "SecureConnectionLevel"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "Propriété SecureConnectionLevel"
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Propri&#233;t&#233; SecureConnectionLevel (WMI MSReportServer_ConfigurationSetting)
  Retourne le niveau de connexion sécurisée qui est spécifié dans le fichier RSReportServer.config. En lecture seule.  
  
## Syntaxe  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## Valeurs de la propriété  
 Valeur de type **Entier** qui représente le niveau de la connexion sécurisée. Les valeurs de retour indiquent que le protocole SSL est configuré ou non. Une valeur supérieure ou égale à 1 indique que le protocole SSL est activé. La valeur 0 indique que le protocole SSL est désactivé.  
  
## Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  