---
description: Méthode ListReservedURLs (WMI MSReportServer_ConfigurationSetting)
title: ListReservedURLs, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
helpviewer_keywords:
- ListReservedURLs method
ms.assetid: 32335af1-5eae-4420-a0ef-b1e8a3267166
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e19d6bf8c8f437f032edd9ad7a26b94f93a7ea7f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454481"
---
# <a name="configurationsetting-method---listreservedurls"></a>Méthode ConfigurationSetting - ListReservedURLs
  Répertorie les URL réservées pour toutes les applications sur le serveur de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub ListReservedUrls(ByRef Application() as String, ByRef UrlString() as String, _  
    ByRef Account() as String, ByRef AccountSID() as String, _  
    ByRef length() as Int32, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ListReservedUrls(out string[] Application, out string[] UrlString,  
        out string[] Account, out string[] AccountSID,  
        out int[] Length, out int[] HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Application[]*  
 [out] Applications qui ont des réservations d'URL.  
  
 *UrlString[]*  
 [out] URL réservées.  
  
 *Account[]*  
 [out] Noms de comptes associés au compte pour les réservations d'URL.  
  
 *AccountSID[]*  
 [out] SID de comptes associés au compte pour les réservations d'URL.  
  
 *Longueur*  
 [out] Longueur des tableaux retournés par la méthode.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. La valeur 0 indique que l'appel de la méthode a abouti ; un code d'erreur indique que l'appel n'a pas abouti.  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
