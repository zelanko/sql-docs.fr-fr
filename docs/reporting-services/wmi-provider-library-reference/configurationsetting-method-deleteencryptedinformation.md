---
title: "Méthode de DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting) | Documents Microsoft"
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
apiname:
- DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DeleteEncryptedInformation method
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
caps.latest.revision: 19
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 88991ec2c7787264253df79626b7df1f9edece45
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---
# <a name="configurationsetting-method---deleteencryptedinformation"></a>Méthode ConfigurationSetting - DeleteEncryptedInformation
  Supprime les informations chiffrées de la base de données du serveur de rapports.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>Paramètres  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
 *ExtendedErrors[]*  
 [out] Tableau de chaînes contenant les erreurs supplémentaires retournées par l'appel.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Lorsque cette méthode est appelée, les données suivantes sont supprimées :  
  
-   Informations de source de données chiffrées, y compris le nom d'utilisateur et le mot de passe.  
  
-   Données d'abonnement chiffrées à l'aide des interfaces d'extension de remise.  
  
-   Toutes les informations de la table de clés de la base de données du serveur de rapports.  
  
 Suite à l'appel de cette méthode, l'utilisateur doit initialiser chaque ordinateur qui utilise la base de données du serveur de rapports.  
  
 L’appel de la méthode DeleteEncryptedInformation n’affecte pas le fichier de configuration du serveur de rapports.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
