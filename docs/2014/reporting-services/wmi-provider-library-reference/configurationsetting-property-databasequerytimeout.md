---
title: DatabaseQueryTimeout, propriété (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
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
caps.latest.revision: 35
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2cf7248fe0052a23e3ceef2243a4b6b45645402b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257995"
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
 Non signé 32 bits `integer` objet qui représente le nombre de secondes pendant lesquelles la requête est autorisée à exécuter.  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
