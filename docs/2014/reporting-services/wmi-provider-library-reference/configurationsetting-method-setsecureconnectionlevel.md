---
title: SetSecureConnectionLevel, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetSecureConnectionLevel method
ms.assetid: 0fac7d5e-2670-4657-9439-331e7d93babb
caps.latest.revision: 21
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: f761337d48cc168ee87a0557201b5827a80afd21
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043525"
---
# <a name="setsecureconnectionlevel-method-wmi-msreportserverconfigurationsetting"></a>Méthode SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting)
  Définit le niveau de connexion sécurisée du serveur de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetSecureConnectionLevel(Level as Integer, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Int32 Level,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Level*  
 Valeur entière représentant un niveau de connexion sécurisée.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Quand cette méthode est appelée, la propriété de serveur de rapports SecureConnectionLevel prend la valeur spécifiée. La valeur 0 indique que le protocole SSL est désactivé. Une valeur supérieure ou égale à 1 indique que le protocole SSL est activé.  
  
-   Lorsque la valeur est définie, l’élément SecureConnectionLevel dans le fichier de configuration de serveur de rapports est modifié et la `URLRoot` élément dans le fichier de configuration est configuré pour utiliser « https:// » si spécifié *niveau* est supérieur à ou égal à 1, ou « http:// » si le texte spécifié *niveau* est 0.  
  
 Dans [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], SecureConnectionLevel est un commutateur d’activation ou de désactivation. La valeur par défaut est 0. Pour toute valeur supérieure ou égale à 1 passée par le biais de l’API de la méthode SetSecureConnectionLevel, le protocole SSL est considéré comme activé et la propriété de configuration SecureConnectionLevel est définie en conséquence dans le fichier rsreportserver.config. Les valeurs 2 et 3 sont toujours autorisées pour des raisons de compatibilité descendante.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  