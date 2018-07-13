---
title: ListSSLCertificateBindings, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificateBindings method
ms.assetid: d12d280c-9b6f-47a8-bcd9-34cde31c8886
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 66de4c245aeb16af2667381b8ec6a42133a60099
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166120"
---
# <a name="listsslcertificatebindings-method-wmi-msreportserverconfigurationsetting"></a>Méthode ListSSLCertificateBindings (WMI MSReportServer_ConfigurationSetting)
  Retourne la liste des certificats SSL installés sur l'ordinateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub ListSSLCertificateBindings(ByVal LCID As Int32, ByRef Application() As String, _  
    ByRef CertificateHash() As String, ByRef IPAddresses() As String, ByRef Port() As Int32, _  
    ByRef Errors() As String, ByRef Length As Int32, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListSSLCertificateBindings(Int32 Lcid, out string[] Application,   
    out string[] CertificateHash,out string[] IPAddress,   
    out Int32[] Port, out string Errors,   
    out Int32 length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *LCID*  
 Paramètres régionaux à utiliser pour les messages d’erreur renvoyés.  
  
 *Application[]*  
 [out] Applications comportant des liaisons de certificat.  
  
 *CertificateHash[]*  
 [out] Hachages pour les certificats.  
  
 *IPAddress[]*  
 [out] Adresses IP des applications.  
  
 *Port[]*  
 [out] Numéro de port stocké dans la liaison dans rsreportserver.config.  
  
 *Errors[]*  
 [out] Descriptions des erreurs qui se sont produites.  
  
 *Longueur*  
 [out] Longueur du tableau retourné par la méthode.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
