---
title: "M&#233;thode DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "méthode DeleteEncryptedInformation"
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# M&#233;thode DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting)
  Supprime les informations chiffrées de la base de données du serveur de rapports.  
  
## Syntaxe  
  
```vb  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## Paramètres  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
 *ExtendedErrors[]*  
 [out] Tableau de chaînes contenant les erreurs supplémentaires retournées par l'appel.  
  
## Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## Notes  
 Lorsque cette méthode est appelée, les données suivantes sont supprimées :  
  
-   Informations de source de données chiffrées, y compris le nom d'utilisateur et le mot de passe.  
  
-   Données d'abonnement chiffrées à l'aide des interfaces d'extension de remise.  
  
-   Toutes les informations de la table de clés de la base de données du serveur de rapports.  
  
 Suite à l'appel de cette méthode, l'utilisateur doit initialiser chaque ordinateur qui utilise la base de données du serveur de rapports.  
  
 L’appel de la méthode DeleteEncryptedInformation n’affecte pas le fichier de configuration du serveur de rapports.  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  