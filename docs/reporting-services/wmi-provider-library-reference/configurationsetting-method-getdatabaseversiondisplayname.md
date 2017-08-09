---
title: "Méthode GetDatabaseVersionDisplayName (WMI) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetDatabaseVersionDisplayName method
ms.assetid: e1286424-7043-4f12-a7ad-1cf69e81baa4
caps.latest.revision: 15
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: b4743439f2edf3f3cfb253aa981af83350f5aff7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---getdatabaseversiondisplayname"></a>Méthode ConfigurationSetting - GetDatabaseVersionDisplayName
  Obtient le nom complet de la chaîne de version d'une base de données de serveur de rapports spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub GetDatabaseVersionDisplayName(Version As String, DisplayName As String, ByRef HRESULT As Int32)  
```  
  
```csharp  
public void GetDatabaseVersionDisplayName(string Version, string DisplayName, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Version*  
 Chaîne qui contient la chaîne de version d'une base de données de serveur de rapports.  
  
 *DisplayName*  
 [out] Chaîne qui contient le nom complet correspondant à la version fournie.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant indique la correspondance entre la version de la base de données et la chaîne d'affichage.  
  
|**Release**|**Version**|**Nom complet**|  
|-----------------|-----------------|----------------------|  
|RS 2005 SP2|@DBVersion= 'C.0.8.54'|SQL Server 2005 SP2|  
|RS 2005 SP1|@DBVersion= 'C.0.8.43'|SQL Server 2005 SP1|  
|RS 2005 RTM|@DBVersion= 'C.0.8.40'|SQL Server 2005|  
|RS 2000 SP2|@DBVersion= « C.0.6.54 »|SQL Server 2000 SP2|  
|RS 2000 SP1|@DBVersion= 'C.0.6.51'|SQL Server 2000 SP1|  
|RS 2000 RTM|@DBVersion= 'C.0.6.43'|SQL Server 2000|  
|Correctif logiciel||Version applicable la plus proche|  
  
 Pour une *Version* antérieure à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000, le paramètre HRESULT ACT_E_BAD_VERSION est retourné.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
