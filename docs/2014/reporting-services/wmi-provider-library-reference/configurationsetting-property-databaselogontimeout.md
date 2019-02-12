---
title: DatabaseLogonTimeout, propriété (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonTimeout property
ms.assetid: 4a65162c-33de-485e-8fd3-2bd6bff8bf8d
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: ef5793aa278d9d1a1b9a10f45a68dd5a97442f69
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56019130"
---
# <a name="databaselogontimeout-property-wmi-msreportserverconfigurationsetting"></a>Propriété DatabaseLogonTimeout (WMI MSReportServer_ConfigurationSetting)
  Spécifie le délai d'attente, en secondes, avant l'échec d'une tentative de connexion à la base de données du serveur de rapports. La valeur **0** indique une durée d’attente illimitée. Lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim DatabaseLogonTimeout As Int32  
```  
  
```csharp  
public Int32 DatabaseLogonTimeout;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Objet entier signé 32 bits qui représente le nombre de secondes.  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
