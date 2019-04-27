---
title: SetWindowsServiceIdentity, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dc59e8a963f39a3686e7d7cb02cd2e2b17a39783
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62646335"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserverconfigurationsetting"></a>Méthode SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting)
  Fait en sorte que le service Windows Report Server s'exécute en tant qu'utilisateur Windows spécifié et accorde des autorisations de système de fichiers suffisantes à ce compte pour permettre au serveur de rapports de fonctionner.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetWindowsServiceIdentity(UseBuiltInAccount as Boolean, _  
    Account as String, Password as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetWindowsServiceIdentity(boolean UseBuiltInAccount,   
    string Account, string Password, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *UseBuiltInAccount*  
 Indique si le compte spécifié est un compte Windows intégré.  
  
 *Compte*  
 Compte Windows à utiliser pour exécuter le service Windows, au format « DOMAINE\alias ».  
  
 *Mot de passe*  
 Mot de passe du compte.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Lorsque le *UseBuiltInAccount* paramètre est défini sur `true` et le serveur de rapports s’exécute sur Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] ou Windows XP, la valeur de la *nom*, *domaine*, et *mot de passe* paramètres sont ignorés et le compte système Local est utilisé.  
  
 Lorsque le *UseBuiltInAccount* paramètre est défini sur `true` et le serveur de rapports s’exécute sur Windows Server 2003, le *domaine* et *mot de passe* sont des propriétés ignoré, et le champ nom doit contenir « Builtin\system » ou « Builtin\System » ou « Builtin\LocalService ».  
  
 La méthode SetWindowsServiceIdentity définit des autorisations d’accès aux fichiers sur les fichiers et les dossiers dans le répertoire d’installation du serveur de rapports.  
  
 Le compte spécifié dans le *compte* paramètre nécessite `LogonAsService` droits dans Windows. La méthode accorde ce droit au compte spécifié.  
  
## <a name="requirements"></a>Configuration requise  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
