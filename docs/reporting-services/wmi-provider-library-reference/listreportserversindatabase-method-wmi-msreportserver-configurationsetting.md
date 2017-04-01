---
title: "M&#233;thode ListReportServersInDatabase (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
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
  - "ListReportServersInDatabase (WMI MSReportServer_ConfigurationSetting Class)"
apilocation: 
  - "reportingservices.mof"
apitype: "MOFDef"
helpviewer_keywords: 
  - "ListReportServersInDatabase, méthode"
ms.assetid: a4bf5968-c46f-484f-a510-65e2dde65a0d
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
---
# M&#233;thode ListReportServersInDatabase (WMI MSReportServer_ConfigurationSetting)
  Retourne la liste des installations du serveur de rapports qui sont présentes dans la base de données du serveur de rapports, même si elles n'ont pas accès aux informations sécurisées.  
  
## Syntaxe  
  
```vb  
Public Sub ListReportServersInDatabase(ByRef MachineNames() As String, _  
    ByRef InstanceNames() As String, ByRef InstallationIDs() As String, _  
    ByRef IsInitialized() As Boolean, ByRef Length As Int32, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] MachineNames,   
    out string[] InstanceNames, out string[] InstallationIDs,   
    out Boolean[] IsInitialized,out Int32 Length, out Int32 HRESULT,    
    out string[] ExtendedErrors);  
```  
  
## Paramètres  
 *MachineNames[]*  
 [out] Tableau contenant les noms de machines des installations du serveur de rapports dans la base de données.  
  
 *InstanceNames[]*  
 [out] Tableau contenant les noms d'instances de chacune des installations du serveur de rapports dans la base de données.  
  
 *InstallationIDs[]*  
 [out] Tableau contenant l'ID d'installation de chaque installation du serveur de rapports dans la base de données.  
  
 *IsInitialized[]*  
 [out] Tableau contenant l'état d'initialisation de chaque installation du serveur de rapports dans la base de données.  
  
 *Longueur*  
 [out] Longueur des tableaux retournés par la méthode. Tous les tableaux retournés ont la même longueur.  
  
 *HRESULT*  
 [out] Valeur indiquant si l'appel a réussi ou échoué.  
  
 *ExtendedErrors[]*  
 [out] Tableau de chaînes contenant les erreurs supplémentaires retournées par l'appel.  
  
## Valeur retournée  
 Retourne un paramètre *HRESULT* qui indique si l'appel de la méthode a réussi ou a échoué. Une valeur 0 indique que l'appel de méthode a réussi. Une valeur différente de zéro indique qu'une erreur s'est produite.  
  
## Notes  
 ListReportServersInDatabase répertorie les installations du serveur de rapports qui sont présentes dans la base de données du serveur de rapports, qu’elles aient accès ou non aux informations sécurisées, et retourne un ensemble de tableaux correspondants qui contiennent des informations à propos de chaque installation.  
  
## Spécifications  
 **Espace de noms :** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## Voir aussi  
 [Membres MSReportServer_ConfigurationSetting](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  