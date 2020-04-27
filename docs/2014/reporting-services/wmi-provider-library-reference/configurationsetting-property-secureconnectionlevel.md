---
title: SecureConnectionLevel, propriété (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SecureConnectionLevel
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SecureConnectionLevel property
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5d1b3bccc8a7fee3899fa21208d83a718a33f5fb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66097560"
---
# <a name="secureconnectionlevel-property-wmi-msreportserver_configurationsetting"></a>Propriété SecureConnectionLevel (WMI MSReportServer_ConfigurationSetting)
  Retourne le niveau de connexion sécurisée qui est spécifié dans le fichier RSReportServer.config. Lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Valeur `Integer` qui représente le niveau de connexion sécurisée. Les valeurs de retour indiquent que le protocole SSL est configuré ou non. Une valeur supérieure ou égale à 1 indique que le protocole SSL est activé. La valeur 0 indique que le protocole SSL est désactivé.  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
