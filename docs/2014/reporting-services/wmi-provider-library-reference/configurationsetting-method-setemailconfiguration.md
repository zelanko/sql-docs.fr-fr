---
title: SetEmailConfiguration, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- SetEmailConfiguration method
ms.assetid: b40a2224-2c90-4d32-892f-1fe73a0591ca
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 142fd8bf2116d4cc672aeb607938ea8c1c73bf8a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66097986"
---
# <a name="setemailconfiguration-method-wmi-msreportserver_configurationsetting"></a>Méthode SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting)
  Configure l'extension de remise par messagerie utilisée par le serveur de rapports pour envoyer des messages électroniques.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub SetEmailConfiguration(ByVal SendUsingSMTPServer As Boolean, _  
    ByVal SMTPServer As String, ByVal SenderEmailAddress As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetEmailConfiguration (Boolean SendUsingSMTPServer,   
   string SMTPServer, string SenderEmailAddress,   
   out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *SendUsingSMTPServer*  
 Valeur booléenne indiquant si le serveur doit utiliser le serveur SMTP pour envoyer le courrier électronique. Cette valeur peut uniquement être True. La valeur par défaut est false.  
  
 *SMTPServer*  
 Chaîne contenant le nom ou l'adresse IP d'un serveur SMTP.  
  
 *SenderEmailAddress*  
 Adresse de messagerie utilisée dans le champ 'De :' pour les messages électroniques envoyés depuis le serveur de rapports.  
  
 *SIGNÉ*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Lorsque le paramètre *SendUsingSMTPServer* a la valeur `true`, l’entrée **SendUsing** dans le fichier de configuration du serveur de rapports a la valeur 1. Lorsque *SendUsingSMTPServer* a la valeur `false`, l’entrée **SendUsing** n’est pas configurée.  
  
 Avec cette méthode, les utilisateurs ne peuvent pas configurer l’entrée **SendUsing** dans le fichier de configuration du serveur de rapports à une autre valeur que 1. Pour configurer le serveur de rapports pour une fonctionnalité autre que le courrier SMTP, vous devez modifier le fichier de configuration manuellement.  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :**[!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
