---
title: SetWindowsServiceIdentity, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
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
ms.openlocfilehash: d08e9900453fe259d727e202489d728e0dce47e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66097876"
---
# <a name="setwindowsserviceidentity-method-wmi-msreportserver_configurationsetting"></a>Méthode SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting)
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
 *UseBuiltInAccount a*  
 Indique si le compte spécifié est un compte Windows intégré.  
  
 *Compte*  
 Compte Windows à utiliser pour exécuter le service Windows, au format « DOMAINE\alias ».  
  
 *Mot de passe*  
 Mot de passe du compte.  
  
 *SIGNÉ*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Lorsque le *paramètre UseBuiltInAccount a* a la valeur `true` et que le serveur de rapports s’exécute [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] sur Microsoft ou Windows XP, la valeur des paramètres *Name*, *Domain*et *Password* est ignorée et le compte système local est utilisé.  
  
 Lorsque le paramètre *UseBuiltInAccount a* a la valeur `true` et que le serveur de rapports s’exécute sur Windows Server 2003, les propriétés *Domain* et *Password* sont ignorées, et le champ Name doit contenir « Builtin\system » ou « , » ou « Builtin\LocalService ».  
  
 La méthode SetWindowsServiceIdentity définit des autorisations d’accès aux fichiers sur les fichiers et les dossiers dans le répertoire d’installation du serveur de rapports.  
  
 Le compte spécifié dans le ** paramètre de compte `LogonAsService` requiert des droits dans Windows. La méthode accorde ce droit au compte spécifié.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
