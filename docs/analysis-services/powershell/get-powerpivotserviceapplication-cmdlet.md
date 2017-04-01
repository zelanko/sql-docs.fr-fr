---
title: "Applet de commande Get-PowerPivotServiceApplication | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 99e4faa1-2f87-43c6-b7ec-a97d4112c5ac
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Applet de commande Get-PowerPivotServiceApplication
  Retourne une ou plusieurs applications de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
 **S'applique à :** SharePoint 2010 et SharePoint 2013.  
  
## Syntaxe  
  
```  
Get-PowerPivotServiceApplication [[-Identity] <SPGeminiServiceApplicationPipeBind>] [<CommonParameters>]  
```  
  
## Description  
 L'applet de commande Get-PowerPivotServiceApplication retourne l'application de service spécifiée par le paramètre Identity. Si aucun paramètre n’est spécifié, l’applet de commande retourne toutes les applications de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] de la batterie. Chaque application est identifiée par son nom complet, son type d'application et son GUID. Pour afficher les autres propriétés d’une application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], ajoutez l’option format-list à l’applet de commande.  
  
## Paramètres  
  
### -Identity \<SPGeminiServiceApplicationPipeBind>  
 Spécifie l'application de service à obtenir. La valeur doit être un GUID valide qui identifie l'objet de manière unique dans la batterie.  
  
|||  
|-|-|  
|Requis ?|false|  
|Position ?|0|  
|Valeur par défaut||  
|Accepter l'entrée de pipeline ?|true|  
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
C:\PS>Get-PowerPivotServiceApplication  
```  
  
 Cet exemple retourne une ou plusieurs applications de service de la batterie.  
  
## Exemple 2  
  
```  
C:\PS>Get-PowerPivotServiceApplication | format-list  
```  
  
 Cet exemple retourne toutes les propriétés d’une application de service [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## Exemple 3  
  
```  
C:\PS>get-PowerPivotServiceApplication -Identity 1234567-890a-bcde-fghijklm  
```  
  
 Cet exemple retourne une seule application de service, en indiquant son nom complet, son type d'application et son GUID. Si le nom complet est long, il sera tronqué. Utilisez l'option format-list pour afficher le nom entier.  
  
  