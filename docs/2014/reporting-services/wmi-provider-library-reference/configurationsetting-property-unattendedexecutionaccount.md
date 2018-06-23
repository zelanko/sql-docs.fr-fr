---
title: UnattendedExecutionAccount, propriété (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- UnattendedExecutionAccount
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- UnattendedExecutionAccount property
ms.assetid: ab5203ba-c01e-4020-8619-ee290cf9da07
caps.latest.revision: 17
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 4f97cc66d94459064cc9e71806641533e9cbc064
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36053218"
---
# <a name="unattendedexecutionaccount-property-wmi-msreportserverconfigurationsetting"></a>Propriété UnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting)
  Retourne le compte d'utilisateur dont le serveur de rapports emprunte l'identité lorsqu'il exécute des rapports sans assistance. En lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim UnattendedExecutionAccount As String  
```  
  
```csharp  
public string UnattendedExecutionAccount;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Objet `String` qui représente le nom du compte.  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  