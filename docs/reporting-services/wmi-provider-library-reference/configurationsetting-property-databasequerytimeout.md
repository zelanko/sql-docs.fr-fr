---
title: "DatabaseQueryTimeout, propriété (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
apiname: DatabaseQueryTimeout Property
apilocation: reportingservices.mof
apitype: MOFDef
helpviewer_keywords: DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
caps.latest.revision: "35"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 8c56a5f4102236affc6860aea200857509d4e2af
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="configurationsetting-property---databasequerytimeout"></a>Propriété ConfigurationSetting - DatabaseQueryTimeout
  Spécifie le nombre de secondes qui doivent s'écouler avant que le serveur de rapports suppose que la commande a échoué ou a pris trop de temps pour s'exécuter. Le serveur de rapports établit la valeur de minutage de la requête par rapport au catalogue SQL Server et non par rapport à une source de données du rapport. En lecture/écriture.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Objet **integer** non signé 32 bits qui représente le nombre de secondes pendant lesquelles la requête est autorisée à s’exécuter.  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
