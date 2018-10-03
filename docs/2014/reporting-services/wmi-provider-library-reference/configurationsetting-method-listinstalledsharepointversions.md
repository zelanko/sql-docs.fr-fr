---
title: ListInstalledSharePointVersions, méthode (WMI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- ListInstalledSharePointVersions method
ms.assetid: 8f0a5e9f-23f1-41e5-9a90-dfec19ef1df7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: df7a2d38bf0c08349b570c0303c1f9951ebccce0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122359"
---
# <a name="listinstalledsharepointversions-method-wmi"></a>Méthode ListInstalledSharePointVersions (WMI)
  Retourne un ensemble de jetons qui représentent les versions de Microsoft [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] ou [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installées sur le même ordinateur que le serveur de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub ListInstalledSharePointVersions(ByRef VersionTokens() _  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] VersionTokens,   
    out Int32 Length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *VersionTokens[]*  
 [out] Tableau qui contient les jetons qui représentent la version d'un produit ou d'une technologie SharePoint compatible avec le serveur de rapports installé.  
  
 *Longueur*  
 [out] Longueur du tableau de jetons de la version.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Chaque jeton retourné représente une version de [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] ou [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] compatible avec le serveur de rapports actuellement installé. Si une version particulière de SharePoint est compatible avec les versions SharePoint précédentes, les jetons pour chaque version SharePoint compatible sont retournés.  
  
 Voici un tableau des jetons SharePoint retournés.  
  
|**Jetons de version**|**Description**|  
|------------------------|---------------------|  
|WSS_V2_Compatible|Une installation de [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]ou [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] compatible avec [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 2.0 est installée.|  
|WSS_V3_Compatible|Une installation [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], [!INCLUDE[offSPServ](../../includes/offspserv-md.md)], [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]ou [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] compatible avec [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0 est installée.|  
|WSS_V4_Compatible|Une installation [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] ou [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] compatible avec Office 14 est installée.|  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
