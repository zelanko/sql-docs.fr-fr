---
title: DatabaseLogonType, propriété (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- DatabaseLogonType
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DatabaseLogonType property
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 078c430e2300a0b80f85357f9f962e8e2dd72838
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65570904"
---
# <a name="configurationsetting-property---databaselogontype"></a>Propriété ConfigurationSetting - DatabaseLogonType
  Spécifie si le serveur de rapports utilise un compte de service [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, un compte d’utilisateur Windows ou un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour accéder à la base de données du serveur de rapports. En lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Dim DatabaseLogonType As Integer  
```  
  
```csharp  
public int DatabaseLogonType;  
```  
  
## <a name="property-values"></a>Valeurs de la propriété  
 Objet **entier** qui représente le type de connexion.  
  
## <a name="example-code"></a>Exemple de code  
 [Classe MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="remarks"></a>Notes  
 Valeurs possibles :  
  
-   0 pour une connexion Windows  
  
-   1 pour une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   2 pour une connexion en tant que service.  
  
 Si vous spécifiez 0 (Windows), vous devez définir la valeur dans la propriété [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogonaccount.md) en fonction d’un compte d’utilisateur Windows valide correspondant.  
  
 Si vous spécifiez 1 (SQL Server), assurez-vous que la valeur de la propriété [DatabaseLogonAccount](../../reporting-services/wmi-provider-library-reference/configurationsetting-property-databaselogonaccount.md) correspond à une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide.  
  
 Si vous spécifiez 2 (service Windows), le serveur de rapports utilise un compte [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] et le compte de service Windows pour accéder à la base de données du serveur de rapports. La propriété DatabaseLogonAccount est ignorée.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
