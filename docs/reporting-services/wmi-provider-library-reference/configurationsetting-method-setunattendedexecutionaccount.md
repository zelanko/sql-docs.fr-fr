---
description: Méthode SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting)
title: SetUnattendedExecutionAccount, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetUnattendedExecutionAccount method
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5f65c36ae1f27039061642dba87ec79b6f81c7c2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497922"
---
# <a name="configurationsetting-method---setunattendedexecutionaccount"></a>Méthode ConfigurationSetting - SetUnattendedExecutionAccount
  Spécifie le compte utilisé pour exécuter des rapports sans assistance.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetUnattendedExecutionAccount(UserName as String, _  
    Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetUnattendedExecutionAccount (string UserName,   
    string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *UserName*  
 Compte Windows à utiliser pour les exécutions sans assistance.  
  
 *Mot de passe*  
 Mot de passe du compte spécifié.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 La méthode SetUnattendedExecutionAccount ne vérifie pas si le serveur de rapports peut se connecter en tant que l’utilisateur spécifié.  
  
 Il est impossible d’utiliser la méthode SetUnattendedExecutionAccount pour exécuter des exécutions sans assistance dans le contexte du service Windows de serveur de rapports.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
