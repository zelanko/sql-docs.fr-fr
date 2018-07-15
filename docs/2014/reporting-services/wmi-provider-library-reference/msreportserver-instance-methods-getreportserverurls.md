---
title: GetReportServerUrls, méthode (WMI MSReportServer_Instance) | Microsoft Docs
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
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 9b2963bad73fce65f252ad44ed857f6006978c2f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37313195"
---
# <a name="getreportserverurls-method-wmi-msreportserverinstance"></a>Méthode GetReportServerUrls (WMI MSReportServer_Instance)
  Retourne la liste des URL que les utilisateurs peuvent employer pour accéder au serveur de rapports et au Gestionnaire de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub GetReportServerUrls (ByRef ApplicationName() As String, ByRef URLs()_  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetReportServerUrls(out string[] applicationName,   
    out string[] URLs, out int length, out int HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *ApplicationName[]*  
 Tableau qui contient les applications installées. Valeurs possibles sont `ReportServerWebService` ou `ReportManager`.  
  
 *URLs[]*  
 Tableau qui contient les URL inscrites avec succès.  
  
 *Longueur*  
 Valeur entière qui contient la longueur des tableaux retournés.  
  
 *HRESULT*  
 Valeur qui indique le succès ou un code d'erreur.  
  
## <a name="return-values"></a>Valeurs de retour  
  
## <a name="remarks"></a>Notes  
 Les méthodes exposées par les objets de gestion WMI sont appelées par le biais de la fonction InvokeMethod. Pour plus d’informations, consultez la section relative à l’exécution des méthodes sur des objets de gestion dans la documentation WMI du [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
