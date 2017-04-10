---
title: "Propri&#233;t&#233; DatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "DatabaseLogonTimeout Property"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "propriété DatabaseLogonTimeout"
ms.assetid: 4a65162c-33de-485e-8fd3-2bd6bff8bf8d
caps.latest.revision: 38
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# Propri&#233;t&#233; DatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting)
  Spécifie le délai d'attente, en secondes, avant l'échec d'une tentative de connexion à la base de données du serveur de rapports. La valeur **0** indique une durée d’attente illimitée. Lecture seule.  
  
## Syntaxe  
  
```vb  
Public Dim DatabaseLogonTimeout As Int32  
```  
  
```csharp  
public Int32 DatabaseLogonTimeout;  
```  
  
## Valeurs de la propriété  
 Objet entier signé 32 bits qui représente le nombre de secondes.  
  
## Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  