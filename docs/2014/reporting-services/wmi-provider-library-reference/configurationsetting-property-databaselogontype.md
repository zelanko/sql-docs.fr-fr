---
title: DatabaseLogonType, propriété (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseLogonType
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: a8bbbcc9ba9f1eefad4801a0e9294affea4ef39a
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020583"
---
# <a name="databaselogontype-property-wmi-msreportserverconfigurationsetting"></a>Propriété DatabaseLogonType (WMI MSReportServer_ConfigurationSetting)
  Spécifie si le serveur de rapports utilise un compte de service [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, un compte d’utilisateur Windows ou un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour accéder à la base de données du serveur de rapports. En lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Objet `integer` qui représente le type de connexion.  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Notes  
 Valeurs possibles :  
  
-   0 pour une connexion Windows  
  
-   1 pour une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   2 pour une connexion en tant que service.  
  
 Si vous spécifiez 0 (Windows), vous devez définir la valeur dans la propriété [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) en fonction d’un compte d’utilisateur Windows valide correspondant.  
  
 Si vous spécifiez 1 (SQL Server), assurez-vous que la valeur de la propriété [DatabaseLogonAccount](configurationsetting-property-databaselogonaccount.md) correspond à une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide.  
  
 Si vous spécifiez 2 (service Windows), le serveur de rapports utilise un compte [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] et le compte de service Windows pour accéder à la base de données du serveur de rapports. La propriété DatabaseLogonAccount est ignorée.  
  
## <a name="requirements"></a>Configuration requise  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
