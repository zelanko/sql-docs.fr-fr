---
title: "GetAdminSiteUrl, méthode (WMI) | Microsoft Docs"
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
helpviewer_keywords: GetAdminSiteUrl method
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
caps.latest.revision: "14"
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 934332c5316c67cca9b84a6a8643012269833c49
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="configurationsetting-method---getadminsiteurl"></a>Méthode ConfigurationSetting - GetAdminSiteUrl
  Obtient l'URL absolue du site Web Administration centrale pour la batterie de serveurs Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]ou [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] à laquelle le serveur de rapports est intégré.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub GetAdminSiteUrl(ByRef AdminSiteUrl as String, _  
ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GetAdminSiteUrl(out string AdminSiteUrl, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *AdminSiteUrl*  
 [out] Chaîne qui contient l'URL absolue du site Web Administration centrale pour la batterie de serveurs SharePoint à laquelle le serveur de rapports est intégré.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-methods.md)  
  
  
