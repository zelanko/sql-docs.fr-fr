---
title: GetReportServerUrls, méthode (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- GetReportServerUrls method
ms.assetid: 4865e32c-0114-465a-be8c-be223a7bc09e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2580538f24fe220369f0f6ea807e6caa8dd822a6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63020537"
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
 Tableau qui contient les applications installées. Les valeurs possibles sont `ReportServerWebService` et `ReportManager`.  
  
 *URLs[]*  
 Tableau qui contient les URL inscrites avec succès.  
  
 *Longueur*  
 Valeur entière qui contient la longueur des tableaux retournés.  
  
 *HRESULT*  
 Valeur qui indique le succès ou un code d'erreur.  
  
## <a name="return-values"></a>Valeurs de retour  
  
## <a name="remarks"></a>Notes  
 Les méthodes exposées par les objets de gestion WMI sont appelées par le biais de la fonction InvokeMethod. Pour plus d’informations, consultez la section relative à l’exécution des méthodes sur des objets de gestion dans la documentation WMI du [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.  
  
## <a name="requirements"></a>Configuration requise  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
