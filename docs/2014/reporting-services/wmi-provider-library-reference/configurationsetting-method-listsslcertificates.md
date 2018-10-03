---
title: ListSSLCertificates, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListSSLCertificates method
ms.assetid: 88cd0936-b202-4ab8-90f2-d9c3f66d37f4
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a83096e8b1fe3eed9e0df513931b812125955f61
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221719"
---
# <a name="listsslcertificates-method-wmi-msreportserverconfigurationsetting"></a>Méthode ListSSLCertificates (WMI MSReportServer_ConfigurationSetting)
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
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
