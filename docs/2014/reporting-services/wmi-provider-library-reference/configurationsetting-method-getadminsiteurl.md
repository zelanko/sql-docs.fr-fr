---
title: GetAdminSiteUrl, méthode (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetAdminSiteUrl method
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9012a5cbc130ac79963e033c8c3d93807d946445
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66098434"
---
# <a name="getadminsiteurl-method-wmi"></a>Méthode GetAdminSiteUrl (WMI)
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
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="requirements"></a>Configuration requise  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-methods.md)  
  
  
