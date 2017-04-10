---
title: "Applet de commande New-PowerPivotSystemServiceInstance | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 7ea94113-c0f1-4cca-9228-f1a034fba5db
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Applet de commande New-PowerPivotSystemServiceInstance
  Ajoute une nouvelle instance de service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] à un serveur d’applications.  
  
 **S'applique à :** SharePoint 2010 et SharePoint 2013.  
  
## Syntaxe  
  
```  
New-PowerPivotSystemServiceInstance [[-ParentService] <PowerPivotMidTierServicePipeBind>] [-SystemServiceInstanceName <string>] [-Provision] [<CommonParameters>]  
```  
  
## Description  
 L’applet de commande New-PowerPivotSystemServiceInstance configure un nouvel objet PowerPivotSystemService au niveau de la batterie une fois que vous avez utilisé le programme d’installation de SQL Server pour installer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint sur le serveur d’applications local. Vous ne pouvez configurer qu'une seule instance du service sur chaque serveur d'applications.  Si le service est déjà configuré, vous ne pouvez pas exécuter cette applet de commande.  
  
## Paramètres  
  
### -ParentService \<PowerPivotMidTierServicePipeBind>  
 Spécifie le GUID de l’objet parent du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] dans la batterie. Dans cette version, un seul objet parent est autorisé. Vous pouvez utiliser l'applet de commande Get-PowerPivotSystemService pour retourner l'objet de service ou son GUID.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
|Accepter les caractères génériques ?|false|  
  
### -SystemServiceInstanceName \<string>  
 Spécifie un nom qui identifie cet objet.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|1|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### Provision [\<SwitchParameter>]  
 Rend le service accessible sur SharePoint. Les valeurs valides sont $true ou $false.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|false|  
|Accepter les caractères génériques ?|false|  
  
### \<CommonParameters>  
 Cette applet de commande prend en charge les paramètres communs : Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer et OutVariable. Pour plus d’informations, consultez [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun.|  
|Sorties|Aucun.|  
  
## Exemple 1  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -Provision:$true  
```  
  
 Cet exemple montre la forme la plus commune de l'applet de commande. Il inscrit le service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] sur le serveur d’applications local avec la batterie.  
  
## Exemple 2  
  
```  
C:\PS>New-PowerPivotSystemServiceInstance -SystemServiceInstanceName "MyPSSInstance" -provision:$false  
```  
  
 Cet exemple nomme l’instance du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , mais sans la configurer. Si vous ne fournissez pas de nom, le nom par défaut, instance de service système SQL Server Analysis Services, est utilisé à la place. La création d'un nom personnalisé pour le service est facultative. Vous pouvez nommer le service pour prendre en charge les scénarios de test, ou si vous disposez d'un outil ou d'un script personnalisé qui configure l'instance à une étape ultérieure.  
  
  