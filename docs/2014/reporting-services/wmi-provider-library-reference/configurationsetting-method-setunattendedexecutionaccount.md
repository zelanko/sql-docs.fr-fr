---
title: SetUnattendedExecutionAccount, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetUnattendedExecutionAccount method
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
caps.latest.revision: 18
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 91668016e2372ed5eb87453bb6c003f8bf25c122
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142422"
---
# <a name="setunattendedexecutionaccount-method-wmi-msreportserverconfigurationsetting"></a>Méthode SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting)
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
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  