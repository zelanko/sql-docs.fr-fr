---
title: "Applet de commande Remove-PowerPivotSystemServiceInstance | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: bc46094a-5584-47ba-8883-77dc79373a5d
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Applet de commande Remove-PowerPivotSystemServiceInstance
  Supprime une instance du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de la batterie de serveurs.  
  
 **S'applique à :** SharePoint 2010 et SharePoint 2013.  
  
## Syntaxe  
  
```  
Remove-PowerPivotSystemServiceInstance [-Confirm <switch>] [-DeleteLocal <switch>] [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## Description  
 L’applet de commande Remove-PowerPivotSystemServiceInstance supprime les informations d’instance relatives au service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de la batterie de serveurs. Elle ne supprime pas les fichiers programme. Pour supprimer définitivement les fichiers programme, vous devez les désinstaller.  
  
 Si vous supprimez le service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], veillez à exécuter également Remove-PowerPivotEngineServiceInstance pour supprimer l’instance Analysis Services associée, puis Remove-PowerPivotServiceApplication pour supprimer toutes les applications de service PowerPivot. Les applications de service ne s'exécuteront plus une fois les services supprimés.  
  
 Pour annuler cette modification, vous pouvez exécuter New-PowerPivotSystemServiceInstance pour réactiver les informations d'instance.  
  
## Paramètres  
  
### -Identity \<PowerPivotMidTierServiceInstancePipeBind>  
 Spécifie le GUID de l’instance du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] que vous souhaitez supprimer. Il existe une instance de service sur chaque serveur d’applications comportant une installation de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
|Accepter les caractères génériques ?|false|  
  
### -DeleteLocal \<switch>  
 Supprime l’instance du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] installée sur l’ordinateur local, ce qui vous permet de supprimer l’instance sans avoir à spécifier d’identité d’objet.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|nommée|  
|Valeur par défaut||  
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
 Cette applet de commande prend en charge les paramètres communs : Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer et OutVariable. Pour plus d’informations, consultez [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825).  
  
## Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun.|  
|Sorties|Aucun.|  
  
## Exemple 1  
  
```  
C:\PS>Remove-PowerPivotSystemServiceInstance -deletelocal  
```  
  
 Cet exemple indique comment supprimer l’instance du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] qui s’exécute sur le serveur d’applications local.  
  
## Exemple 2  
  
```  
C:\PS>Remove-PowerPivotSystemServiceInstance -identity 1234567-890a-bcde-fghijklmn  
```  
  
 Cet exemple indique comment supprimer un service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] spécifique en fonction de son identité.  
  
  