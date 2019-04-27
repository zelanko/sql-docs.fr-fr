---
title: DatabaseQueryTimeout, propriété (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseQueryTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 25023ed146d00b8635b9ce822cbb2cdf23be65ec
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62646355"
---
# <a name="databasequerytimeout-property-wmi-msreportserverconfigurationsetting"></a>Propriété DatabaseQueryTimeout (WMI MSReportServer_ConfigurationSetting)
  Spécifie le nombre de secondes qui doivent s'écouler avant que le serveur de rapports suppose que la commande a échoué ou a pris trop de temps pour s'exécuter. Le serveur de rapports établit la valeur de minutage de la requête par rapport au catalogue SQL Server et non par rapport à une source de données du rapport. En lecture/écriture.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Objet `integer` non signé 32 bits qui représente le nombre de secondes pendant lesquelles la requête est autorisée à s'exécuter.  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
