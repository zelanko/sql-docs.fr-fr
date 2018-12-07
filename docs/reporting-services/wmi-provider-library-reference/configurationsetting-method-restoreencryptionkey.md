---
title: RestoreEncryptionKey, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- RestoreEncryptionKey method
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6d19ecb9c4f14c0f9750a7344a6c2c442785cbb0
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52416136"
---
# <a name="configurationsetting-method---restoreencryptionkey"></a>Méthode ConfigurationSetting - RestoreEncryptionKey
  Réapplique la clé de chiffrement spécifiée à la base de données du serveur de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Paramètres  
 *KeyFile[]*  
 [out] Tableau contenant la clé de chiffrement chiffrée.  
  
 *Longueur*  
 [out] Longueur du tableau retourné par la méthode.  
  
 *Mot de passe*  
 Chaîne utilisée pour chiffrer la clé de chiffrement.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
 *ExtendedErrors[]*  
 [out] Tableau de chaînes contenant les erreurs supplémentaires retournées par l'appel.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes   
 S'il existe déjà une entrée pour le serveur de rapports dans la base de données du serveur de rapports, elle est supprimée. La nouvelle entrée est ensuite créée à l’aide de la clé de chiffrement spécifiée et de la clé publique du serveur de rapports.  
  
 Cette méthode est très efficace quand elle est appelée après la méthode [DeleteEncryptionKey](../../reporting-services/wmi-provider-library-reference/configurationsetting-method-deleteencryptionkey.md) , qui efface la liste de clés de chiffrement.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a> Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
