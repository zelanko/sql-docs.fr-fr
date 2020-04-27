---
title: GenerateDatabaseUpgradeScript, méthode (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseUpgradeScript method
ms.assetid: 88534e8e-2877-41cd-b5c2-b1d33a0fd203
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a095b63f8c42709700f6f338edc409f801f8be3c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66098459"
---
# <a name="generatedatabaseupgradescript-method-wmi-msreportserver_configurationsetting"></a>Méthode GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting)
  Génère un script pouvant être utilisé pour mettre à niveau la base de données de serveur de rapports vers le schéma [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] .  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Public Sub GenerateDatabaseUpgradeScript(DatabaseName as String, _  
    ServerVersion as String, ByRef Script as String, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GenerateDatabaseUpgradeScript (string DatabaseName,   
    string ServerVersion, out string Script,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>Paramètres  
 *Databasename*  
 Chaîne contenant le nom de la base de données du serveur de rapports à mettre à niveau.  
  
 *ServerVersion*  
 Chaîne contenant la version du serveur de rapports.  
  
 *Script*  
 [out] Chaîne contenant le script SQL généré.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## <a name="remarks"></a>Notes  
 Le script généré prend en charge [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-members.md)  
  
  
