---
title: DatabaseLogonAccount, propriété (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonAccount
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonAccount property
ms.assetid: 55f2863f-1ac1-4519-b512-e7f11c0ea5ea
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6f66f21b5c866688bd5c348f26788f4a869aca88
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48151949"
---
# <a name="databaselogonaccount-property-wmi-msreportserverconfigurationsetting"></a>Propriété DatabaseLogonAccount (WMI MSReportServer_ConfigurationSetting)
  Spécifie le compte d'ouverture de session utilisé par le serveur de rapports lors de la connexion à la base de données du serveur de rapports. Lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim DatabaseLogonAccount As String  
```  
  
```csharp  
public string DatabaseLogonAccount;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Objet `String` qui représente le nom du compte d'ouverture de session.  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Notes  
 Les valeurs valides pour cette propriété varient selon la valeur de la [DatabaseLogonType](configurationsetting-property-databaselogontype.md) propriété.  
  
 Cette propriété est ignorée si le [DatabaseLogonType](configurationsetting-property-databaselogontype.md) propriété est définie sur `2 (Service)`.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
