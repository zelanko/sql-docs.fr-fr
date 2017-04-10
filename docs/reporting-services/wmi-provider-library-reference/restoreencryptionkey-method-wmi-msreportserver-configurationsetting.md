---
title: "M&#233;thode RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "méthode RestoreEncryptionKey"
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# M&#233;thode RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting)
  Réapplique la clé de chiffrement spécifiée à la base de données du serveur de rapports.  
  
## Syntaxe  
  
```vb  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## Paramètres  
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
  
## Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## Notes  
 S'il existe déjà une entrée pour le serveur de rapports dans la base de données du serveur de rapports, elle est supprimée. La nouvelle entrée est ensuite créée à l'aide de la clé de chiffrement spécifiée et de la clé publique du serveur de rapports.  
  
 Cette méthode est très efficace quand elle est appelée après la méthode [DeleteEncryptionKey](../../reporting-services/wmi-provider-library-reference/deleteencryptionkey-method-wmi-msreportserver-configurationsetting.md), qui efface la liste de clés de chiffrement.  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  