---
title: ReserveURL, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ReservedURL method
ms.assetid: b9008a62-3edd-4f8a-99f2-7598c2133899
caps.latest.revision: 14
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 1cd5ef5a1e4a29b70d742e858a30ab9912cce6bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153178"
---
# <a name="reserveurl-method-wmi-msreportserverconfigurationsetting"></a>Méthode ReserveURL (WMI MSReportServer_ConfigurationSetting)
  Ajoute une réservation d'URL pour une application donnée.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub ReserveURL(Application as String, _  
    UrlString as String, Lcid as Int32, _   
    ByRef [Error] as String, ByRef HRESULT as Int32)  
```  
  
```csharp  
public void ReserveURL(string Application, string UrlString, int Lcid,   
    out string error, out int HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Application*  
 Nom de l'application pour laquelle l'URL doit être réservée.  
  
 *URLString*  
 URL pour la réservation.  
  
 *lcid*  
 Paramètres régionaux à utiliser pour les messages d'erreur retournés.  
  
 *Erreur*  
 [out] Description de l'erreur qui s'est produite.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. La valeur 0 indique que l'appel de la méthode a abouti ; un code d'erreur indique que l'appel n'a pas abouti.  
  
## <a name="remarks"></a>Notes  
 La propriété*UrlString* n'inclut pas le nom de répertoire virtuel. Le [SetVirtualDirectory](configurationsetting-method-setvirtualdirectory.md) méthode est fournie à cet effet.  
  
 Des réservations d'URL sont créées pour le compte de service Windows actuel. La modification du compte de service Windows nécessite la mise à jour manuelle de toutes les réservations d'URL.  
  
 Cette méthode entraîne un recyclage forcé de tous les domaines d'application. Les domaines d'application sont redémarrés une fois cette opération terminée.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  