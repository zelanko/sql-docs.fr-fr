---
title: "Méthode de RemoveSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting) | Documents Microsoft"
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
helpviewer_keywords:
- RemoveSSLCertificateBindings method
ms.assetid: b8b484c9-04c4-4ae9-980e-67bbe5aa8481
caps.latest.revision: 12
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2a4c9fe3ff515e9c6dce2986d19b75a61ac0b548
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="configurationsetting-method---removesslcertificatebinding"></a>Méthode ConfigurationSetting - RemoveSSLCertificateBinding
  Supprime une liaison de certificat SSL.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub RemoveSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal Lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void RemoveSSLCertificateBindings(string Application,  
    string CertificateHash, string IPAddress, Int32 Port, Int32 Lcid,  
    out string Error, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Application*  
 Nom de l'application pour laquelle la liaison de certificat doit être supprimée.  
  
 *CertificateHash*  
 Hachage du certificat.  
  
 *IPAddress*  
 Adresse IP de l'application.  
  
 *Port*  
 Port SSL associé à la liaison.  
  
 *lcid*  
 Paramètres régionaux à utiliser pour les messages d’erreur renvoyés.  
  
 *Erreur*  
 [out] Description de l'erreur qui s'est produite.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. La valeur 0 indique que l'appel de la méthode a abouti ; un code d'erreur indique que l'appel n'a pas abouti.  
  
## <a name="remarks"></a>Notes  
 Cette méthode supprime la liaison spécifique du fichier rsreportserver.config et éventuellement HTTP.SYS.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
