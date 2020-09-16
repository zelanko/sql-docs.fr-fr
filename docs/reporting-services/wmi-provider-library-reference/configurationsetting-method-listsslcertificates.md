---
description: Méthode ListSSLCertificates (WMI MSReportServer_ConfigurationSetting)
title: ListSSLCertificates, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificates method
ms.assetid: 88cd0936-b202-4ab8-90f2-d9c3f66d37f4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: b1c4aafdeeb348f3b4a3b4135a17ede2db8d4cfc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88468971"
---
# <a name="configurationsetting-method---listsslcertificates"></a>Méthode ConfigurationSetting - ListSSLCertificates
  Retourne la liste des certificats installés sur l'ordinateur serveur de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub CreateSSLCertificateBinding (ByRef CertificateHash() as String, _  
    ByRef CertName() as String, ByRef HostName() as String, ByRef Length as Int32, _   
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListSSLCertificates(out string[] CertificateHash,   
    out string[] CertName, out string[] Hostname, out Int32 length,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *CertificateHash[]*  
 [out] Hachages des certificats.  
  
 *CertName[]*  
 [out] Noms des certificats.  
  
 *HostName[]*  
 [out] Noms d'hôtes des certificats.  
  
 *Longueur*  
 [out] Représente la longueur des tableaux *CertificateHash*, *CertName* et *HostName* .  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. La valeur 0 indique que l'appel de la méthode a abouti ; un code d'erreur indique que l'appel n'a pas abouti.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
