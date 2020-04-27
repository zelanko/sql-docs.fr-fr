---
title: CreateSSLCertificateBinding, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- CreateSSLCertificateBinding
ms.assetid: 407d50e4-0a55-43cb-8ddf-2d82714071b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f16b86b1343d83c44819427b8ba6c43726798e93
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098540"
---
# <a name="createsslcertificatebinding-method-wmi-msreportserver_configurationsetting"></a>Méthode CreateSSLCertificateBinding (WMI MSReportServer_ConfigurationSetting)
  Crée une liaison de certificat SSL.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub CreateSSLCertificateBinding(ByVal Application As String, _  
    ByVal CertificateHash As String, ByVal IPAddress As String, _  
    ByVal Port As Int32, ByVal lcid As Int32, _  
    ByRef [Error] As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void CreateSSLCertificateBinding(string application,   
    string certificateHash, string IPAddress, int Port,   
    int lcid, out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Application*  
 Nom de l'application pour laquelle la liaison de certificat doit être créée.  
  
 *CertificateHash*  
 Hachage du certificat.  
  
 *IPAddress*  
 Adresse IP de l'application.  
  
 *Port*  
 Port SSL associé à la liaison.  
  
 *Lcid*  
 Paramètres régionaux à utiliser pour les messages d'erreur retournés.  
  
 *Error*  
 [out] Description des erreurs qui se sont produites.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. La valeur 0 indique que l'appel de la méthode a abouti ; un code d'erreur indique que l'appel n'a pas abouti.  
  
## <a name="remarks"></a>Notes  
 Cette méthode ajoute une liaison à rsreportserver.config pour l'application. Si aucune liaison n'existe déjà dans HTTP.SYS, elle est créée ici.  
  
 Avant de créer la liaison, l'appel de méthode examine les réservations d'URL pour l'application spécifiée afin de déterminer si la liaison de certificat SSL est valide.  
  
 Les conditions suivantes sont validées et peuvent provoquer des erreurs :  
  
1.  Le certificat n'existe pas.  
  
2.  L'adresse IP spécifiée ne correspond à aucune adresse IP de cet ordinateur.  
  
3.  L’adresse IP spécifiée est une adresse IP DHCP (modifications régulières) ; utilisez plutôt l’adresse IP générique (0.0.0.0).  
  
4.  L'adresse IP spécifiée ne correspond pas à l'adresse IP des réservations d'URL ET il n'existe pas de réservation d'URL générique ni de nom d'hôte.  
  
5.  Une réservation d'URL qui spécifie un nom d'hôte existe, mais le nom d'hôte ne correspond pas au nom d'hôte de certificat.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
