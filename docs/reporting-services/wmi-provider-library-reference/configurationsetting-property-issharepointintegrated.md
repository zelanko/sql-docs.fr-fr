---
description: Propriété ConfigurationSetting - IsSharePointIntegrated
title: IsSharePointIntegrated, propriété (WMI) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: c548fed8-5e04-4faf-8b10-b37c86178056
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 628212c9538b3a2efea08b0fdfb5def7fe017e10
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497902"
---
# <a name="configurationsetting-property---issharepointintegrated"></a>Propriété ConfigurationSetting - IsSharePointIntegrated
  Spécifie si le serveur de rapports s'exécute en mode intégré SharePoint. À compter de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], cette propriété retourne toujours **False** , car en mode SharePoint, les instances de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sont des services partagés SharePoint et elles ne sont pas contrôlées par les fournisseurs WMI.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Objet **Boolean** qui indique si le serveur de rapports fonctionne en mode intégré SharePoint.  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
