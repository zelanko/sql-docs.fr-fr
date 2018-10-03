---
title: ReencryptSecureInformation, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- ReencryptSecureInformation method
ms.assetid: 8a487497-c207-45b2-8c92-87c58cc68716
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4cf5c75a959c0794fea1d66b137c2370dfb3d6b6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217799"
---
# <a name="reencryptsecureinformation-method-wmi-msreportserverconfigurationsetting"></a>Méthode ReencryptSecureInformation (WMI MSReportServer_ConfigurationSetting)
  Génère une nouvelle clé de chiffrement et rechiffre toutes les informations sécurisées dans le catalogue à l'aide de cette nouvelle clé.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub ReencryptSecureInformation(ByRef HRESULT as Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ReencryptSecureInformation (out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Paramètres  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
 *ExtendedErrors[]*  
 [out] Tableau de chaînes contenant les erreurs supplémentaires retournées par l'appel.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 La méthode ReencryptSecureInformation permet à l’administrateur de remplacer la clé de chiffrement existante par une nouvelle clé.  
  
 Lorsque cette méthode est appelée, le serveur de rapports génère une nouvelle clé de chiffrement et parcourt tout le contenu chiffré afin de le rechiffrer avec la nouvelle clé de chiffrement.  
  
 Les extensions de remise peuvent stocker des informations sécurisées dans leurs structures de paramètres de remise. Quand ReencryptSecureInformation est appelée, le serveur de rapports charge chaque abonnement et l’extension de remise correspondante pour rechiffrer les informations stockées dans les paramètres associés.  
  
 Si cette méthode est exécutée sur un ordinateur dans un déploiement avec montée en puissance parallèle, chaque ordinateur dans le déploiement avec montée en puissance parallèle doit être réinitialisé.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
