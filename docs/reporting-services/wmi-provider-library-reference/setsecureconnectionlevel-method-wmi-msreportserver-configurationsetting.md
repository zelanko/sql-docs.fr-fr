---
title: "M&#233;thode SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "méthode SetSecureConnectionLevel"
ms.assetid: 0fac7d5e-2670-4657-9439-331e7d93babb
caps.latest.revision: 21
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# M&#233;thode SetSecureConnectionLevel (WMI MSReportServer_ConfigurationSetting)
  Définit le niveau de connexion sécurisée du serveur de rapports.  
  
## Syntaxe  
  
```vb  
Public Sub SetSecureConnectionLevel(Level as Integer, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void SetSecureConnectionLevel(Int32 Level,   
    out Int32 HRESULT);  
```  
  
## Paramètres  
 *Level*  
 Valeur entière représentant un niveau de connexion sécurisée.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
## Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## Notes  
 Quand cette méthode est appelée, la propriété de serveur de rapports SecureConnectionLevel prend la valeur spécifiée. La valeur 0 indique que le protocole SSL est désactivé. Une valeur supérieure ou égale à 1 indique que le protocole SSL est activé.  
  
-   Quand la valeur est définie, l’élément SecureConnectionLevel dans le fichier de configuration du serveur de rapports est modifié et l’élément **URLRoot** dans le fichier de configuration est configuré de façon à utiliser « https:// » si la valeur *Level* spécifiée est supérieure ou égale à 1, ou « http:// » si la valeur *Level* spécifiée est 0.  
  
 Dans [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], SecureConnectionLevel est un commutateur d’activation ou de désactivation. La valeur par défaut est 0. Pour toute valeur supérieure ou égale à 1 passée par le biais de l’API de la méthode SetSecureConnectionLevel, le protocole SSL est considéré comme activé et la propriété de configuration SecureConnectionLevel est définie en conséquence dans le fichier rsreportserver.config. Les valeurs 2 et 3 sont toujours autorisées pour des raisons de compatibilité descendante.  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  