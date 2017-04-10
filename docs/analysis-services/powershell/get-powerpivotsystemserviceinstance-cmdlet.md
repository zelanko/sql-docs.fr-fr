---
title: "Applet de commande Get-PowerPivotSystemServiceInstance | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 56027a8e-1949-4349-b616-68c8b1d2963c
caps.latest.revision: 9
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 9
---
# Applet de commande Get-PowerPivotSystemServiceInstance
  Retourne une ou plusieurs instances du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] s’exécutant sur des serveurs d’applications de la batterie.  
  
 **S'applique à :** SharePoint 2010 et SharePoint 2013.  
  
## Syntaxe  
  
```  
Get-PowerPivotSystemServiceInstance [-Identity <PowerPivotMidTierServiceInstancePipeBind>] [<CommonParameters>]  
```  
  
## Description  
 L’applet de commande Get-PowerPivotSystemServiceInstance retourne les propriétés d’une ou plusieurs instances du service système [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] s’exécutant dans la batterie. L'applet de commande indique le type de l'application, son état (en ligne ou hors connexion), et son identité. Pour afficher les propriétés supplémentaires d'une instance spécifique, ajoutez le paramètre Identity et l'option format-list à l'applet de commande.  
  
## Paramètres  
  
### -Identity \<PowerPivotMidTierServiceInstancePipeBind>  
 Spécifie l'instance de service à obtenir. La valeur doit être un GUID valide qui identifie l'objet de manière unique dans la batterie.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
|Accepter les caractères génériques ?|false|  
  
### \<CommonParameters>  
 Cette applet de commande prend en charge les paramètres communs : Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer et OutVariable. Pour plus d’informations, consultez [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)  
  
## Entrées et sorties  
 Le type d'entrée correspond au type des objets que vous pouvez canaliser vers l'applet de commande. Le type de retour correspond au type des objets retournés par l'applet de commande.  
  
|||  
|-|-|  
|Entrées|Aucun.|  
|Sorties|Aucun.|  
  
## Exemple 1  
  
```  
C:\PS>Get-PowerPivotSystemServiceInstance -Identity 1234567-890a-bcde-fghijklm | format-list| format-list  
```  
  
 Cet exemple retourne les propriétés supplémentaires de l'instance spécifiée, notamment le nom du serveur, la version et l'état de la mise à niveau.  
  
  