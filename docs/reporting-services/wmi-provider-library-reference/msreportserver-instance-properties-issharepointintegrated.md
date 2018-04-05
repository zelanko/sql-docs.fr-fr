---
title: IsSharePointIntegrated, propriété (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: ''
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 67fc8c606dfa194a8b5fe6c7ec3fb647628f0022
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="msreportserverinstance-properties---issharepointintegrated"></a>Propriétés MSReportServer_Instance - IsSharePointIntegrated
  Spécifie si le serveur de rapports s'exécute en mode intégré SharePoint. À compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], cette propriété retourne toujours **False** , car en mode SharePoint, les instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sont des services partagés SharePoint et elles ne sont pas contrôlées par les fournisseurs WMI.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Valeur **Boolean** qui indique si le serveur de rapports fonctionne en mode intégré SharePoint.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a> Voir aussi  
 [Membres MSReportServer_Instance](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-members.md)   
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
  
