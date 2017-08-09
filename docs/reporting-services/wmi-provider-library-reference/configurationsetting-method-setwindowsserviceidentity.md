---
title: "Méthode de SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting) | Documents Microsoft"
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
apiname:
- SetWindowsServiceIdentity (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetWindowsServiceIdentity method
ms.assetid: 9bbc734c-9e69-48c2-8bec-8abe7c6cc987
caps.latest.revision: 19
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 935e2d44cbfd0363832eb6401b63d4a0b36623b4
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---setwindowsserviceidentity"></a>Méthode ConfigurationSetting - SetWindowsServiceIdentity
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
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Quand le paramètre *UseBuiltInAccount* a la valeur **true** et que le serveur de rapports s’exécute sur Microsoft [!INCLUDE[win2kfamily](../../includes/win2kfamily-md.md)] ou Windows XP, la valeur des paramètres *Name*, *Domain*et *Password* est ignorée et le compte système Local est utilisé.  
  
 Quand le paramètre *UseBuiltInAccount* a la valeur **true** et que le serveur de rapports s’exécute sur Windows Server 2003, les propriétés *Domain* et *Password* sont ignorées et le champ de nom doit contenir « Builtin\NetworkService », « Builtin\System » ou « Builtin\LocalService ».  
  
 La méthode SetWindowsServiceIdentity définit des autorisations d’accès aux fichiers sur les fichiers et les dossiers dans le répertoire d’installation du serveur de rapports.  
  
 Le compte spécifié dans le paramètre *Account* requiert des droits **LogonAsService** dans Windows. La méthode accorde ce droit au compte spécifié.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
