---
title: "Le propriété SecureConnectionLevel (WMI MSReportServer_ConfigurationSetting) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SecureConnectionLevel
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SecureConnectionLevel property
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
caps.latest.revision: 19
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 926be7ba1e11f82f6306b8828b84823a91b3d515
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="configurationsetting-property---secureconnectionlevel"></a>Propriété ConfigurationSetting - SecureConnectionLevel
  Retourne le niveau de connexion sécurisée qui est spécifié dans le fichier RSReportServer.config. En lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim SecureConnectionLevel As Integer  
```  
  
```csharp  
public Integer SecureConnectionLevel;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Valeur de type **Entier** qui représente le niveau de la connexion sécurisée. Les valeurs de retour indiquent que le protocole SSL est configuré ou non. Une valeur supérieure ou égale à 1 indique que le protocole SSL est activé. La valeur 0 indique que le protocole SSL est désactivé.  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
