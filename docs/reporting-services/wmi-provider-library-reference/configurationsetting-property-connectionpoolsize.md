---
title: "Propriété de ConnectionPoolSize (WMI MSReportServer_ConfigurationSetting) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ConnectionPoolSize
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- ConnectionPoolSize property
ms.assetid: b80c8e5d-b725-4fe4-aec6-02fb18ec4434
caps.latest.revision: 17
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b329ec9fee9cdf8df13e4272157c2915b6d64996
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-property---connectionpoolsize"></a>Propriété ConfigurationSetting - ConnectionPoolSize
  Taille du pool de connexions qu’utilise le serveur de rapports pour communiquer avec l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données du serveur de rapports. En lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim ConnectionPoolSize As UInt32  
```  
  
```csharp  
public UInt32 ConnectionPoolSize;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Objet **integer** en lecture seule qui renvoie la valeur **768**.  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
