---
title: "Applet de commande Set-PowerPivotSystemService | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: f6ef197b-3d74-4339-ae73-8a7c1eaf0e91
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 11
---
# Applet de commande Set-PowerPivotSystemService
  Définit les propriétés globales de l'objet PowerPivotSystemService au niveau de la batterie.  
  
 **S'applique à :** SharePoint 2010 et SharePoint 2013.  
  
## Syntaxe  
  
```  
Set-PowerPivotSystemService [-Identity <PowerPivotMidTierServicePipeBind>] [-UpdateAssemblyInformation <switch>] [-WorkbookUpgradeOnDataRefresh <boolean>] [-DirectTCPConnections <boolean>] [-Confirm <switch>] [<CommonParameters>]  
```  
  
## Description  
 L’applet de commande Set-PowerPivotSystemService met à jour les propriétés de l’objet parent de service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans la batterie.  
  
## Paramètres  
  
### -Identity \<PowerPivotMidTierServicePipeBind>  
 Spécifie l'objet parent dont vous mettez à jour les propriétés. La valeur doit être un GUID valide qui identifie l'objet de manière unique dans la batterie.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
|Accepter les caractères génériques ?|false|  
  
### -UpdateAssemblyInformation \<switch>  
 Utilisé uniquement pour la mise à niveau. Si la version d'assembly déployée dans la batterie de serveurs est différente de la version stockée dans la base de données de configuration SharePoint, vous pouvez exécuter cette applet de commande pour mettre à jour les informations de l'assembly dans la base de données de configuration. Les informations de version de l'assembly sont disponibles dans les propriétés de fichier du fichier Microsoft.AnalysisServices.SharePoint.Integration.dll stocké dans l'assembly global.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -WorkbookUpgradeOnDataRefresh \<boolean>  
 Utilisé pour mettre à niveau de manière automatique un classeur [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] au début d'une actualisation des données planifiée sur le serveur. L'actualisation des données est prise en charge uniquement pour les classeurs qui correspondent à la version actuelle du serveur. Si vous activez cette propriété, un classeur est automatiquement mis à niveau afin que l'actualisation des données puisse continuer. Cette propriété est définie au niveau de l'instance de serveur. Vous ne pouvez pas la modifier pour des classeurs, des bibliothèques, des sites ou des utilisateurs spécifiques.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|2|  
|Valeur par défaut|false|  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -DirectTCPConnections \<boolean>  
 Spécifie qu’Excel Services envoie directement toutes les requêtes à l’instance de SQL Server Analysis Services (POWERPIVOT) qui a chargé une base de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], en ignorant le fournisseur de données MSOLAP et le transport de canal qui sont habituellement utilisés pour chaque demande de requête envoyée à une base de données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 La définition de ce paramètre optimise les performances et l’évolutivité des requêtes [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en améliorant l’efficacité des connexions aux bases de données chargées. Notez que ce paramètre ne modifie pas le comportement de l'allocation de la demande de chargement initiale. Les autres paramètres, tels que –RoundRobinAllocation et –HealthBasedAllocation, qui sont utilisés pour allouer les requêtes de chargement de base de données entre plusieurs instances de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint dans la batterie ne sont pas affectés, car –DirectTCPConnections s’applique uniquement aux requêtes générées après le chargement de la base de données.  
  
 Pour les topologies de batteries de serveurs incluant des installations d’Excel Services et de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint qui s’exécutent sur des serveurs d’applications distincts, vous devez ouvrir un port dans le pare-feu afin de vous assurer que les requêtes parviennent à l’instance de SQL Server Analysis Services (POWERPIVOT). Pour savoir comment activer les connexions entrantes pour une instance nommée d’Analysis Services, consultez [Configurer le pare-feu Windows pour autoriser l’accès à Analysis Services](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|3|  
|Valeur par défaut|false|  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### -Confirm \<switch>  
 Demande une confirmation avant d'exécuter la commande. Cette valeur est activée par défaut. Pour contourner la réponse de confirmation dans une commande, spécifiez Confirm:$false sur la commande.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### \<CommonParameters>  
 Cette applet de commande prend en charge les paramètres communs : Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer et OutVariable. Pour plus d’informations, consultez [About_Commonparameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun.|  
|Sorties|Aucun.|  
  
## Exemple 1  
  
```  
C:\PS>Set-PowerPivotSystemService -WorkbookUpgradeOnDataRefresh:$true  
```  
  
 Active la mise à niveau automatique des classeurs de version précédente afin que l'actualisation des données planifiée puisse continuer.  
  
  